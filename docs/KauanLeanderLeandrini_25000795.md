# Avaliação — Engenharia de Software 
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Kauan Leander Leandrini

RA: 25000795

Data: 25/03/2026

---

# 1. Definição do MVP 
Descreva aqui **qual parte do sistema** foi incluída no seu MVP. 
Explique claramente:

Meu MVP integra processos de vendas de produtos em uma unidade de farmácia, iniciando na identificação ou cadastro de clientes, em seguida passa em uma consulta de produtos, análise de estoque, registro da venda, finalizando com uma emissão de comprovante. Além disso, está incluso o processo de vendas a prazo, gerando automaticamente a parte de contas a receber.

Fora do MVP ficaram funcionalidades como controle de fornecedores, sistema avançado de compras, relatórios específicos, integração de muitas unidades e controle detalhado de contas a pagar.

Fiz essas escolhas visando reduzir a complexidade inicial do sistema, focando no principal fluxo operacional de uma farmácia, que seria a venda. Sendo assim, pode-se obter um sistema consistente e que funcione, focando no fluxo principal do negócio.

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 — Produtos com quantidade insuficiente em estoque não podem ser comercializados.**

**RN02 — É necessário que o cliente tenha cadastro para efetuar compras a prazo.** 

**RN03 — Toda a venda deve gerar um comprovante detalhando a operação.** 

**RN04 — É preciso que o estoque seja automaticamente atualizado ao final de cada venda.** 

**RN05 — Todos os produtos para serem vendidos devem ter seus preços de venda definidos.** 

**RN06 — As vendas efetuadas a prazo precisam gerar de imediato um lançamento em contas a receber.**  

**RN07 — Produtos controlados só podem ser comercializados com a validação de receita médica.**  

---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 — O sistema deve permitir o cadastro de novos clientes.**  
**RF02 — O sistema deve permitir pesquisas de produtos pelo nome, fabricante e código de barras.**  
**RF03 — O sistema precisa permitir a identificação de clientes que já possuam cadastro.**  
**RF04 — O sistema deve verificar a quantidade disponível em estoque e informar os valores atualizados antes de confirmar a venda.**  
**RF05 — O sistema precisa permitir o registro de vendas de produtos.**  
**RF06 — O sistema precisa calcular o valor total de cada venda.**  
**RF07 — O sistema deve emitir comprovantes no final de cada venda.**  
**RF08 — O sistema precisa registrar vendas feitas a prazo e gerar contas a receber.**  
**RF09 — O sistema precisa atualizar imediatamente o estoque depois de cada venda.**
**RF10 — O sistema deve permitir que o farmacêutico valide receitas médicas para produtos controlados.**
**RF11 — O sistema precisa verificar o estoque levando em conta a unidade da farmácia onde a venda está sendo efetuada.**

---

# 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 — O sistema precisa responder à operações de consulta de produtos em até 2 segundos.**  
**RNF02 — O sistema deve permitir que apenas usuários com autorização acessem funcionalidades específicas.**  
**RNF03 — O sistema deve estar disponível conforme o horário de funcionamento da farmácia.**  
**RNF04 — O sistema precisa garantir integridade de dados de vendas e estoque.**  
**RNF05 — O sistema deve ter uma interface de fácil uso e simples para os atendentes.** 

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 12 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends
<img width="1221" height="784" alt="UCGeral_puml" src="https://github.com/user-attachments/assets/8c297b8c-4d6b-43be-95c7-848f7221475b" />

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UC01 — Registrar Venda**
**Ator(es): Atendente**  
**Descrição: Realiza totalmente o preocesso de venda de produtos.**  
**Pré-condições: Sistema ativo; produtos cadastrados.**  
**Pós-condições: Registro da venda, atualização do estoque e comprovante emitido.**  

### Fluxo Principal
1. Atendente inicia a venda.
2. Sistema solicita identificação do cliente.
3. Atendente informa cliente.
4. Sistema permite consulta de produtos.
5. Atendente seleciona produto.
6. Atendente informa quantidade.
7. Sistema verifica estoque.
8. Sistema calcula total.
9. Atendente confirma venda.
10. Sistema emite comprovante.

### Fluxos Alternativos / Exceções
**- FA01 —  Cliente sem cadastro:**
- Efetua cadastro do cliente.

**- FA02 —  Estoque insuficiente:**
- Sistema acusa um erro e o item é cancelado.

### Relacionamentos
- **Include:** (Identificar Cliente, Consultar Produto, Verificar Estoque, Calcular Total, Emitir Comprovante)  
- **Extend:** (Registrar Venda a Prazo, Validar Receita Médica)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="353" height="1071" alt="UC1_puml" src="https://github.com/user-attachments/assets/430e4d34-893f-44bb-b6db-ad689fb4b815" />

---

## **UC02 — Identificação do Cliente**
**Ator(es): Atendente, Cliente**  
**Descrição: Atendente identifica cliente para vincular à venda.**  
**Pré-condições: Cliente pode ou não estar cadastrado.**  
**Pós-condições: Cliente identificado no sistema.**  

### Fluxo Principal
1. Sistema solicita dados do cliente. 
2. Atendente informa dados. 
3. Sistema busca cliente. 
4. Sistema retorna cliente encontrado. 

### Fluxos Alternativos / Exceções
**- FA01 —  Cliente não encontrado:**
- Sugere cadastro do cliente.

### Relacionamentos
- **Extend:** (Cadastrar Cliente)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="259" height="311" alt="UC2_puml" src="https://github.com/user-attachments/assets/81d8e6d0-3e33-4543-b1c6-f6c5a1d0eb17" />

---

## **UC03 — Cadastrar Cliente**
**Ator(es): Atendente**  
**Descrição: Realiza cadastros de novos clientes.**  
**Pré-condições: Cliente não cadastrado.**  
**Pós-condições: Cliente registrado no sistema.**  

### Fluxo Principal
1. Atendente informa dados dos cliente.  
2. Sistema valida dados.  
3. Sistema salva cadastro do cliente. 

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="181" height="247" alt="UC3_puml" src="https://github.com/user-attachments/assets/7fad697c-21a4-4788-8dce-01004d4b8c16" />

---

## **UC04 — Consultar Produto**
**Ator(es): Atendente**  
**Descrição: Permite busca de produtos.**  
**Pré-condições: Produtos cadastrados.**  
**Pós-condições: Produto encontrado.**  

### Fluxo Principal
1. Atendente informa os critérios de busca.
2. Sistema lista produtos.
3. Atendente seleciona produto desejado.

### Relacionamentos
- **Include:** (Selecionar Produto)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="181" height="247" alt="UC4_puml" src="https://github.com/user-attachments/assets/7abea656-e252-49c4-b46e-d7f7fe262bd4" />

---

## **UC05 — Selecionar Produto**
**Ator(es): Atendente**  
**Descrição: Escolhe um produto da lista.**  

### Fluxo Principal
1. Atendente escolhe o produto.

### Relacionamentos
- **Include:** (Informar quantidade)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="135" height="137" alt="UC5_puml" src="https://github.com/user-attachments/assets/8246af2f-bc20-473e-b42b-302e0f11856b" />

---

## **UC06 — Informar Quantidade**
**Ator(es): Atendente**  
**Descrição: Define quantidade desejada.**  

### Fluxo Principal
1. Atendente informa a quantidade.
2. Sistema aplica valor do produto.

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="152" height="192" alt="UC06_puml" src="https://github.com/user-attachments/assets/65f20d51-a452-4a5f-bfac-ccd4353ce93c" />

---

## **UC07 — Verificar Estoque**
**Ator(es): Sistema**  
**Descrição: Confere disponibilidade do produto.**  

### Fluxo Principal
1. Sistema consulta estoque.
2. Sistema retorna quantidade disponível.

### Fluxos Alternativos / Exceções
**- FA01 —  Estoque insuficiente:**
- Retorna erro.

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="308" height="256" alt="UC7_puml" src="https://github.com/user-attachments/assets/066e3d92-ef8a-4ba2-9b96-37a833808743" />

---

## **UC08 — Calcular Total**
**Ator(es): Sistema**  
**Descrição: Calcula o valor total da venda.**  

### Fluxo Principal
1. Sistema soma valores dos itens.

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="175" height="192" alt="UC8_puml" src="https://github.com/user-attachments/assets/2e0f2d82-f515-4c24-b8ef-c8ee2e19e7ca" />

---

## **UC09 — Emitir Comprovante**
**Ator(es): Sistema**  
**Descrição: Gera comprovante da venda.**  

### Fluxo Principal
1. Sistema gera comprovante.
2. Sistema apresenta ao cliente.

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="146" height="192" alt="UC9_puml" src="https://github.com/user-attachments/assets/fee0d692-1abc-4cda-bfcd-cc630b398bd5" />

---

## **UC10 — Registrar Venda a Prazo**
**Ator(es): Atendente**  
**Descrição: Permite venda com pagamento posterior.**  
**Pré-condições: Cliente cadastrado.**  

### Fluxo Principal
1. Atendente seleciona opção a prazo.
2. Sistema registra venda.

### Relacionamentos
- **Extend:** (Gerar Conta a Receber)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="180" height="192" alt="UC10_puml" src="https://github.com/user-attachments/assets/2d757b94-8ac8-4c67-9adb-244d72773c99" />

---

## **UC11 — Gerar Conta a Receber**
**Ator(es): Sistema**  
**Descrição: Registra valor a ser pago futuramente.**  

### Fluxo Principal
1. Sistema cria lançamento financeiro.
   
### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="193" height="192" alt="UC11_puml" src="https://github.com/user-attachments/assets/f1968bea-ef78-4344-8338-cbc1f632c4ef" />

---

## **UC12 — Validar Receita Médica**
**Ator(es): Farmacêutico**  
**Descrição: Autoriza venda de produtos controlados.**  
**Pré-condições: Produto controlado.**   

### Fluxo Principal
1. Farmacêutico analisa receita.
2. Sistema valida autorização.

### Fluxos Alternativos / Exceções
**- FA01 —  Receita inválida**
- Venda bloqueada. 

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
<img width="250" height="311" alt="UC12_puml" src="https://github.com/user-attachments/assets/06aa546d-ba8d-4758-bca5-7da356842a8f" />

---
