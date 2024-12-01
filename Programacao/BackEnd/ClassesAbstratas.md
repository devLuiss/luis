# Classes abstratas

Uma classe abstrata é uma classe que não pode ser instanciada, ou seja, não é possível criar um objeto a partir dela. Ela é utilizada como base para outras classes que herdam dela, e que podem ser instanciadas.

```typescript
abstract class Animal {
  abstract makeSound(): void;
}

class Dog extends Animal {
  makeSound() {
    console.log("Au au");
  }
}

const dog = new Dog();

dog.makeSound(); // Saída: "Au au"
```

- A classe abstrata nao pode ser criada diretamente `const animal = new Animal();` pois ela é uma classe base para outras classes.
- A classe que herda da classe abstrata deve implementar todos os métodos abstratos definidos na classe base.
- A classe que herda da classe abstrata pode ser instanciada.
