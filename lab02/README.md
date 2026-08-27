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

- ***Comportamento prático da abordagem***: Demonstra a integração gradual dos módulos relacionados ao Pedido, começando pelo módulo principal e avançando para os módulos inferiores. Enquanto Pagamento, Estoque e Entrega ainda não estão disponíveis, são utilizados Stubs para simular seu comportamento. (*Stub = pedaço de código simples que simula um módulo inferior ou dependente que ainda não foi desenvolvido*)
  
- ***Mecanismo técnico***: Foco na integração hierárquica dos módulos. Uso de diagrama de hierarquia de módulos. Módulos: Pedido; Calculadora de Frete; Pagamento Stub; Estoque Stub; Entrega Stub. Conforme os módulos reais ficam disponíveis, os Stubs são substituídos por Pagamento, Estoque e Entrega.
  
- ***Benefícios***: Permite testar os módulos superiores antes que todo o sistema esteja pronto, facilitando a identificação de problemas de integração. Os Stubs permitem controlar as respostas dos módulos ainda não implementados.

### 2.3. [Integração Incremental Bottom-Up (Ascendente) com uso de Drivers](./diagramas/bottom-up.puml) 
Caso: *Finalizar um pedido*

- ***Comportamento prático da abordagem***: Demonstra a integração gradual dos módulos do sistema começando pelos componentes de nível inferior, como Calculadora de Frete, Pagamento, Estoque e Entrega. Os módulos são testados individualmente por meio de Drivers e, posteriormente, integrados ao módulo superior Pedido. (*Driver = pedaço de código que simula um módulo superior ou chamador quando o módulo principal ainda não está pronto, mas as partes inferiores já estão desenvolvidas*)

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
Caso: *Aplicar cupom de desconto*

- ***Comportamento prático da abordagem***: Demonstra a validação da funcionalidade de aplicação de cupom conforme os critérios definidos pelo negócio. O Cliente informa o código do cupom e o Sistema verifica se ele atende aos critérios de validade. Se for válido, o desconto é calculado e o valor do carrinho é atualizado. Caso contrário, uma mensagem de erro é apresentada.
  
- ***Mecanismo técnico***: Foco na validação dos critérios necessários para aceitar a funcionalidade. Uso de diagrama de atividades com raias de responsabilidade, representando as ações do Cliente e do Sistema. O fluxo envolve a funcionalidade aplicarCupom(codigo), incluindo validação do cupom, cálculo do desconto e atualização do valor do carrinho.

- ***Benefícios***: Permite verificar se a funcionalidade atende às regras e expectativas definidas pelo negócio antes de ser considerada concluída, identificando situações em que o comportamento implementado não corresponde aos critérios de aceitação.

### 3.2. [Teste Alfa (Alpha Testing)](./diagramas/alpha.puml)
Caso: *Cadastrar um produto no marketplace*

- ***Comportamento prático da abordagem***: Demonstra a execução da funcionalidade de cadastro de produtos por um Participante do Teste Alfa (representado por Vendedor no diagrama), em um ambiente controlado. O participante acessa a área de cadastro, informa os dados do produto e verifica o comportamento do sistema. Caso existam dados inválidos, visualiza as mensagens de erro, corrige as informações e realiza uma nova tentativa até que o produto seja cadastrado com sucesso.
  
- ***Mecanismo técnico***: Foco na validação da funcionalidade antes de sua disponibilização aos usuários finais. Uso de diagrama de atividades com raias de responsabilidade, representando as ações do Participante do Teste Alfa e do Sistema. O fluxo envolve o cadastro e a validação dos dados do produto, incluindo nome, descrição, preço e quantidade, além do registro do resultado do teste.
  
- ***Benefícios***: Permite identificar defeitos, comportamentos inesperados e problemas de usabilidade em um ambiente controlado antes da liberação da funcionalidade para o público, possibilitando correções com base nos resultados e feedbacks obtidos durante o teste.
  
### 3.3. [Teste Beta (Beta Testing)](./diagramas/beta.puml) 
Caso: *Avaliar um produto comprado*

- ***Comportamento prático da abordagem***: Demonstra a utilização da funcionalidade por um Cliente Beta, que acessa o histórico de pedidos, seleciona um produto comprado e informa uma avaliação. O sistema valida os dados e, caso sejam válidos, publica a avaliação e apresenta a confirmação ao cliente. Caso sejam inválidos, o cliente pode corrigir as informações e tentar novamente.
  
- ***Mecanismo técnico***: Foco na utilização da funcionalidade por usuários externos em condições próximas às reais. Uso de diagrama de atividades com raias de responsabilidade, representando as ações do Cliente Beta e do Sistema. A funcionalidade envolve a validação e a publicação da avaliação, composta por nota e comentário.

- ***Benefícios***: Permite identificar problemas que podem não ter sido encontrados nos testes anteriores, principalmente relacionados ao uso real da funcionalidade, além de verificar se o sistema atende às expectativas dos usuários antes da liberação geral.
    
## 4. Teste de Sistema (System Testing)
### 4.1. [Teste de Recuperação (Recovery Testing)](./diagramas/recovery.puml) 
Caso: *Recuperar um pedido após uma falha do sistema*

- ***Comportamento prático da abordagem***: Demonstra o comportamento do sistema após uma falha durante o processamento de um pedido. O sistema é restaurado e tenta recuperar os dados do pedido. Se os dados estiverem íntegros, o processamento é retomado e o pedido é confirmado. Caso contrário, uma mensagem de erro é apresentada.
  
- ***Mecanismo técnico***: Foco na recuperação do sistema e na integridade dos dados após uma falha. Uso de diagrama de atividades com raias de responsabilidade, representando as ações do Cliente e do Sistema. O fluxo envolve o processamento, a falha, a restauração do sistema e a recuperação dos dados do pedido.
  
- ***Benefícios***: Permite verificar se o sistema consegue retornar ao funcionamento após uma falha sem perder ou corromper dados importantes, identificando problemas de recuperação que poderiam afetar pedidos e usuários.
### 4.2. [Teste de Segurança (Security Testing)](./diagramas/security.puml) 
Caso: *Verificar acesso ao pedido do cliente*

- ***Comportamento prático da abordagem***: Demonstra a verificação de segurança ao acessar um pedido. O sistema verifica se o cliente está autenticado e, em seguida, se o pedido pertence a ele. O acesso é permitido somente quando as duas condições são atendidas.

- ***Mecanismo técnico***: Foco na autenticação e na autorização do acesso aos pedidos. Uso de diagrama de atividades com raias de responsabilidade, representando as ações do Cliente e do Sistema. O sistema realiza as verificações de autenticação e de propriedade do pedido antes de permitir sua visualização.

- ***Benefícios***: Permite identificar falhas de controle de acesso, como um cliente autenticado conseguir visualizar o pedido de outro cliente, protegendo informações privadas dos usuários.

### 4.3. [Teste de Estresse (Stress Testing)](./diagramas/stress.puml) 
Caso: *Acesso à página de um produto sob carga elevada*

- ***Comportamento prático da abordagem***: Demonstra o aumento progressivo de solicitações de acesso à página de um produto para verificar como o sistema se comporta sob uma carga elevada. O sistema processa as solicitações e verifica-se se continua respondendo ou se apresenta degradação.
  
- ***Mecanismo técnico***: Foco no comportamento e na estabilidade do sistema sob carga elevada. Uso de diagrama de atividades, com as raias Teste e Sistema. O Teste envia solicitações e aumenta a carga, enquanto o Sistema processa as solicitações. Ao final, o resultado do teste é registrado, incluindo a ocorrência ou não de degradação.
  
- ***Benefícios***: Permite identificar problemas de desempenho, estabilidade e capacidade quando o sistema é submetido a uma carga elevada, ajudando a encontrar o limite em que o sistema começa a apresentar degradação.
  
### 4.4. [Teste de Desempenho (Performance Testing)](./diagramas/performance.puml)
