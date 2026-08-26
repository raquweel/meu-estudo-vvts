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
Caso: *Finalizar um pedido*
- ***Comportamento prático da abordagem***: Demonstra a integração simultânea dos principais componentes do processo de compra. O Cliente adiciona itens ao Carrinho e finaliza o Pedido, que se comunica com os componentes CalculadoraFrete, Pagamento, Estoque e Entrega. Todos os componentes são integrados antes da realização do teste.
  
- ***Mecanismo técnico***: Foco na comunicação entre os componentes/partes maiores do sistema. Uso de diagrama de componentes. Componentes: Carrinho; Pedido; CalculadoraFrete; Pagamento; Estoque; Entrega; e Teste, responsável por verificar o funcionamento do conjunto integrado.

- ***Benefícios***: Permite verificar se os principais componentes conseguem funcionar corretamente em conjunto e identificar problemas nas interfaces e na comunicação entre eles. Entretanto, como todos são integrados de uma vez, pode ser mais difícil identificar qual componente causou uma falha.

### 2.2. [Integração Incremental Top-Down (Descendente) com uso de Stubs](./diagramas/top-down.puml) 
Caso: *Finalizar um pedido*

- ***Comportamento prático da abordagem***: Demonstra a integração gradual dos módulos relacionados ao Pedido, começando pelo módulo principal e avançando para os módulos inferiores. Enquanto Pagamento, Estoque e Entrega ainda não estão disponíveis, são utilizados Stubs (*Stub = pedaço de código simples que simula um módulo inferior ou dependente que ainda não foi desenvolvido*) para simular seu comportamento.
  
- ***Mecanismo técnico***: Foco na integração hierárquica dos módulos. Uso de diagrama de hierarquia de módulos. Módulos: Pedido; Calculadora de Frete; Pagamento Stub; Estoque Stub; Entrega Stub. Conforme os módulos reais ficam disponíveis, os Stubs são substituídos por Pagamento, Estoque e Entrega.
  
- ***Benefícios***: Permite testar os módulos superiores antes que todo o sistema esteja pronto, facilitando a identificação de problemas de integração. Os Stubs permitem controlar as respostas dos módulos ainda não implementados.

### 2.3. [Integração Incremental Bottom-Up (Ascendente) com uso de Drivers](./diagramas/bottom-up.puml) 
Caso: *Finalizar um pedido*

- ***Comportamento prático da abordagem***: Demonstra a integração gradual dos módulos do sistema começando pelos componentes de nível inferior, como Calculadora de Frete, Pagamento, Estoque e Entrega. Os módulos são testados individualmente por meio de Drivers (*Driver = pedaço de código que simula um módulo superior ou chamador quando o módulo principal ainda não está pronto, mas as partes inferiores já estão desenvolvidas*) e, posteriormente, integrados ao módulo superior Pedido.

- ***Mecanismo técnico***: Foco na integração dos módulos de baixo para cima. Uso de diagrama de componentes. Componentes: Pedido; Calculadora de Frete; Pagamento; Estoque; Entrega; e seus respectivos Drivers, que acionam os módulos inferiores durante os testes.

- ***Benefícios***: Permite testar os módulos inferiores antes da implementação ou integração dos módulos superiores. Os Drivers simulam as chamadas que seriam feitas pelo Pedido, facilitando a identificação de erros nos módulos e nas suas interfaces.

### 2.4. [Teste de Fumaça (Smoke Testing)](./diagramas/smoke.puml) 
Caso: *Realizar login no e-commerce*

- ***Comportamento prático da abordagem***: Demonstra uma verificação rápida do fluxo principal de login. O cliente acessa a tela, informa e-mail e senha e envia o formulário. O sistema verifica os dados e, caso sejam válidos, permite o acesso à área do cliente. Caso contrário, apresenta uma mensagem de erro.
  
- ***Mecanismo técnico***: Foco no fluxo principal da funcionalidade. Uso de fluxograma, representando as etapas de acesso, preenchimento, validação e resultado do login.

- ***Benefícios***: Permite verificar rapidamente se uma funcionalidade essencial do e-commerce está funcionando após uma nova versão ou alteração no sistema, identificando falhas graves que impediriam a continuidade dos testes.

### 2.5. [Teste de Regressão](./diagramas/regressao.puml)
Caso: *Finalizar uma compra após alteração no cálculo do frete*

- ***Comportamento prático da abordagem***: Demonstra a execução novamente do fluxo de compra após uma alteração na CalculadoraFrete. O Cliente adiciona um item ao Carrinho, finaliza o Pedido, que solicita o cálculo do frete e, em seguida, realiza o pagamento. O objetivo é verificar se a alteração no cálculo do frete não afetou o funcionamento das demais etapas da compra.
  
- ***Mecanismo técnico***: Foco na reexecução de uma funcionalidade que já funcionava anteriormente. Uso de diagrama de sequência. Participantes: Cliente, Carrinho, Pedido, CalculadoraFrete e Pagamento. O fluxo utiliza os métodos adicionaItem(), finalizaPedido(), calcularFrete() e processarPagamento().
  
- ***Benefícios***: Permite identificar defeitos introduzidos por alterações no sistema, verificando se funcionalidades existentes continuam funcionando corretamente. Também ajuda a detectar efeitos colaterais em componentes que não foram diretamente modificados.
    
## 3. Teste de Validação (Validation Testing)
### 3.1. [Critérios de Aceitação (User Acceptance Testing)](./diagramas/aceitacao.puml) 

### 3.2. [Teste Alfa (Alpha Testing)](./diagramas/alpha.puml)
### 3.3. [Teste Beta (Beta Testing)](./diagramas/beta.puml) 
    
## 4. Teste de Sistema (System Testing)
### 4.1. [Teste de Recuperação (Recovery Testing)](./diagramas/recovery.puml) 
### 4.2. [Teste de Segurança (Security Testing)](./diagramas/security.puml) 
### 4.3. [Teste de Estresse (Stress Testing)](./diagramas/stress.puml) 
### 4.4. [Teste de Desempenho (Performance Testing)](./diagramas/performance.puml)
