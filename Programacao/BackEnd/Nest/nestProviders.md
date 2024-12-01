## Services (Serviços/Providers):

- Um **serviço** (ou **Provider** no contexto do Nest) é qualquer classe que contenha lógica de negócio, acesso a banco de dados, ou outras funções reutilizáveis.
- **Providers** podem ser injetados em Controllers ou em outros Providers.
- Exemplo: `AppService` pode ser um serviço que contém lógica para buscar ou manipular dados e que é injetado em um Controller para lidar com requisições HTTP.
- Todos os serviços precisam ser marcados com o decorator `@Injectable()` para que possam ser injetados como dependências em outras partes da aplicação.
