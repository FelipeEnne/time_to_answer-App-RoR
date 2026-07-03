# Time to Answer

Aplicação web em Ruby on Rails com página inicial de boas-vindas (`Welcome#index`). O projeto foi atualizado para uma stack suportada, eliminando dependências com vulnerabilidades conhecidas (CVEs).

## Stack

| Componente | Versão |
|---|---|
| Ruby | 3.4.9 |
| Rails | 8.0.x |
| Banco de dados | SQLite3 |
| Servidor | Puma |
| Assets | Propshaft + Importmap (Turbo / Stimulus) |

## Requisitos

- Ruby 3.4.9 (ou compatível com a versão em `.ruby-version`)
- Bundler
- SQLite3

No Windows, com RubyInstaller em `C:\Ruby34-x64`, garanta que `C:\Ruby34-x64\bin` esteja no `PATH`.

## Setup

```bash
bundle install
bin/rails db:prepare
bin/rails server
```

Acesse [http://localhost:3000](http://localhost:3000) (rota raiz) ou `/welcome/index`.

Alternativa com o script de setup (instala gems, prepara o banco e sobe o servidor):

```bash
bin/setup
```

## Testes

```bash
bin/rails test
```

## Segurança

As dependências Ruby foram atualizadas de Rails 5.2 / Ruby 2.6 (EOL) para Rails 8 / Ruby 3.4. A auditoria de gems não reporta vulnerabilidades conhecidas:

```bash
bundle exec bundle-audit check --update
```

Em desenvolvimento e teste, o Rails gera automaticamente a `secret_key_base` local. Em produção, defina `SECRET_KEY_BASE` no ambiente ou gere credenciais com:

```bash
bin/rails credentials:edit
```

## Estrutura relevante

- `app/controllers/welcome_controller.rb` — página inicial
- `config/routes.rb` — `root` aponta para `welcome#index`
- `Gemfile` / `Gemfile.lock` — dependências e versões travadas
