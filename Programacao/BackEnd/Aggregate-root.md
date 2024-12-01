# Aggregate-root.ts

```typescript
import { Entity } from "@/core/entitites/entity";

export abstract class AggregateRoot<Props> extends Entity<Props> {}
```

# Explicacao:

- Classe abstrata que representa um Aggregate Root
- Um Aggregate Root é uma entidade que é responsável por garantir a consistência de um grupo de entidades
- a classe acima é uma abstração de um Aggregate Root que herda de uma entidade genérica que recebe um tipo de propriedades
