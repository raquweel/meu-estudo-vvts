# Diagramas e suas utilizações
Cenário: Plataforma de E-commerce e Marketplace de grande porte
## 1. Teste de Unidade (Unit Testing)
### 1.1. [Teste de unidade](./diagramas/unidade.puml)
Caso: *Calcular o valor do frete*
- ***Comportamento prático da abordagem***: Demonstra um teste isolado do componente CalculadoraFrete para validar a lógica de cálculo do valor do frete. A CalculadoraFrete utiliza as informações do Pedido, como valor total e peso, e do EnderecoEntrega, que contém o CEP de destino. A classe CalculadoraFreteTest verifica individualmente o cálculo do frete por peso e a aplicação da regra de frete grátis.
  
- ***Mecanismo técnico***: Foco na lógica de cálculo. Uso de diagrama de classes. Classes: Pedido (valorTotal, pesoTotal); EnderecoEntrega (cep); CalculadoraFrete (contém o método calcularFrete()); CalculadoraFreteTest (realiza os testes da CalculadoraFrete).

- ***Benefícios***: Por ser um teste isolado e rápido, facilita encontrar exatamente onde está o problema antes que a funcionalidade seja integrada ao restante do e-commerce.

## 2. Teste de Integração (Integration Testing)
### 2.1. [Integração Não Incremental (Big Bang)](./diagramas/big-bang.puml)
Caso: *Finalizar uma compra*
- ***Comportamento prático da abordagem***: Demonstra a integração simultânea dos principais componentes do processo de compra. O Cliente adiciona itens ao Carrinho e finaliza o Pedido, que se comunica com os componentes CalculadoraFrete, Pagamento, Estoque e Entrega. Todos os componentes são integrados antes da realização do teste.
  
- ***Mecanismo técnico***: Foco na comunicação entre os componentes/partes maiores do sistema. Uso de diagrama de componentes. Componentes: Carrinho; Pedido; CalculadoraFrete; Pagamento; Estoque; Entrega; e Teste, responsável por verificar o funcionamento do conjunto integrado.

- ***Benefícios***: Permite verificar se os principais componentes conseguem funcionar corretamente em conjunto e identificar problemas nas interfaces e na comunicação entre eles. Entretanto, como todos são integrados de uma vez, pode ser mais difícil identificar qual componente causou uma falha.

### 2.2. [Integração Incremental Top-Down (Descendente) com uso de Stubs](./diagramas/top-down.puml) 

### 2.3. [Integração Incremental Bottom-Up (Ascendente) com uso de Drivers](./diagramas/bottom-up.puml) 

### 2.4. [Teste de Fumaça (Smoke Testing)](./diagramas/smoke.puml) 

### 2.5. [Teste de Regressão](./diagramas/regressao.puml)
    
## 3. Teste de Validação (Validation Testing)
### 3.1. [Critérios de Aceitação (User Acceptance Testing)](./diagramas/aceitacao.puml) 

### 3.2. [Teste Alfa (Alpha Testing)](./diagramas/alpha.puml)
### 3.3. [Teste Beta (Beta Testing)](./diagramas/beta.puml) 
    
## 4. Teste de Sistema (System Testing)
### 4.1. [Teste de Recuperação (Recovery Testing)](./diagramas/recovery.puml) 
### 4.2. [Teste de Segurança (Security Testing)](./diagramas/security.puml) 
### 4.3. [Teste de Estresse (Stress Testing)](./diagramas/stress.puml) 
### 4.4. [Teste de Desempenho (Performance Testing)](./diagramas/performance.puml)
