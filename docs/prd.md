# Sorteio Solidário - Product Requirements Document (PRD) v2

## 1. Metas e Contexto

### 1.1. Metas

* **Agilidade no Lançamento:** Lançar a primeira versão funcional (MVP) da plataforma no menor tempo possível.
* **Experiência do Usuário Simplificada:** Garantir um processo de compra de cupons rápido e intuitivo, sem a necessidade de cadastro complexo.
* **Transparência e Confiança:** Assegurar que os participantes confiem no processo, com confirmações claras e resultados de sorteios vinculados à Loteria Federal.

### 1.2. Contexto

O instituto necessita de uma ferramenta digital para organizar campanhas de arrecadação de fundos, superando os desafios de alcance e logística dos métodos tradicionais. A plataforma **Sorteio Solidário** automatizará a venda de cupons, o controle de pagamentos e a divulgação dos resultados, criando um processo centralizado, eficiente e transparente.

### 1.3. Histórico de Alterações

| Data | Versão | Descrição | Autor |
| :--- | :--- | :--- | :--- |
| 25/09/2025 | 1.1 | Adicionada Regra de Negócio para apuração do sorteio. | John (PM) |
| 24/09/2025 | 1.0 | Geração final do documento para o MVP | John (PM) |

## 2. Requisitos

### 2.1. Funcionais

* **FR1:** Administradores devem poder criar e gerenciar sorteios através de um painel de controle renderizado pelo backend (Laravel).
* **FR2:** Sorteios ativos devem ser publicamente visíveis em páginas individuais servidas por uma aplicação frontend (Next.js).
* **FR3:** Participantes devem poder comprar cupons através de um formulário simplificado, sem necessidade de login.
* **FR4:** O sistema deve integrar com o PagSeguro para processar transações de Pix e Cartão de Crédito.
* **FR5:** O sistema deve gerar números de cupom únicos e aleatórios automaticamente após a confirmação do pagamento.
* **FR6:** Participantes devem receber a confirmação da compra e seus números por e-mail.
* **FR7:** O resultado do sorteio, baseado na Loteria Federal, deve ser registrado no painel e exibido na página do sorteio.

### 2.2. Não-Funcionais

* **NFR1:** A aplicação frontend deve ser responsiva, funcionando em desktops e dispositivos móveis.
* **NFR2:** As transações de pagamento devem ser seguras, utilizando a infraestrutura do gateway de pagamento.
* **NFR3:** A interface deve evitar o uso explícito do termo "rifa".
* **NFR4:** Os dados do participante devem ser reaproveitados via cookies para melhorar a experiência em compras futuras.

### 2.3. Regras de Negócio do Sorteio

* **RN1: Geração de Números:** A geração dos números da sorte para os participantes se dará de forma aleatória no momento da confirmação da compra.
* **RN2: Regra de Aproximação do Ganhador:** Se o número sorteado pela Loteria Federal não tiver sido distribuído a nenhum participante, o ganhador será determinado pela seguinte regra de aproximação:
    1.  Busca-se o número participante imediatamente **superior** (ordem crescente).
    2.  Se nenhum for encontrado até o final da série, busca-se o número participante imediatamente **inferior** (ordem decrescente) a partir do número sorteado originalmente.
    3.  Este processo se repete até que um participante válido seja encontrado.

## 3. Épicos e Histórias de Usuário

### Épico 1: Estrutura Fundamental e Primeira Campanha

**Objetivo do Épico:** Estabelecer a base da plataforma, permitindo que um administrador crie e publique um sorteio através do painel Laravel, e que um participante possa visualizar este sorteio no frontend Next.js, comprar um cupom e receber a confirmação.

---

#### História 1.1: Cadastro de Sorteio no Painel Laravel
* **Como** administrador,
* **Eu quero** acessar um painel de controle para cadastrar um novo sorteio com título, descrição, prêmio e regras,
* **Para que** eu possa disponibilizar uma nova campanha de arrecadação.

---

#### História 1.2: Visualização Pública do Sorteio no Frontend
* **Como** participante,
* **Eu quero** acessar uma página pública e única (gerada pelo Next.js) para cada sorteio,
* **Para que** eu possa ver os detalhes do prêmio e as regras antes de decidir participar.

---

#### História 1.3: Fluxo de Compra Simplificado no Frontend
* **Como** participante,
* **Eu quero** preencher um formulário simples com meus dados e efetuar o pagamento via PagSeguro,
* **Para que** o processo de compra seja rápido e sem atritos.

---

#### História 1.4: Confirmação e Recebimento dos Números
* **Como** participante,
* **Eu quero** receber meus números por e-mail e ver uma tela de confirmação após o pagamento ser aprovado,
* **Para que** eu tenha a certeza de que minha participação foi registrada.

## 4. Próximos Passos

Este documento deve ser usado como guia para a criação da Especificação de UI/UX e do Documento de Arquitetura.