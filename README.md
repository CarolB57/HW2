
### Homework 2: Implementando e Estendendo a Aplicação RottenPotatoes

**Aluna:** Caroline Bohadana Rodrigues Viana

**Matrícula:** 232050975

A aplicação foi construída com o uso do framework **Ruby (3.4.6) on Rails (8.0.2.1)**, seguindo as orientações apresentadas no livro Engineering Software as a Service: An Agile Approach Using Cloud Computing Second Edition, de Armando Fox and David Patterson, capítulo 4: SaaS Framework: Rails as a Model–View–Controller Framework, e seguindo o padrão de arquitetura **Model-View-Controller (MVC)**. O objetivo é criar uma página web capaz de listar filmes de um banco de dados e permitir que o usuário os liste por título ou data de lançamento.

---
### Desenvolvimento da Aplicação

1. **Configuração do Model (Dados):**
    - O Model `Movie` foi criado para representar os filmes no banco de dados.
    - Uma **migration** (migração) foi executada para criar a tabela `movies` no banco de dados, definindo as colunas: `title`, `rating`, `description` e `release_date`.
    - O banco de dados foi populado com dados iniciais através do arquivo `seeds.rb`, o qual cadastrou quatro filmes de exemplo.
    
2. **Definição das Rotas (URLs):** No arquivo `config/routes.rb`, uma única linha (`resources :movies`) foi usada para gerar automaticamente todas as URLs necessárias para listar, ver, criar, editar e apagar filmes, seguindo as convenções RESTful.

3. **Implementação do Controller (Lógica):**
	- O `MoviesController` foi criado para gerenciar as requisições dos usuários.
	- O método `index` foi implementado para buscar os filmes do banco de dados. Ele foi aprimorado para receber um parâmetro da URL (`params[:sort]`) e usar o método `.order` do ActiveRecord para ordenar a lista de filmes de acordo com o critério escolhido (título ou data de lançamento).
	- O controller passa a lista de filmes (`@movies`) e a informação da coluna ordenada (`@coluna_ordenada`) para a View.

4. **Desenvolvimento da View (Visualização):**
	- O arquivo `index.html.erb` foi criado para exibir a lista de filmes.
	- Com o uso do **ERB (Embedded Ruby)**, o loop (`<% @movies.each do |movie| %>`) percorre a lista de filmes e exibe os dados de cada um em uma linha.
	- Nos cabeçalhos da tabela, foram adicionados links (`link_to`) que, ao serem clicados, recarregam a página com os parâmetros de ordenação na URL (ex: `?sort=title`).
	- Uma lógica condicional (`if/else`) foi implementada para adicionar uma classe CSS `.sorted` dinamicamente ao cabeçalho da coluna que está atualmente ordenada, permitindo o destaque visual.

---
### Instalação e Execução da Aplicação

**Pré-requisitos:**
- Git
- Ruby
- Bundler (`gem install bundler`)
- Ruby on Rails (`gem install rails`)

1. **Clonar o Repositório:** execute o comando abaixo no terminal para baixar o código do GitHub:
```bash
git clone https://github.com/CarolB57/HW2.git
```

2. **Entrar no Diretório do Projeto:**
```bash
cd HW2
```

3. **Instalar as Dependências:** o Bundler irá ler o arquivo `Gemfile` e instalar todas as bibliotecas (gems) que o projeto necessita.
```bash
bundle install
```

4. **Configurar o Banco de Dados:** os  dois comandos a seguir irão criar o banco de dados, executar a migration para criar a tabela `movies` e, em seguida, popular a tabela com os dados iniciais.
```bash
rake db:migrate
rake db:seed
```

5. **Iniciar o Servidor:** o comando abaixo inicia o servidor web local do Rails.
```bash
rails server
```

6. **Acessar a Aplicação:** no navegador, entre no link abaixo:
```bash
http://localhost:3000/movies
```
