# Subdomínios no DDD

## Introdução

**Subdomínios** são como dividimos o domínio da nossa aplicação, que representa todo o conjunto de problemas que o software resolve, em pequenas partes. A ideia é entender como repartir a lógica do negócio para facilitar o desenvolvimento, a manutenção e a comunicação entre os times.

Subdomínios não se referem diretamente à separação de lógica de código, mas ao negócio e à problemática que estamos resolvendo. Eles ajudam a organizar melhor o entendimento das partes envolvidas no sistema.

---

## Tipos de Subdomínios

Subdomínios são geralmente classificados em três tipos principais:

### 1. Core Subdomains

- **Descrição**: São os subdomínios essenciais para o negócio, que geram valor diretamente ou são fundamentais para o funcionamento do software.
- **Características**:
  - Representam o "coração" do domínio.
  - Dificilmente podem ser terceirizados.
  - Devem ser priorizados no desenvolvimento.
  - Exemplos em um e-commerce:
    - Compra
    - Catálogo
    - Pagamento
    - Entrega
- **Importância**: Se qualquer core subdomain parar de funcionar, o negócio estará em risco.

---

### 2. Supporting Subdomains

- **Descrição**: Dão suporte para que os core subdomains possam funcionar corretamente.
- **Características**:
  - Não são essenciais por si só, mas suportam os processos principais.
  - Exemplos em um e-commerce:
    - Estoque (dá suporte ao catálogo e à compra).
- **Importância**: Apesar de menos críticos, são necessários para garantir que os processos core fluam corretamente.

---

### 3. Generic Subdomains

- **Descrição**: São subdomínios que podem ser facilmente substituídos ou terceirizados.
- **Características**:
  - Não impactam diretamente o core do negócio.
  - Muitas vezes, são genéricos o suficiente para utilizar soluções prontas.
  - Exemplos em um e-commerce:
    - Notificações ao cliente
    - Sistema de promoções
    - Chat de atendimento
- **Importância**: Facilitam a operação, mas não são indispensáveis para o funcionamento.

---

## Comunicação Entre Subdomínios

Subdomínios devem ser independentes, mesmo que estejam na mesma base de código. É importante desacoplar suas responsabilidades, permitindo que um subdomínio continue funcionando mesmo que outro seja alterado ou removido.

- **Comunicação**:
  - No caso de monólitos, a comunicação pode ser síncrona, mas ainda deve ser desacoplada.
  - Usar **domain events** para enviar notificações entre subdomínios é uma abordagem comum.
- **Boas Práticas**:
  - Não criar dependências diretas de código entre subdomínios.
  - Priorizar comunicação desacoplada para maior flexibilidade.

---

## Aplicação Prática

Ao desenvolver um sistema:

1. **Divida os subdomínios** considerando o negócio e as necessidades do cliente.
2. **Identifique o que é core, supporting e generic**.
3. Foque no desenvolvimento dos core subdomains com maior qualidade e priorize o suporte e genéricos para soluções terceirizadas, quando possível.

---

## Exemplos de Subdomínios

### Sistema de Fórum:

- **Core**: Criação e interação com tópicos.
- **Supporting**: Sistema de notificações (pode variar de acordo com a necessidade).
- **Generic**: Personalização do tema do fórum.

### Sistema de E-commerce:

- **Core**: Pagamentos, catálogo, compras.
- **Supporting**: Estoque, logística.
- **Generic**: Chat de atendimento, notificações.

---

## Conclusão

Entender e dividir o domínio em subdomínios ajuda a:

- Organizar o desenvolvimento de software.
- Priorizar esforços no que realmente importa.
- Criar sistemas mais escaláveis e flexíveis.

Subdomínios não são apenas uma questão técnica; eles refletem como o negócio é estruturado e operado.
"""
