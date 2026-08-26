# Diagramas e suas utilizações
Cenário: Plataforma de E-commerce e Marketplace de grande porte
## 1. Teste de Unidade (Unit Testing)
### 1.1. [Teste de unidade](./diagramas/unidade.puml)
Caso: Calcular o valor do frete
- Demonstra um teste unitário do componente CalculadoraFrete para validar a lógica de cálculo do frete com base no peso do pedido e na regra de frete grátis.
Utiliza a classe CalculadoraFreteTest, com os testes calculaFretePorPeso() e freteGratis(), para verificar cada comportamento individualmente. A dependência ConsultaFrete é substituída por ConsultaFreteStub, permitindo testar a lógica sem depender de serviços externos;
- O teste de unidade permite testar uma pequena parte isolada do sistema.

## 2. Teste de Integração (Integration Testing)
### 2.1. [Integração Não Incremental (Big Bang)](./diagramas/big-bang.puml)

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
