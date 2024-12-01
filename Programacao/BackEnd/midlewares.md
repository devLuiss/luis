### Midlewares

- **Middlewares** são funções que têm acesso ao objeto de solicitação (req), ao objeto de resposta (res) e à próxima função de middleware no ciclo de solicitação/resposta. Eles podem executar qualquer código, fazer alterações nos objetos de solicitação e resposta, encerrar o ciclo de solicitação/resposta ou chamar a próxima função de middleware.

#### Exemplo de Middleware no NestJS

```typescript
import { Injectable, NestMiddleware } from "@nestjs/common";
import { Request, Response, NextFunction } from "express";

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    console.log(`Request...`);
    next();
  }
}
```
