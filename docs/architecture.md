# Arquitetura da Aplicação: Sorteio Solidário

## 1. Visão Geral

Este documento descreve a arquitetura full-stack para o projeto **Sorteio Solidário**. A solução é composta por duas aplicações principais e desacopladas que se comunicam via API:

1.  **Backend (API e Painel Administrativo):** Desenvolvido em **PHP/Laravel**, é responsável por toda a lógica de negócio, gerenciamento de dados e pelo painel de controle administrativo.
2.  **Frontend (Interface Pública):** Desenvolvido com **Next.js 14**, é responsável pela experiência do usuário público, incluindo a landing page, visualização de sorteios e o fluxo de compra.

## 2. Arquitetura do Backend (Laravel)

O backend é o núcleo do sistema, construído em **PHP/Laravel**.

### 2.1. Repositório Base
O desenvolvimento do backend partirá do seguinte template, que já estabelece a estrutura organizacional e as configurações iniciais:
* **Link:** [https://github.com/brediweb/controle-template.git](https://github.com/brediweb/controle-template.git)

### 2.2. Padrão de Arquitetura
A aplicação seguirá um padrão em camadas (Controllers, Services, Repositories) para garantir uma clara separação de responsabilidades.

### 2.3. Painel Administrativo (Laravel Blade)
O painel para gerenciar as campanhas será renderizado diretamente pelo Laravel, utilizando o motor de templates **Blade**. As rotas sob o prefixo `/admin` serão responsáveis por exibir e processar os formulários de CRUD (Criar, Ler, Atualizar, Desativar) dos sorteios.

### 2.4. Definição da API (Rotas para o Frontend)
As seguintes rotas de API JSON serão expostas para o consumo do frontend Next.js:

* `GET /api/sorteios`
* `GET /api/sorteio/{slug}`
* `POST /api/sorteio/{slug}/comprar`
* `POST /api/webhooks/pagseguro`

## 3. Arquitetura do Frontend (Next.js)

O frontend é baseado no boilerplate **Next.js 14 com shadcn/ui e Swiper** fornecido.

### 3.1. Repositório Base
O desenvolvimento do frontend partirá do seguinte template, que já inclui o stack tecnológico e os padrões de implementação:
* **Link:** [https://github.com/angeloricardoweb/boilerplate-next14-api-base](https://github.com/angeloricardoweb/boilerplate-next14-api-base)

### 3.2. Stack de Tecnologia
O stack tecnológico está definido pelo boilerplate e inclui **Next.js 14, TypeScript, Tailwind CSS, shadcn/ui, Axios, React Hook Form e Zod**.

### 3.3. Estrutura de Pastas
A estrutura seguirá o padrão do **App Router** do Next.js, conforme o boilerplate. As páginas públicas (`/`, `/sorteio/[slug]`, `/parabens`) serão criadas dentro de `src/app/`.

### 3.4. Padrões de Implementação
O desenvolvimento seguirá os padrões já estabelecidos no boilerplate, como o uso da função `cn` para classes, os utilitários de cookies e a instância do Axios para comunicação com a API.

## 4. Integração Full-Stack

* **Comunicação:** O frontend Next.js atua como um consumidor da API pública fornecida pelo backend Laravel.
* **Configuração:** A URL da API do Laravel será uma variável de ambiente no projeto Next.js para facilitar a configuração entre os ambientes de desenvolvimento e produção.