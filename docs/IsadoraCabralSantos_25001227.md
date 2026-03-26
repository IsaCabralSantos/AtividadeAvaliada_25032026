# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia**

Aluno: *Isadora Cabral dos Santos*  
RA: *25001227*  
Data: *25/03/2026*  

---

# 1. Definição do MVP
O meu MVP exemplifica o processo de venda da farmácia, indo desde a identificação e cadastro do cliente (caso não esteja), o processo da compra de verificar se tem estoque ou não e finalizar a compra.

No MVP está o cadastro de cada cliente, consulta de produtos, realização de vendas e também gerar contas a receber.
# Fica fora:
- **compras**
- **contas a pagar**
- **relatórios**
- **controle completo dos usuários**

---

# 2. Regras de Negócio (mínimo: 5)

- **RN01 — Um produto só pode ser vendido se houver quantidade suficiente em estoque.**
- **RN02 — Toda venda realizada deve atualizar automaticamente o estoque da unidade.**
- **RN03 — Vendas a prazo devem gerar automaticamente uma conta a receber com data de vencimento.**
- **RN04 — O cliente pode ser cadastrado no momento da venda caso não exista no sistema.**
- **RN05 — Medicamentos controlados só podem ser vendidos após validação do farmacêutico.**

---

# 3. Requisitos Funcionais (mínimo: 8)

- **RF01 — Cadastrar novos clientes no sistema.**
- **RF02 - Localizar clientes já registrados na base.**
- **RF03 — Pesquisar produtos por nome, código ou fabricante.**
- **RF04 — Realizar o fechamento de vendas.**
- **RF05 — Validar se há estoque disponível antes de concluir a venda.**
- **RF06 — Dar baixa automática no estoque após a venda.**
- **RF07 — Registrar pagamentos à vista ou à prazo.**
- **RF08 — Lançar vendas a prazo no contas a receber.**
- **RF09 — Emitir o comprovante de venda ao finalizar.**
---

# 4. Requisitos Não Funcionais (mínimo: 4)
- **RNF01 — Eficiência: Operações principais devem ser processadas em até 1 minuto.**
- **RNF02 — Segurança: Acesso permitido apenas mediante autenticação segura.**
- **RNF03 — Confiabilidade: Garantia de funcionamento ininterrupto durante o expediente da farmácia.**
- **RNF04 — Integridade: Armazenamento robusto com foco em prevenção de perda de dados.**
- **RNF05 — Usabilidade: Design intuitivo otimizado para a rotina dos atendentes.**

---

# 5. Casos de Uso (mínimo: 10)
### Diagrama de Casos de Uso Geral

<img width="956" height="682" alt="DIAGRAMAGERAL" src="https://github.com/user-attachments/assets/4d7b0df9-46e1-4fae-b885-b5b067fd88fc" />

---

# 6. Documentação dos Casos de Uso

## UC01 — Realizar Venda

**Ator Principal** Atendente 
**Objetivo** Realizar a venda de produtos para o cliente 
**Pré-condições** Sistema funcionando; Produto cadastrado 
**Pós-condições** Venda registrada; Estoque atualizado 

### Fluxo Principal
1. O atendente inicia a venda
2. O sistema solicita identificação do cliente
3. O atendente seleciona os produtos
4. O sistema verifica o estoque
5. O atendente escolhe a forma de pagamento
6. O sistema finaliza a venda

### Fluxos Alternativos
- **A1 — Estoque insuficiente:** O sistema informa erro e não permite finalizar a venda

### Relacionamentos
**RF Relacionados** RF03 — Realizar venda 
**RNF Relacionados** RNF01 — Performance 
**RN Relacionadas** RN01 — Controle de estoque 

### Diagrama de Atividade - UC01

<img width="304" height="679" alt="UC01_REALIZARVENDA" src="https://github.com/user-attachments/assets/dfb371fe-22ac-4371-906c-4b46e691843e" />


---

## UC02 — Identificar Cliente

**Ator Principal** Atendente 
**Objetivo** Identificar um cliente no sistema 
**Pré-condições** Cliente pode estar cadastrado 
**Pós-condições** Cliente identificado 

### Fluxo Principal
1. O atendente informa os dados
2. O sistema busca o cliente
3. O sistema exibe o resultado

### Fluxos Alternativos
- **A1 — Cliente não encontrado:** O sistema oferece opção de cadastro

### Relacionamentos
**RF Relacionados** RF02 — Identificar cliente 
**RNF Relacionados** RNF02 — Segurança 
**RN Relacionadas** RN04 — Cadastro rápido 

### Diagrama de Atividade - UC02

<img width="282" height="309" alt="Captura de tela 2026-03-25 213753" src="https://github.com/user-attachments/assets/428e0635-616b-4430-8c2f-ad332bec84cd" />

---

## UC03 — Cadastrar Cliente

**Ator Principal** Atendente 
**Objetivo** Cadastrar um novo cliente 
**Pré-condições** Dados obrigatórios disponíveis 
**Pós-condições** Cliente cadastrado no sistema 

### Fluxo Principal
1. Inserir dados do cliente
2. Salvar cliente

### Fluxos Alternativos
- **A1 — Dados inválidos:** Sistema solicita correção

### Relacionamentos
**RF Relacionados** RF01 — Cadastro de cliente 
**RNF Relacionados** RNF04 — Usabilidade 
**RN Relacionadas** RN04 — Cadastro durante venda 

### Diagrama de Atividade - UC03

<img width="144" height="247" alt="UC03_CASDASTRARCLIENTE" src="https://github.com/user-attachments/assets/75976d60-656b-4e36-a6e8-4cad1563f403" />

---

## UC04 — Consultar Produto

**Ator Principal** Atendente 
**Objetivo** Buscar produtos no sistema 
**Pré-condições** Produtos cadastrados 
**Pós-condições** Resultados exibidos 

### Fluxo Principal
1. Inserir nome/código do produto
2. Sistema retorna resultados

### Fluxos Alternativos
- **A1 — Produto não encontrado:** Sistema exibe mensagem de "nenhum produto encontrado"

### Relacionamentos
**RF Relacionados** RF03 — Consulta de produtos 
**RNF Relacionados** RNF01 — Performance 

### Diagrama de Atividade - UC04

<img width="195" height="247" alt="UC04_CONSULTARPRODUTO" src="https://github.com/user-attachments/assets/bd859ff4-65a5-41d2-8716-08fdcbc69c61" />

---

## UC05 — Verificar Estoque

**Ator Principal** Sistema 
**Objetivo** Verificar disponibilidade de produtos 
**Pré-condições** Produto selecionado 
**Pós-condições** Status do estoque retornado 

### Fluxo Principal
1. Consultar quantidade em estoque
2. Retornar status de disponibilidade

### Fluxos Alternativos
- **A1 — Sem estoque disponível:** Sistema notifica indisponibilidade

### Relacionamentos
**RF Relacionados** RF04 — Verificação de estoque 
**RN Relacionadas** RN01 — Controle de estoque 

### Diagrama de Atividade - UC05

<img width="430" height="256" alt="UC05_VERIFICARESTOQUE" src="https://github.com/user-attachments/assets/a9133fa6-d74d-495a-b493-7a5847e2f3b2" />

---

## UC06 — Registrar Pagamento

**Ator Principal** Atendente 
**Objetivo** Registrar forma de pagamento da venda 
**Pré-condições** Venda iniciada 
**Pós-condições** Pagamento registrado 

### Fluxo Principal
1. Escolher forma de pagamento
2. Confirmar pagamento

### Fluxos Alternativos
- **A1 — Pagamento a prazo:** Gerar conta a receber automaticamente

### Relacionamentos
**RF Relacionados** RF07 — Registro de pagamento 
**RN Relacionadas** RN03 — Venda a prazo 

### Diagrama de Atividade - UC06

<img width="302" height="366" alt="UC06_REGISTRARPAGAMENTO" src="https://github.com/user-attachments/assets/299ca56f-feaa-44b8-a14d-3b5a2b4403ee" />

---

## UC07 — Gerar Comprovante

**Ator Principal** Atendente 
**Objetivo** Emitir comprovante da venda 
**Pré-condições** Venda finalizada 
**Pós-condições** Comprovante emitido 

### Fluxo Principal
1. Gerar comprovante com dados da venda
2. Exibir ou imprimir

### Relacionamentos
**RF Relacionados** RF08 — Emissão de comprovante 

### Diagrama de Atividade - UC07

<img width="144" height="192" alt="UC07_GERARCOMPROVANTE" src="https://github.com/user-attachments/assets/bd632e2b-e848-41f7-b3cd-dc55280029d8" />

---

## UC08 — Registrar Venda a Prazo

**Ator Principal** Atendente 
**Objetivo** Registrar venda com pagamento futuro 
**Pré-condições** Cliente identificado e aprovado para crédito 
**Pós-condições** Venda a prazo registrada 

### Fluxo Principal
1. Escolher prazo de vencimento
2. Definir data de vencimento
3. Confirmar venda a prazo

### Relacionamentos
**RN Relacionadas** RN03 — Venda a prazo 

### Diagrama de Atividade - UC08

<img width="208" height="247" alt="UC08_REGISTRARVENDAAPRAZO" src="https://github.com/user-attachments/assets/e7e6f141-a24d-451a-b957-03bf90ff96a9" />

---

## UC09 — Gerar Conta a Receber

**Ator Principal** Sistema 
**Objetivo** Criar registro financeiro de venda a prazo 
**Pré-condições** Venda a prazo registrada 
**Pós-condições** Conta lançada no financeiro 

### Fluxo Principal
1. Criar registro de conta
2. Definir valor da venda
3. Definir data de vencimento

### Relacionamentos
**RN Relacionadas** RN03 — Controle financeiro 

### Diagrama de Atividade - UC09

<img width="141" height="302" alt="UC09_GERARCONTAARECEBER" src="https://github.com/user-attachments/assets/436190c3-8027-44b7-907e-721d0e60a9cf" />

---

## UC10 — Validar Receita

**Ator Principal** Farmacêutico 
**Objetivo** Validar venda de medicamentos controlados 
**Pré-condições** Receita apresentada pelo cliente 
**Pós-condições** Receta validada ou rejeitada 

### Fluxo Principal
1. Receber receita do cliente
2. Validar receita
3. Autorizar ou bloquear venda

### Fluxos Alternativos
- **A1 — Receita inválida:** Venda é bloqueada

### Relacionamentos
**RN Relacionadas** RN05 — Medicamentos controlados 

### Diagrama de Atividade - UC10

<img width="249" height="256" alt="UC10_VALIDARRECEITA" src="https://github.com/user-attachments/assets/229dcc5b-0876-49d8-8772-490b50e739bc" />

---

