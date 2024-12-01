### SOLID

![SOLIDE](https://miro.medium.com/v2/resize:fit:720/format:webp/1*v-moZEu-SekhA-nnR3x5Dg.png)

- **S**ingle Responsibility Principle (Princípio da Responsabilidade Única)
- **O**pen/Closed Principle (Princípio do Aberto/Fechado )
- **L**iskov Substitution Principle (Princípio da Substituição de Liskov)
- **I**nterface Segregation Principle (Princípio da Segregação de Interfaces)
- **D**ependency Inversion Principle (Princípio da Inversão de Dependências)

### S - Princípio da Responsabilidade Única (SRP) + DDD (Agregados)

Cada classe ou componente do sistema deve ter uma única responsabilidade, alinhada ao agregado relevante no DDD.
Exemplo no LEADBROKER:
Dentro do contexto de bidding, a classe LeadBiddingService (responsável por gerenciar o leilão de leads) deve estar isolada de outros processos como a validação de leads, que seria tratada por uma classe separada LeadValidator. No DDD, o leilão de leads pode ser visto como um agregado, encapsulando toda a lógica e regras de domínio associadas à compra e venda de leads. Isso evita o acoplamento de regras de outros domínios.

### O - Princípio Aberto/Fechado (OCP) + DDD (Entidades)

O sistema deve ser extensível sem modificar as entidades principais do domínio, seguindo o modelo de entidades do DDD.
Exemplo no LEADBROKER:
A entidade LeadBid pode ser estendida para diferentes tipos de lances, como AutomaticBid ou ManualBid, sem alterar a entidade central LeadBid. Isso permite que novas funcionalidades de bidding sejam adicionadas sem modificar o comportamento do bidding principal. No DDD, LeadBid seria uma entidade essencial do domínio, e esse comportamento garantiria que a lógica de domínio seja flexível e extensível.

### L - Princípio da Substituição de Liskov (LSP) + DDD (Entidades)

Subclasses devem substituir suas classes base de maneira que o comportamento do sistema não mude, respeitando as regras do domínio.
Exemplo no LEADBROKER:
Se a entidade Comprador tem subclasses como CompradorAutomático e CompradorManual, ambos devem funcionar de forma intercambiável sem alterar as regras de domínio do leilão de leads. No DDD, essas seriam diferentes entidadesdentro do mesmo contexto, mas que podem ser usadas sem quebrar as regras estabelecidas no domínio da compra de leads.

### I - Princípio da Segregação de Interfaces (ISP) + DDD (Serviços de Domínio)

As interfaces devem ser focadas em uma responsabilidade específica, como serviços de domínio em DDD, que são usados para executar ações específicas.
Exemplo no LEADBROKER:
No lugar de uma interface LeadManager que lida com todas as operações, interfaces mais específicas como LeadBidder(para lances) e LeadProcessor (para processar leads) podem ser usadas. Esses seriam serviços de domínio no DDD, cada um focado em uma ação específica dentro do contexto do leilão de leads, evitando que um serviço ou interface fique sobrecarregado.

### D - Princípio da Inversão de Dependências (DIP) + DDD (Repositorios e Interfaces)

Classes de alto nível não devem depender de implementações concretas, e sim de abstrações. Em DDD, isso se alinha com o uso de repositórios e interfaces para acessar e persistir as entidades.
Exemplo no LEADBROKER:
A classe LeadAuctionManager (responsável por gerenciar o leilão) não deve depender diretamente de uma implementação específica, como EmailNotifier. Em vez disso, ela deve depender de uma abstração como Notifier, que poderia ser implementada por diferentes notificadores, como SMSNotifier ou SlackNotifier. No DDD, os repositóriosdesempenham essa função de abstração, isolando o acesso às entidades e agregados e permitindo que o sistema evolua sem grandes mudanças.

### Referências

- Livro Clean Architecture, Robert C. Martin (Uncle Bob) : capitulos 7 ao 11
