## Módulos (Modules):

- Um **módulo** no NestJS é responsável por **organizar** e **reunir** várias partes da aplicação como controllers, serviços, configurações e conexões com bancos de dados.
- **Módulos** são a base estrutural da aplicação no NestJS, funcionando como "pacotes" que agrupam diferentes funcionalidades.
- Um módulo agrupa controllers e providers (serviços) que o módulo irá usar.
  - **Controllers**: São os controllers que fazem parte desse módulo.
  - **Providers**: São classes ou serviços que implementam lógica de negócio ou se conectam a um banco de dados, e que podem ser injetados em controllers ou em outros serviços.
