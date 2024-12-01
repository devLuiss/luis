## Decorators:

- **Decorators** são funções especiais que adicionam comportamento a **classes**, **métodos**, **propriedades**, ou até **parâmetros**.
- Eles são usados extensivamente no NestJS e são herdados de conceitos do TypeScript e até do Java (JSF, JSP).
- Em termos simples, eles são como funções que recebem uma classe ou um método como argumento e **modificam seu comportamento** de alguma maneira.
- Exemplo de decorators no NestJS:
  - `@Controller`: Marca uma classe como um controlador HTTP.
  - `@Get`, `@Post`: Definem métodos que respondem a requisições HTTP específicas.
  - `@Injectable`: Marca uma classe como algo que pode ser **injetado** em outras classes (injeção de dependência).
- Você pode criar seus próprios decorators para reutilizar lógicas e comportamentos personalizados.
