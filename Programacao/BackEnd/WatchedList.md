# **WatchedList (Lista Observada)**

## Conceito:

Uma _WatchedList_ é uma estrutura que permite gerenciar e monitorar alterações em listas de objetos dentro de um agregado. Ela identifica itens adicionados, removidos ou modificados, facilitando operações eficientes com o banco de dados. Isso é particularmente útil ao evitar recriações desnecessárias, melhorando a performance e garantindo a consistência dos dados.

Quando trabalhamos com relacionamentos complexos, como uma pergunta com seus anexos, a _WatchedList_ ajuda a rastrear mudanças na lista, determinando quais itens precisam ser criados, editados ou removidos. Isso é especialmente importante durante edições, quando novos itens podem ser adicionados e existentes removidos ou modificados.

## Exemplo de uso:

```typescript
// WatchedList Implementation
class WatchedList<T> {
  private current: T[] = [];
  private newItems: T[] = [];
  private removedItems: T[] = [];

  constructor(initialItems: T[]) {
    this.current = [...initialItems];
  }

  add(item: T) {
    this.newItems.push(item);
  }

  remove(item: T) {
    const index = this.current.findIndex((currentItem) => currentItem === item);
    if (index > -1) {
      this.removedItems.push(this.current[index]);
    }
  }

  getNewItems() {
    return this.newItems;
  }

  getRemovedItems() {
    return this.removedItems;
  }

  getCurrentItems() {
    return this.current;
  }
}

// Exemplo de uso: Gerenciamento de anexos em uma pergunta
class Attachment {
  constructor(public id: string, public name: string) {}
}

// Lista inicial de anexos
const attachments = new WatchedList<Attachment>([
  new Attachment("1", "file1.pdf"),
  new Attachment("2", "file2.pdf"),
]);

// Adicionar novo anexo
attachments.add(new Attachment("3", "file3.pdf"));

// Remover um anexo existente
attachments.remove(new Attachment("2", "file2.pdf"));

// Processar alterações no banco de dados
console.log("Novos anexos:", attachments.getNewItems());
console.log("Anexos removidos:", attachments.getRemovedItems());
console.log("Anexos atuais:", attachments.getCurrentItems());
```

## Quando usar:

- Ao gerenciar listas de objetos dentro de um agregado.
- Para rastrear alterações em listas, identificando itens adicionados, removidos ou modificados.
- Para otimizar operações de persistência, evitando recriações desnecessárias e garantindo a consistência dos dados.
- Em cenários onde a performance e a eficiência são críticas, especialmente em operações de edição e persistência de dados.
  []: # (end)
