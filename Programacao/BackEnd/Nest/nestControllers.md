## Controllers:

- São a **porta de entrada** da aplicação através do HTTP.
- Quando o usuário faz uma requisição HTTP, o primeiro lugar que o Nest usa para processar a requisição é o **Controller**.
- No NestJS, os Controllers são identificados com o decorator `@Controller`. Esse decorator transforma a classe em um controlador, permitindo que seus métodos sejam mapeados para rotas HTTP.
- **Métodos HTTP** como `@Get`, `@Post`, `@Put`, `@Delete` são decorators usados nos métodos da classe Controller para definir as rotas e os tipos de requisições que esses métodos lidam.
- Por exemplo, um método com o decorator `@Get()` será acionado quando uma requisição GET for feita à rota associada.
- Você pode passar parâmetros para os decorators `@Controller` e `@Get` para definir **prefixos e rotas** específicas. Exemplo: `@Controller('api')` vai prefixar todas as rotas desse controller com `/api`, e `@Get('hello')` vai responder à rota `/api/hello`.
- Isso facilita organizar rotas e criar APIs RESTful de maneira eficiente.
  [[Controllers]]
