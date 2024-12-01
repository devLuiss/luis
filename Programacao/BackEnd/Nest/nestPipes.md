## Pipe/s

- sao midlewares / interceptadores
- validacoes por exemplo

ex:

```typescript
import { BadRequestException, PipeTransform } from "@nestjs/common";
import { ZodError, ZodSchema } from "zod";
import { fromZodError } from "zod-validation-error";

export class ZodValidationPipe implements PipeTransform {
  constructor(private schema: ZodSchema) {}

  transform(value: unknown) {
    try {
      return this.schema.parse(value);
    } catch (error) {
      if (error instanceof ZodError) {
        throw new BadRequestException({
          message: "Validation failed",
          statusCode: 400,
          errors: fromZodError(error),
        });
      }
      throw new BadRequestException("Validation failed");
    }
    return value;
  }
}
```

no exemplo acima, o pipe `ZodValidationPipe` é um pipe de validação que usa a biblioteca `zod` para validar os dados de entrada. Se a validação falhar, ele lança uma exceção `BadRequestException` com uma mensagem de erro e os detalhes do erro de validação.
