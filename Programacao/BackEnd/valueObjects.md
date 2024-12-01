#### Objetos de Valor (Value Objects)

- **Objetos de Valor**: São imutáveis e definidos pelos seus atributos, não possuindo identidade própria. Representam aspectos do domínio que possuem significado, mas não identidade única.
- **Exemplo**: Em um sistema de compras online, um Endereço pode ser modelado como um Value Object, pois é definido pelos atributos como rua, número, bairro, cidade, estado e CEP.
- **Importância**: Facilitam a comparação e manipulação de dados sem a necessidade de gerenciar identidades únicas.
