- #### Repositórios

- **Repositórios**: São responsáveis por encapsular a lógica de acesso aos dados e abstrair o armazenamento de entidades. Eles fornecem uma interface para buscar, salvar, atualizar e deletar entidades, sem expor os detalhes de como os dados são persistidos.
- **Importância**: Repositórios ajudam a manter a camada de domínio independente da infraestrutura (bancos de dados, APIs), respeitando o princípio da inversão de dependência. Eles também permitem testar o domínio de forma mais fácil, já que a lógica de acesso a dados pode ser facilmente simulada.
