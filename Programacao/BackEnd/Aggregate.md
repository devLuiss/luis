# **Aggregates (Agregados)**

## Conceito:

Um aggregate (ou agregado) é um conjunto de entidades que são manipuladas como uma unidade única. Um agregado é composto por uma entidade raiz chamada de _aggregate root_, que controla a persistência e integridade de todas as outras entidades dentro do agregado. As operações no agregado, como criação, atualização e exclusão, devem ser realizadas como um todo, garantindo consistência.

## Exemplo de uso:

```typescript
// Entidades do agregado
class OrderItem {
  constructor(
    public productId: string,
    public quantity: number,
    public price: number
  ) {}
}

class ShippingDetails {
  constructor(
    public address: string,
    public city: string,
    public postalCode: string
  ) {}
}

// Aggregate Root
class Order {
  private items: OrderItem[] = [];

  constructor(
    public orderId: string,
    public customerId: string,
    public shippingDetails: ShippingDetails
  ) {}

  addItem(productId: string, quantity: number, price: number) {
    this.items.push(new OrderItem(productId, quantity, price));
  }

  calculateTotal() {
    return this.items.reduce(
      (total, item) => total + item.quantity * item.price,
      0
    );
  }
}

// Uso do agregado
const shipping = new ShippingDetails("123 Main St", "Cityville", "12345");
const order = new Order("order123", "customer456", shipping);

order.addItem("product789", 2, 100);
order.addItem("product123", 1, 200);

console.log("Total do pedido:", order.calculateTotal());
```

## Quando usar:

- Quando um conjunto de entidades precisa ser tratado como uma unidade coesa.
- Para garantir a consistência e integridade dos dados dentro de um contexto específico.
- Para simplificar a lógica de negócio e manter a complexidade sob controle.

## Exemplo :

```typescript
export class Question extends AggregateRoot<QuestionProps> {
  private _attachments: WatchedList<Attachment>;

  get attachments(): Attachment[] {
    return this._attachments.getItems();
  }

  constructor(props: QuestionProps, id?: UniqueEntityID) {
    super(props, id);
    this._attachments = new WatchedList<Attachment>(props.attachments);
  }

  public addAttachment(attachment: Attachment): void {
    this._attachments.add(attachment);
  }

  public removeAttachment(attachment: Attachment): void {
    this._attachments.remove(attachment);
  }
}
```

- quando eu faco esse extends, eu estou dizendo que a classe Question é um agregado, e que ela é a raiz do agregado.
- a classe AggregateRoot é uma classe base que contem metodos para manipular o agregado, como adicionar, remover, etc.
- a classe QuestionProps é uma interface que contem as propriedades da entidade Question.
- a classe Question pode conter outras entidades, como Answer, Comment, etc, e essas entidades podem ser manipuladas atraves da classe Question.
- aqui no caso a classe Question vai ter anexos que é uma outra entidade, e a classe Question vai ser responsavel por manipular os anexos.
