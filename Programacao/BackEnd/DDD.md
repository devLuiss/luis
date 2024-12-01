# Domain Driven Design (DDD)

O principal desafio da arquitetura de software é pensar de maneira desconectada das camadas mais externas ao "desenhar" a aplicação.

## Camadas Externas

- Interface com o usuário
- Banco de dados
- Serviços externos
- HTTP

O DDD (Domain Driven Design) reside na camada mais interna, que é o dominio/núcleo da aplicação. Ou seja, o código deve existir independentemente do contexto em que está rodando. Ele deve ser um código puramente JavaScript ou TypeScript, como se fosse um módulo de uma biblioteca, sem dependência de nada.

## Devemos Pensar

Como representar um problema da vida real em código sem qualquer dependência de nada, sem banco de dados, sem HTTP, sem nada.

## INICIO DE UM PROJETO

Quando se pensar no inicio de um projeto depois de definido as tecnologias , devemos comecar a mapear as camadas mais internas da aplicacao, ou seja, o dominio da aplicacao.
sendo : ENTIDADES DE DOMINIO, CASOS DE USO.
Para mapear essas camadas deve ser feito uma conversa com os [[DomainExperts]].

- **DDD (Domain Driven Design)**: Metodologia de desenvolvimento de software que se concentra no domínio do problema, em vez de se preocupar com a tecnologia. O DDD ajuda a alinhar o código com as regras de negócio, facilitando a manutenção e a evolução do sistema.

  - **Entidades de Domínio**: Objetos que representam conceitos do domínio, com identidade própria e regras de negócio associadas.

  - **Casos de Uso**: Funcionalidades do sistema que representam interações entre o usuário e as entidades de domínio.

  - **Agregados**: Grupos de entidades relacionadas que são tratadas como uma única unidade. Os agregados são delimitados por uma entidade raiz que garante a consistência e a integridade das demais entidades.

  - **Repositórios**: Interfaces que definem operações de acesso e persistência de entidades. Os repositórios são implementados por classes concretas que interagem com o banco de dados ou outras fontes de dados.

  - **Serviços de Domínio**: Classes que encapsulam regras de negócio complexas que não pertencem a uma única entidade. Os serviços de domínio são usados para operações que envolvem múltiplas entidades ou agregados.

  - **Value Objects**: Objetos imutáveis que representam valores sem identidade própria. Os value objects são usados para modelar conceitos que não têm identidade única, como datas, horas, endereços, etc.

  - **Eventos de Domínio**: Mensagens que representam eventos importantes no ciclo de vida das entidades. Os eventos de domínio são usados para notificar outras partes do sistema sobre mudanças ou ações realizadas.

  - **Especificações**: Classes que representam critérios de seleção de entidades. As especificações são usadas para filtrar entidades com base em regras de negócio específicas.

  - **Fábricas**: Classes que encapsulam a lógica de criação de entidades complexas. As fábricas são usadas para criar instâncias de entidades com base em parâmetros específicos.
