# **WatchedList (Lista Observada)**

## **Conceito**

A _WatchedList_ é uma estrutura projetada para gerenciar e monitorar alterações em listas de objetos dentro de um agregado. Ela permite rastrear alterações como itens **adicionados**, **removidos** ou **modificados**, facilitando operações mais eficientes no banco de dados.

Esse pattern é especialmente útil em cenários onde há relacionamentos complexos, como, por exemplo, gerenciar anexos de uma pergunta ou tags de uma publicação. A _WatchedList_ identifica o que precisa ser criado, editado ou removido, evitando recriações desnecessárias e mantendo a consistência dos dados.

### **Por que usar?**

- **Eficiência**: Realiza apenas as operações necessárias no banco de dados, reduzindo o custo computacional.
- **Consistência**: Garante que os dados reflitam com precisão as alterações realizadas pelo usuário.
- **Simplicidade**: Fornece uma maneira clara de rastrear mudanças em listas de objetos, como itens adicionados, removidos ou mantidos.

---

## **Exemplo de Uso**

O exemplo abaixo demonstra a implementação da _WatchedList_ em TypeScript, que pode ser adaptada para gerenciar qualquer tipo de objeto.

```typescript
// WatchedList Implementation
export abstract class WatchedList<T> {
  public currentItems: T[]; // Lista atual de itens
  private initial: T[]; // Lista inicial de itens
  private new: T[]; // Itens adicionados
  private removed: T[]; // Itens removidos

  constructor(initialItems?: T[]) {
    this.currentItems = initialItems || [];
    this.initial = initialItems || [];
    this.new = [];
    this.removed = [];
  }

  abstract compareItems(a: T, b: T): boolean;

  // Métodos públicos para acessar informações da lista
  public getItems(): T[] {
    return this.currentItems;
  }

  public getNewItems(): T[] {
    return this.new;
  }

  public getRemovedItems(): T[] {
    return this.removed;
  }

  // Adiciona um item à lista observada
  public add(item: T): void {
    if (this.isRemovedItem(item)) {
      this.removeFromRemoved(item);
    }

    if (!this.isNewItem(item) && !this.wasAddedInitially(item)) {
      this.new.push(item);
    }

    if (!this.isCurrentItem(item)) {
      this.currentItems.push(item);
    }
  }

  // Remove um item da lista observada
  public remove(item: T): void {
    this.removeFromCurrent(item);

    if (this.isNewItem(item)) {
      this.removeFromNew(item);
      return;
    }

    if (!this.isRemovedItem(item)) {
      this.removed.push(item);
    }
  }

  // Atualiza a lista com uma nova coleção de itens
  public update(items: T[]): void {
    const newItems = items.filter((a) => {
      return !this.getItems().some((b) => this.compareItems(a, b));
    });

    const removedItems = this.getItems().filter((a) => {
      return !items.some((b) => this.compareItems(a, b));
    });

    this.currentItems = items;
    this.new = newItems;
    this.removed = removedItems;
  }

  // Métodos auxiliares privados
  private isCurrentItem(item: T): boolean {
    return this.currentItems.some((v) => this.compareItems(item, v));
  }

  private isNewItem(item: T): boolean {
    return this.new.some((v) => this.compareItems(item, v));
  }

  private isRemovedItem(item: T): boolean {
    return this.removed.some((v) => this.compareItems(item, v));
  }

  private removeFromNew(item: T): void {
    this.new = this.new.filter((v) => !this.compareItems(v, item));
  }

  private removeFromCurrent(item: T): void {
    this.currentItems = this.currentItems.filter(
      (v) => !this.compareItems(item, v)
    );
  }

  private removeFromRemoved(item: T): void {
    this.removed = this.removed.filter((v) => !this.compareItems(item, v));
  }

  private wasAddedInitially(item: T): boolean {
    return this.initial.some((v) => this.compareItems(item, v));
  }
}
```
