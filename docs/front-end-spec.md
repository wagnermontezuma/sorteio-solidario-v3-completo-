`*agent ux-expert`

Olá\! Sally aqui. Com certeza. A nova regra de negócio para a apuração do sorteio é uma excelente adição para garantir a transparência.

Essa regra impacta principalmente o backend, mas é importante que a documentação de frontend reflita o contexto completo do projeto. Atualizei a **Especificação de UI/UX** (`front-end-spec.md`) com a nova regra mencionada na seção de "Regras", para que o documento fique completo e consistente com o PRD.

Aqui está a versão final e atualizada do documento.

-----

````markdown
# Especificação de UI/UX: Sorteio Solidário

## 1. Objetivos e Princípios Gerais de UX

### Personas
* **Participante (Comprador):** Busca uma maneira rápida e segura de participar de um sorteio e apoiar uma causa.
* **Administrador:** Usuário interno que necessita de uma interface funcional para gerenciar campanhas.

### Princípios de Design
1.  **Simplicidade Acima de Tudo:** Foco no "feijão com arroz" para garantir clareza e facilidade de uso.
2.  **Consistência Visual:** Manter um padrão visual coeso em todas as telas públicas.
3.  **Foco no Mobile:** O design deve ser pensado primeiramente para dispositivos móveis.

## 2. Arquitetura da Informação (IA)

### Mapa do Site (Páginas Públicas do Frontend)

```mermaid
graph TD
    A[Landing Page] --> B{Sorteio Ativo};
    B --> C[Página do Sorteio];
    C -- Compra --> D[Página de Confirmação];
````

## 3\. Fluxos de Usuário

### Fluxo Principal: Compra de Cupom

  * **Objetivo do Usuário:** Adquirir um ou mais cupons para um sorteio específico de forma rápida e segura.
  * **Ponto de Entrada:** O usuário inicia o fluxo na `Página do Sorteio`.
  * **Critério de Sucesso:** O usuário finaliza o pagamento, visualiza seus números na tela de confirmação e os recebe por e-mail.

### Diagrama do Fluxo

```mermaid
graph TD
    A[Início: Página do Sorteio] --> B[Usuário seleciona a quantidade de cupons];
    B --> C[Preenche o formulário: Nome, E-mail, Telefone];
    C --> D{Escolhe a forma de pagamento};
    D --> E[PIX];
    D --> F[Cartão de Crédito];
    E --> G[Clica em 'Participar'];
    F --> G;
    G --> H[Sistema exibe QR Code ou formulário do PagSeguro];
    H --> I{Pagamento Aprovado?};
    I -- Sim --> J[Sistema gera os números e envia o e-mail];
    J --> K[Fim: Exibe Página de Confirmação com os números];
    I -- Não --> L[Exibe mensagem de erro];
    L --> C;

    style K fill:#D5F5E3
    style L fill:#FADBD8
```

## 4\. Layout das Páginas e Regras

### 4.1. Landing Page

  * **Propósito:** Apresentar a iniciativa **Sorteio Solidário** e conduzir o usuário para os sorteios ativos.
  * **Estrutura:**
      * **Área de Destaque (Hero):** Título, subtítulo sobre a causa e um botão de ação "Ver Sorteios Ativos".
      * **Lista de Sorteios Ativos:** Título da seção e um grid de cards com os sorteios em andamento.
      * **Rodapé Informativo:** Informações sobre o instituto.

### 4.2. Página do Sorteio

  * **Propósito:** Exibir os detalhes de um sorteio e permitir a compra.
  * **Estrutura:**
      * Galeria de imagens do prêmio.
      * Bloco de informações: Título, Descrição, e uma seção de **Regras** que incluirá a **Regra de Aproximação do Ganhador**.
      * **Área de Compra (Destaque):** Formulário de compra.

### 4.3. Página de Confirmação

  * **Propósito:** Confirmar o sucesso da compra e entregar os números da sorte.
  * **Estrutura:**
      * Mensagem de sucesso (ex: "Parabéns\!").
      * Lista clara dos números adquiridos.
      * Botão para retornar à página inicial.

## 5\. Componentes e Branding

  * **Biblioteca de Componentes:** Utilizaremos **shadcn/ui**, conforme definido pelo boilerplate.
  * **Branding:** Um guia de estilo provisório será usado até o recebimento da identidade visual oficial.

<!-- end list -->

```

---
Documento `front-end-spec.md` atualizado com sucesso.

Agora que o PRD e a Especificação de UI/UX estão alinhados, você gostaria que eu gerasse o `architecture.md` final e atualizado?
```