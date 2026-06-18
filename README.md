# Fórum de Discussão com Autenticação JWT

API REST de um fórum com autenticação JWT, tópicos, respostas e perfis.

> 📦 **Template de trabalho em grupo da WebForge.** Clique em **Use this template** (botão verde acima) para criar o repositório do seu grupo.

## 🚀 Como rodar

```bash
npm install
npm start        # inicia em http://localhost:3002
```

O projeto já sobe com uma rota raiz `GET /`. Todo o resto é com o grupo.

## 📋 Requisitos

- **Autenticação** — `POST /auth/registro` (senha com hash bcrypt) e `POST /auth/login` (retorna JWT válido por 24h); middleware que valida `Authorization: Bearer <token>`.
- **Tópicos** — `POST /topicos` (auth), `GET /topicos` com paginação e busca por título, `GET /topicos/:id`, `DELETE /topicos/:id` (somente o criador).
- **Respostas** — `POST /topicos/:id/respostas` (auth), `GET /topicos/:id/respostas`, `DELETE /respostas/:id` (somente o autor).
- **Perfil** — `GET /perfil`, `PATCH /perfil` e listagem de tópicos/respostas por usuário.

> Persistam os dados (arquivo JSON ou SQLite) — os testes podem reiniciar o servidor entre etapas.

## ✅ O que os testes de correção validam

Os testes automáticos sobem o **seu** servidor e fazem requisições HTTP reais contra a API. Eles verificam **comportamento** (status HTTP e corpo das respostas), não a estrutura interna do código — organizem os arquivos como preferirem. Para ser aprovado, a API precisa:

- [ ] `GET /` responde **200**.
- [ ] `POST /auth/registro` cria o usuário (**201**) e **não** retorna a senha no corpo.
- [ ] `POST /auth/login` com credenciais válidas retorna um **token JWT**.
- [ ] Acessar uma rota protegida **sem token** responde **401**.
- [ ] `POST /topicos` com token válido cria o tópico (**201**).
- [ ] `GET /topicos?page=1&limit=10` retorna resultados paginados.
- [ ] `DELETE /topicos/:id` por quem **não** é o criador responde **403**.
- [ ] `POST /topicos/:id/respostas` adiciona resposta vinculada ao tópico.
- [ ] Senha é armazenada com hash (nunca em texto plano).

## 👥 Trabalho em equipe (obrigatório)

Este é um ambiente o mais próximo possível do mercado:

- O repositório deve pertencer a **um** dos membros do grupo. Os **demais membros entram como colaboradores** em `Settings → Collaborators → Add people`.
- Cada membro trabalha em sua **própria branch** e abre **Pull Request** para a `main`, pedindo revisão de outro colega.
- A WebForge mede as **contribuições individuais** de cada membro (commits, linhas adicionadas e removidas) direto do histórico do GitHub. Distribuam bem o trabalho.

## 🧱 Stack

- Node.js + Express (CommonJS)
