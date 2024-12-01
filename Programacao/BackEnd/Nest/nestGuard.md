## Guards (Proteção de Rotas)

- **Guards** no NestJS são usados para proteger rotas e determinar se uma requisição pode ou não ser processada com base em certas condições. Eles funcionam como "porteiros" para as rotas, decidindo se a requisição deve ou não seguir adiante.
- Um **Guard** é basicamente uma classe que implementa a interface `CanActivate`, que tem um método `canActivate()` que retorna `true` (se a requisição pode prosseguir) ou `false` (se ela deve ser bloqueada). Esse método pode ser **assíncrono** e também pode retornar uma `Promise<boolean>`.
