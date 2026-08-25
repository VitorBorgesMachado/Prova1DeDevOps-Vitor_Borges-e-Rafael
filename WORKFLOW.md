# WORKFLOW

## 1. Modelo utilizado

O projeto utiliza uma versão simplificada do **GitHub Flow**.

A `main` é a branch principal do projeto. As funcionalidades são
desenvolvidas em branches separadas e depois integradas na `main`
por meio de `merge`.

Fluxo:

```text
main
 ↓
feature/nome-da-funcionalidade
 ↓
revisão
 ↓
merge
 ↓
main
```

---

## 2. Branches

As branches de funcionalidades seguem o padrão:

```text
feature/nome-da-funcionalidade
```

Branches utilizadas no projeto:

| Branch | Função |
|---|---|
| `main` | Branch principal |
| `feature/base` | Estrutura inicial do site |
| `feature/metas` | Página de metas |
| `feature/historico` | Página de histórico |
| `feature/insights` | Página de insights |

As branches de funcionalidade são criadas a partir da `main` e depois
integradas novamente nela.

Para criar uma branch:

```bash
git checkout main
git pull origin main
git checkout -b feature/metas
```

---

## 3. Atualização das branches

Antes de começar uma nova funcionalidade, a `main` deve ser atualizada:

```bash
git checkout main
git pull origin main
```

Antes de fazer o merge, a branch de trabalho deve ser atualizada com
as alterações da `main`:

```bash
git checkout feature/metas
git fetch origin
git merge origin/main
```

Se houver conflitos, eles devem ser resolvidos antes do merge.

---

## 4. Integração

A equipe não utiliza Pull Requests.

Depois de terminar uma funcionalidade, a branch é comparada com a
`main` e depois integrada por meio de `merge`.

Exemplo:

```bash
git checkout main
git pull origin main
git merge feature/metas
git push origin main
```

---

## 5. Revisão das alterações

Antes do merge, podemos verificar as alterações da branch utilizando:

```bash
git diff main..feature/metas
```

Para ver apenas os arquivos modificados:

```bash
git diff --name-only main..feature/metas
```

Para ver os commits:

```bash
git log main..feature/metas --oneline
```

A revisão serve para verificar se as alterações estão corretas e se
não existem conflitos ou problemas no código.

---

## 6. Commits

Os commits seguem o padrão:

```text
tipo(escopo): descrição
```

Exemplos:

```text
feat(metas): adiciona pagina de metas
fix(metas): corrige barra de progresso
docs: atualiza README
```

A mensagem deve ser curta e explicar o que foi alterado.

---

## 7. Tipos de commit

| Tipo | Quando usar |
|---|---|
| `feat` | Nova funcionalidade |
| `fix` | Correção de erro |
| `docs` | Alteração na documentação |
| `refactor` | Organização do código sem mudar seu funcionamento |
| `test` | Criação ou alteração de testes |
| `style` | Alteração de formatação do código |
| `chore` | Tarefas de manutenção |
| `build` | Alterações na construção do projeto |
| `ci` | Alterações na integração contínua |
| `perf` | Melhorias de desempenho |

### Tipos criados pela equipe

Além dos tipos anteriores, foram definidos três tipos para o projeto:

### `ui`

Usado para alterações na parte visual do site.

Exemplo:

```text
ui(metas): ajusta estilo dos cards
```

### `data`

Usado para alterações relacionadas aos dados do sistema.

Exemplo:

```text
data(historico): adiciona registros de estudo
```

### `content`

Usado para alterações nos textos e conteúdos apresentados nas páginas.

Exemplo:

```text
content(insights): atualiza textos dos indicadores
```

---

## 8. Conflitos

Quando ocorrer um conflito durante o `merge`, os arquivos devem ser
analisados e as alterações corretas devem ser mantidas.

Depois de resolver:

```bash
git add .
git commit -m "fix: resolve conflito de integracao"
```

---

## 9. Reverter alterações

Para desfazer um commit sem apagar o histórico, utilizamos:

```bash
git revert HEAD
```

Isso cria um novo commit desfazendo a alteração anterior.

---

## 10. Organização do projeto

Os arquivos devem ficar organizados de acordo com sua função.

```text
projeto/
│
├── index.html
├── style.css
├── README.md
├── WORKFLOW.md
├── .gitignore
│
└── img/
    └── estudos/
```

---

## 11. Referências

- [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow)
- [Git](https://git-scm.com/)
- [Conventional Commits](https://www.conventionalcommits.org/)

---

## 12. Resumo

```text
Atualizar main
      ↓
Criar feature
      ↓
Desenvolver
      ↓
Fazer commits
      ↓
Revisar alterações
      ↓
Resolver conflitos
      ↓
Merge na main
      ↓
Push para o GitHub
```