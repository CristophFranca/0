# 🌿 Curso Completo de Git e GitHub

> **Do zero ao avançado** — aprenda a versionar seus projetos com **Git** e colaborar com o mundo pelo **GitHub**. Com diagramas visuais, fluxos de trabalho reais e boas práticas usadas em times profissionais.

> 💡 **Como usar este curso:** Todos os comandos podem ser executados no terminal (Linux/Mac) ou Git Bash (Windows). Pratique cada módulo em um repositório de teste — não tenha medo de errar, o Git quase sempre permite desfazer!

---

## 📋 Índice

1. [O que é Git? O que é GitHub?](#-o-que-é-git-o-que-é-github)
2. [Instalação e Configuração](#-instalação-e-configuração)
3. [Módulo 1 — Conceitos Fundamentais](#módulo-1--conceitos-fundamentais)
4. [Módulo 2 — Primeiros Passos (Repositório Local)](#módulo-2--primeiros-passos-repositório-local)
5. [Módulo 3 — Commits](#módulo-3--commits)
6. [Módulo 4 — Branches](#módulo-4--branches)
7. [Módulo 5 — Merge e Rebase](#módulo-5--merge-e-rebase)
8. [Módulo 6 — Resolvendo Conflitos](#módulo-6--resolvendo-conflitos)
9. [Módulo 7 — Repositórios Remotos e GitHub](#módulo-7--repositórios-remotos-e-github)
10. [Módulo 8 — Colaboração no GitHub](#módulo-8--colaboração-no-github)
11. [Módulo 9 — Desfazendo Coisas](#módulo-9--desfazendo-coisas)
12. [Módulo 10 — Stash, Tags e Cherry-pick](#módulo-10--stash-tags-e-cherry-pick)
13. [Módulo 11 — GitHub Actions (CI/CD)](#módulo-11--github-actions-cicd)
14. [Módulo 12 — Fluxos de Trabalho Profissionais](#módulo-12--fluxos-de-trabalho-profissionais)
15. [Módulo 13 — Boas Práticas](#módulo-13--boas-práticas)
16. [Cheatsheet Git](#-cheatsheet-git)
17. [Exercícios Práticos](#-exercícios-práticos)

---

## 🤔 O que é Git? O que é GitHub?

São coisas diferentes, mas que trabalham juntas:

```
┌─────────────────────────────────────────────────────────────┐
│  GIT                          GITHUB                        │
│  ─────────────────────        ──────────────────────────    │
│  Software instalado           Site / plataforma online      │
│  no seu computador            na nuvem                      │
│                                                             │
│  Controla versões             Hospeda repositórios Git      │
│  dos seus arquivos            na internet                   │
│                                                             │
│  Funciona offline             Permite colaboração           │
│  no terminal                  entre times                   │
│                                                             │
│  Criado por                   Fundado em 2008,              │
│  Linus Torvalds (2005)        comprado pela Microsoft       │
└─────────────────────────────────────────────────────────────┘
```

### Analogia: Fotografias do seu Projeto

Pense no Git como um fotógrafo do seu código:

- Cada **commit** é uma fotografia do estado do projeto naquele momento
- Você pode voltar para qualquer fotografia antiga a qualquer hora
- Múltiplas **branches** são como linhas do tempo paralelas do mesmo projeto
- O **GitHub** é o álbum de fotos online que você compartilha com o time

### Por que usar Git?

| Sem Git | Com Git |
|---|---|
| `projeto-final.zip` | Histórico completo de cada mudança |
| `projeto-final-v2.zip` | Sabe quem mudou o quê e quando |
| `projeto-final-AGORA-VAI.zip` | Volta para qualquer versão anterior |
| `projeto-final-cópia(3).zip` | Trabalha em paralelo sem conflito |
| Perdeu o arquivo... | Nunca perde nada |

---

## 🛠️ Instalação e Configuração

### Instalação

```bash
# Ubuntu / Debian
sudo apt install git

# Fedora / RHEL
sudo dnf install git

# macOS (com Homebrew)
brew install git

# Windows
# Baixe o Git Bash em: https://git-scm.com/download/win
```

Verificar se está instalado:
```bash
git --version
# git version 2.43.0
```

---

### Configuração Inicial (obrigatório!)

Antes de usar, diga ao Git quem você é. Essa informação aparece em todos os seus commits:

```bash
# Seu nome (aparece nos commits)
git config --global user.name "Seu Nome"

# Seu e-mail (use o mesmo do GitHub!)
git config --global user.email "seu@email.com"

# Editor padrão para mensagens de commit
git config --global core.editor "code --wait"    # VS Code
git config --global core.editor "nano"           # Nano (simples)
git config --global core.editor "vim"            # Vim

# Nome padrão da branch principal
git config --global init.defaultBranch main

# Ativar cores no terminal
git config --global color.ui auto
```

Verificar configurações:
```bash
git config --list                 # todas as configurações
git config --global --list        # só as globais
git config user.name              # verificar um valor específico
```

As configurações ficam salvas em `~/.gitconfig`:
```
[user]
    name = Seu Nome
    email = seu@email.com
[core]
    editor = code --wait
[init]
    defaultBranch = main
```

---

## Módulo 1 — Conceitos Fundamentais

### As 3 Áreas do Git

Entender essas 3 áreas é a chave para entender o Git:

```
┌─────────────────────────────────────────────────────────────┐
│                    SEU COMPUTADOR                           │
│                                                             │
│  ┌──────────────┐   git add   ┌──────────────┐             │
│  │   WORKING    │ ──────────► │   STAGING    │             │
│  │   DIRECTORY  │             │   AREA       │             │
│  │              │ ◄────────── │  (Index)     │             │
│  │  Seus        │  git restore│              │             │
│  │  arquivos    │             │  Arquivos    │             │
│  │  editados    │             │  prontos     │             │
│  └──────────────┘             │  para commit │             │
│                               └──────┬───────┘             │
│                                      │ git commit          │
│                                      ▼                     │
│                               ┌──────────────┐             │
│                               │  REPOSITORY  │             │
│                               │  (Local)     │             │
│                               │              │             │
│                               │  Histórico   │             │
│                               │  de commits  │             │
│                               └──────────────┘             │
└─────────────────────────────────────────────────────────────┘

Working Directory → Staging Area → Repository
     git add →          git commit →
```

| Área | O que é | Analogia |
|---|---|---|
| **Working Directory** | Onde você edita os arquivos | Sua mesa de trabalho |
| **Staging Area** | Arquivos marcados para o próximo commit | Sua caixa de envio |
| **Repository** | Histórico permanente de commits | Arquivo histórico |

---

### Estados dos Arquivos

```
┌──────────┐  git add   ┌──────────┐  git commit  ┌──────────┐
│Untracked │──────────►│ Staged   │─────────────►│Committed │
│(novo)    │            │          │               │          │
└──────────┘            └──────────┘               └──────────┘
                              ▲                        │
                              │     editar             │
                        ┌─────┴────┐ ◄──────────────── ┘
                        │Modified  │
                        │(editado) │
                        └──────────┘

Untracked  → arquivo novo que o Git ainda não conhece
Modified   → arquivo rastreado que foi editado
Staged     → arquivo pronto para ir no próximo commit
Committed  → arquivo salvo no histórico
```

---

### O que é um Commit?

Um commit é um **snapshot** (fotografia) do seu projeto em um momento específico. Cada commit tem:

```
Commit: a3f8c2d
─────────────────────────────────────────
Autor:    Ana Silva <ana@empresa.com>
Data:     2024-11-15 14:30:00
Mensagem: feat: adiciona sistema de login

Parent:   7b2e1a0  ← commit anterior
Tree:     d4c9f81  ← estado dos arquivos
─────────────────────────────────────────
```

Os commits formam uma **cadeia** (grafo dirigido acíclico):

```
A ← B ← C ← D ← E
                 ↑
               HEAD (você está aqui)
```

---

## Módulo 2 — Primeiros Passos (Repositório Local)

### Iniciando um Repositório

```bash
# Criar uma pasta e iniciar um repositório Git nela
mkdir meu-projeto
cd meu-projeto
git init

# Saída: Initialized empty Git repository in /meu-projeto/.git/

# O que foi criado:
ls -la
# .git/  ← pasta oculta com TODO o histórico do Git
```

```bash
# Ou: clonar um repositório existente do GitHub
git clone https://github.com/usuario/repositorio.git

# Clonar em uma pasta com nome diferente
git clone https://github.com/usuario/repositorio.git meu-nome
```

---

### Verificando o Status

```bash
git status
```

Interpretando a saída:

```
On branch main

Changes to be committed:          ← Staging Area (prontos para commit)
  (use "git restore --staged <file>..." to unstage)
        new file:   index.html

Changes not staged for commit:    ← Working Directory (editados, não adicionados)
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes)
        modified:   style.css

Untracked files:                  ← Arquivos novos, Git não conhece ainda
  (use "git add <file>..." to include in what will be committed)
        script.js
```

---

### Adicionando Arquivos ao Stage

```bash
# Adicionar um arquivo específico
git add index.html

# Adicionar múltiplos arquivos
git add index.html style.css script.js

# Adicionar todos os arquivos modificados/novos
git add .

# Adicionar todos os arquivos de um tipo
git add *.js

# Adicionar interativamente (escolhe linha a linha)
git add -p

# Verificar o que está no stage antes de commitar
git status
git diff --staged        # mostra exatamente o que vai entrar no commit
```

---

### O .gitignore — Ignorando Arquivos

O `.gitignore` diz ao Git quais arquivos **nunca** devem ser rastreados:

```bash
# Criar o .gitignore na raiz do projeto
touch .gitignore
```

```gitignore
# .gitignore

# Dependências (nunca versione node_modules!)
node_modules/
vendor/

# Variáveis de ambiente e segredos
.env
.env.local
*.key
*.pem
config/secrets.yml

# Build e compilados
dist/
build/
*.pyc
__pycache__/
*.class

# Logs
*.log
logs/

# Arquivos de sistema
.DS_Store        # macOS
Thumbs.db        # Windows
desktop.ini

# IDEs
.vscode/
.idea/
*.swp
*.swo

# Cobertura de testes
coverage/
.coverage
```

> 💡 Acesse [gitignore.io](https://gitignore.io) para gerar `.gitignore` específico por linguagem/framework.

```bash
# Verificar se um arquivo está sendo ignorado
git check-ignore -v nome-do-arquivo

# Se você já rastreou um arquivo e quer ignorá-lo agora:
git rm --cached nome-do-arquivo    # remove do tracking, mantém o arquivo
echo "nome-do-arquivo" >> .gitignore
git add .gitignore
git commit -m "chore: add file to gitignore"
```

---

## Módulo 3 — Commits

### Fazendo um Commit

```bash
# Commit com mensagem inline (mais comum)
git commit -m "feat: adiciona página de login"

# Commit abrindo o editor configurado (para mensagens longas)
git commit

# Adicionar e commitar arquivos rastreados em um passo
# (não funciona para arquivos novos/untracked!)
git commit -am "fix: corrige bug no formulário"
```

---

### Convención de Mensagens de Commit

A **Conventional Commits** é o padrão mais usado em times profissionais:

```
<tipo>(<escopo opcional>): <descrição curta>

[corpo opcional — explica o porquê da mudança]

[rodapé opcional — breaking changes, issues fechadas]
```

**Tipos principais:**

| Tipo | Quando usar | Exemplo |
|---|---|---|
| `feat` | Nova funcionalidade | `feat: adiciona autenticação OAuth` |
| `fix` | Correção de bug | `fix: corrige cálculo de desconto` |
| `docs` | Documentação | `docs: atualiza README com instalação` |
| `style` | Formatação, sem lógica | `style: aplica prettier no projeto` |
| `refactor` | Refatoração de código | `refactor: extrai lógica de validação` |
| `test` | Testes | `test: adiciona testes de login` |
| `chore` | Tarefas de manutenção | `chore: atualiza dependências` |
| `perf` | Melhoria de performance | `perf: otimiza query de usuários` |
| `ci` | CI/CD | `ci: configura GitHub Actions` |
| `revert` | Reverter commit | `revert: reverte feat de OAuth` |

**Exemplos reais:**
```bash
git commit -m "feat(auth): implementa login com Google"
git commit -m "fix(api): corrige timeout em requisições longas"
git commit -m "docs: adiciona guia de contribuição"
git commit -m "refactor(users): separa lógica em service layer"
```

---

### Vendo o Histórico

```bash
# Log básico
git log

# Log compacto (uma linha por commit) ← mais usado no dia a dia
git log --oneline

# Log com grafo de branches
git log --oneline --graph --all

# Log dos últimos N commits
git log -5

# Log com diff das mudanças
git log -p

# Buscar commits por mensagem
git log --grep="login"

# Buscar commits por autor
git log --author="Ana"

# Commits em um intervalo de datas
git log --after="2024-01-01" --before="2024-12-31"

# Log de um arquivo específico
git log --oneline -- src/login.js

# Formato personalizado
git log --format="%h %an %s" --date=short
```

**Exemplo de saída do `git log --oneline --graph --all`:**
```
* a3f8c2d (HEAD -> main) feat: adiciona página de perfil
* 7b2e1a0 fix: corrige validação de e-mail
| * 4d9c1f2 (feature/carrinho) feat: implementa carrinho de compras
| * 2a8e3b1 feat: adiciona item ao carrinho
|/
* 1c5d7a9 feat: sistema de login
* 0b3f2e8 Initial commit
```

---

### Inspecionando Commits e Mudanças

```bash
# Ver o que mudou no working directory (não staged)
git diff

# Ver o que está no stage (o que vai entrar no próximo commit)
git diff --staged
git diff --cached   # equivalente

# Ver as mudanças de um commit específico
git show a3f8c2d

# Ver as mudanças entre dois commits
git diff 7b2e1a0 a3f8c2d

# Ver quem alterou cada linha de um arquivo
git blame src/login.js

# Ver o conteúdo de um arquivo em uma versão anterior
git show a3f8c2d:src/login.js
```

---

## Módulo 4 — Branches

Branches são **linhas de desenvolvimento paralelas e independentes**. Permitem trabalhar em funcionalidades novas sem afetar o código principal.

### Visualizando Branches

```
main:    A ── B ── C ── D
                        ↑
feature:                E ── F ── G
                                  ↑
                               você está aqui
```

---

### Criando e Alternando Branches

```bash
# Listar branches locais
git branch

# Listar branches locais e remotas
git branch -a

# Criar uma branch
git branch feature/login

# Alternar para uma branch existente
git switch feature/login
git checkout feature/login   # forma antiga, ainda funciona

# Criar E alternar em um comando só ← mais usado
git switch -c feature/login
git checkout -b feature/login   # forma antiga equivalente

# Criar branch a partir de outra branch
git switch -c feature/login main     # cria a partir da main
git switch -c hotfix/bug-123 v1.2.0  # cria a partir de uma tag

# Ver em qual branch você está
git branch        # o * indica a branch atual
git status        # também mostra a branch atual
```

---

### Trabalhando com Branches

```bash
# Fluxo típico de trabalho com branches:

# 1. Atualizar a main antes de criar a branch
git switch main
git pull origin main

# 2. Criar branch para a nova funcionalidade
git switch -c feature/carrinho-compras

# 3. Trabalhar, commitar...
git add .
git commit -m "feat: estrutura inicial do carrinho"
git commit -m "feat: adicionar/remover itens"
git commit -m "feat: calcular total do carrinho"

# 4. Enviar a branch para o GitHub
git push origin feature/carrinho-compras

# 5. Abrir Pull Request no GitHub (interface web)
```

---

### Renomear e Deletar Branches

```bash
# Renomear a branch atual
git branch -m novo-nome

# Renomear qualquer branch
git branch -m nome-antigo novo-nome

# Deletar branch (seguro — só se já foi mergeada)
git branch -d feature/login

# Forçar deleção (cuidado!)
git branch -D feature/login

# Deletar branch remota
git push origin --delete feature/login
git push origin :feature/login   # forma antiga

# Sincronizar branches remotas deletadas
git fetch --prune
git remote prune origin
```

---

## Módulo 5 — Merge e Rebase

### git merge — Unindo Branches

O merge integra o histórico de duas branches, preservando todos os commits originais.

```bash
# Unir feature/login na main:
git switch main
git merge feature/login
```

**Tipos de merge:**

#### Fast-Forward (sem commit de merge)

Ocorre quando a branch principal não teve novos commits desde que a feature foi criada:

```
Antes:
main:    A ── B
                \
feature:         C ── D

Depois (fast-forward):
main:    A ── B ── C ── D
                        ↑
                      HEAD
```

```bash
git merge feature/login        # fast-forward automático se possível
git merge --no-ff feature/login # força criar commit de merge mesmo se ff fosse possível
```

#### 3-Way Merge (com commit de merge)

Ocorre quando ambas as branches tiveram novos commits:

```
Antes:
main:    A ── B ── C
                    \
feature:  A ── B ── D ── E

Depois (3-way merge):
main:    A ── B ── C ──── M
                    \    /
feature:             D ──
                     ↑
              commits da feature
M = commit de merge (une os dois históricos)
```

---

### git rebase — Reescrevendo Histórico

O rebase "move" os commits da sua branch para o topo de outra, criando um histórico **linear e limpo**:

```
Antes:
main:    A ── B ── C
                ↑
feature:         D ── E

Depois do rebase (feature em cima de main):
main:    A ── B ── C
                    \
feature:             D' ── E'
                     (commits reescritos)
```

```bash
# Rebasear feature sobre a main
git switch feature/login
git rebase main

# Rebase interativo — reescrever, juntar ou reordenar commits
git rebase -i HEAD~3     # editar os últimos 3 commits
git rebase -i main       # editar todos os commits da feature
```

**No rebase interativo, você pode:**
```
pick   a3f8c2d feat: adiciona login
pick   7b2e1a0 fix: corrige validação
pick   4d9c1f2 fix: mais uma correção

# Opções:
# pick   = manter o commit
# reword = manter mas editar a mensagem
# squash = juntar com o commit anterior
# fixup  = juntar com o anterior (descarta mensagem)
# drop   = remover o commit completamente
```

---

### Merge vs Rebase — Quando usar cada um?

```
MERGE                           REBASE
─────────────────────────────   ─────────────────────────────
✅ Preserva histórico real       ✅ Histórico linear e limpo
✅ Não reescreve commits         ✅ Facilita leitura do log
✅ Seguro para branches          ✅ Pull Requests mais claros
   compartilhadas
❌ Histórico pode ficar          ❌ Reescreve commits (não use
   "embaralhado"                    em branches públicas!)
❌ Commits de merge extras       ❌ Pode perder contexto de
                                    quando a mudança foi feita
```

> ⚠️ **Regra de ouro:** **Nunca** faça rebase de commits que já foram enviados para o repositório remoto e compartilhados com outras pessoas. O rebase reescreve o histórico e vai causar conflitos para todos.

---

## Módulo 6 — Resolvendo Conflitos

Conflitos acontecem quando duas branches alteram a **mesma linha** do **mesmo arquivo** de formas diferentes.

### Como um Conflito Aparece

Após `git merge` ou `git rebase` com conflito:

```bash
Auto-merging src/login.js
CONFLICT (content): Merge conflict in src/login.js
Automatic merge failed; fix conflicts and then commit the result.
```

O arquivo conflitante ficará assim:

```javascript
// src/login.js

function validarSenha(senha) {
<<<<<<< HEAD
    // Versão da branch main
    return senha.length >= 8;
=======
    // Versão da feature branch
    return senha.length >= 12 && /[A-Z]/.test(senha);
>>>>>>> feature/senha-forte
}
```

**Interpretando os marcadores:**
```
<<<<<<< HEAD           → início do conflito — sua versão (branch atual)
=======                → separador
>>>>>>> feature/login  → fim do conflito — versão que veio do merge
```

---

### Resolvendo o Conflito

```bash
# 1. Ver todos os arquivos com conflito
git status

# 2. Abrir cada arquivo e editar manualmente
# Remova os marcadores (<<<<, ====, >>>>) e deixe o código como deve ficar:

# Resultado após resolver:
# function validarSenha(senha) {
#     return senha.length >= 12 && /[A-Z]/.test(senha);
# }

# 3. Marcar como resolvido
git add src/login.js

# 4. Finalizar o merge
git commit   # abre editor com mensagem pré-preenchida

# Ou, para abortar e voltar ao estado anterior:
git merge --abort
git rebase --abort
```

**Ferramentas visuais para conflitos:**
```bash
# Usar a ferramenta configurada de diff
git mergetool

# Configurar VS Code como ferramenta de merge
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'
```

---

## Módulo 7 — Repositórios Remotos e GitHub

### Conectando ao GitHub

```bash
# Ver os remotos configurados
git remote -v

# Adicionar um remoto (geralmente chamado "origin")
git remote add origin https://github.com/usuario/repositorio.git

# Alterar a URL do remoto
git remote set-url origin https://github.com/usuario/novo-repo.git

# Remover um remoto
git remote remove origin
```

---

### SSH vs HTTPS

Para autenticar com o GitHub, use **SSH** (mais prático no dia a dia):

```bash
# 1. Gerar chave SSH
ssh-keygen -t ed25519 -C "seu@email.com"
# Pressione Enter para aceitar o caminho padrão
# Crie uma senha (opcional mas recomendado)

# 2. Copiar a chave pública
cat ~/.ssh/id_ed25519.pub
# Copie o conteúdo exibido

# 3. Adicionar no GitHub:
# Settings → SSH and GPG keys → New SSH key → Cole e salve

# 4. Testar a conexão
ssh -T git@github.com
# Hi usuario! You've successfully authenticated...

# 5. Usar URL SSH nos repositórios
git remote set-url origin git@github.com:usuario/repositorio.git
```

---

### Push — Enviando para o GitHub

```bash
# Enviar branch atual para o remoto
git push origin main

# Primeira vez: definir upstream (branch padrão de envio)
git push -u origin main
# Depois disso, basta: git push

# Enviar uma branch nova
git push origin feature/login

# Forçar push (CUIDADO! Nunca em branches compartilhadas)
git push --force origin feature/minha-branch
git push --force-with-lease  # versão mais segura do force

# Enviar todas as branches
git push --all origin

# Enviar tags
git push --tags
```

---

### Pull e Fetch — Recebendo do GitHub

```bash
# fetch: baixa as mudanças mas NÃO aplica no seu código
git fetch origin
git fetch --all   # todos os remotos

# pull: fetch + merge automático ← mais usado no dia a dia
git pull origin main

# pull com rebase (evita commits de merge desnecessários)
git pull --rebase origin main

# Configurar pull para sempre usar rebase
git config --global pull.rebase true
```

**A diferença visual:**

```
git fetch:
  Repositório remoto → Histórico local
  (seu working directory NÃO muda)

git pull:
  Repositório remoto → Histórico local → Working Directory
  (equivale a: git fetch + git merge)
```

---

### Criando um Repositório no GitHub

**Pelo site:**
1. Acesse [github.com](https://github.com) e faça login
2. Clique em `+` → `New repository`
3. Escolha nome, descrição, visibilidade
4. Marque "Add a README file" (opcional)
5. Clique em `Create repository`

**Conectando um projeto local ao GitHub:**
```bash
# Se o repositório do GitHub está vazio:
git remote add origin git@github.com:usuario/repo.git
git branch -M main
git push -u origin main

# Se você ainda não tem repositório local:
git clone git@github.com:usuario/repo.git
cd repo
# começar a trabalhar...
```

---

## Módulo 8 — Colaboração no GitHub

### Fork — Contribuindo para Projetos de Outros

**Fork** cria uma cópia do repositório na sua conta GitHub, onde você tem permissão total:

```
Repositório original:  usuario-original/projeto
                                ↓  fork
Seu fork:              seu-usuario/projeto
                                ↓  clone
Sua máquina:           ~/projeto
```

```bash
# 1. No GitHub, clique em "Fork" no repositório original

# 2. Clone o SEU fork
git clone git@github.com:seu-usuario/projeto.git

# 3. Adicione o repositório original como "upstream"
git remote add upstream git@github.com:usuario-original/projeto.git

# 4. Trabalhe na sua branch
git switch -c feature/minha-contribuicao

# 5. Envie para o seu fork
git push origin feature/minha-contribuicao

# 6. Abra um Pull Request no GitHub (do seu fork para o original)

# Mantendo o fork atualizado com o original:
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

---

### Pull Request (PR) — Propondo Mudanças

Um **Pull Request** é uma proposta formal de merging de uma branch na outra.

**Fluxo típico:**
```
1. Cria branch feature/nova-funcionalidade
2. Faz commits na branch
3. Abre PR: feature/nova-funcionalidade → main
4. Time revisa o código (Code Review)
5. Sugere mudanças, você faz mais commits
6. PR aprovado → Merge na main
7. Branch feature é deletada
```

**Boas práticas para PRs:**
- Título claro seguindo Conventional Commits: `feat: adiciona filtro de produtos`
- Descrição explicando **o quê**, **por quê** e **como testar**
- PR pequeno e focado em uma coisa só (mais fácil de revisar)
- Referenciar issues: `Closes #42` ou `Fixes #42`
- Adicionar screenshots/GIFs para mudanças visuais

**Template de PR:**
```markdown
## O que foi feito?
Breve descrição da mudança.

## Por que foi feito?
Contexto e motivação.

## Como testar?
1. Passo a passo para testar a mudança

## Screenshots (se aplicável)

## Issues relacionadas
Closes #42
```

---

### Issues — Rastreando Problemas e Tarefas

```markdown
<!-- Título da Issue -->
[BUG] Login falha ao usar e-mail com maiúsculas

<!-- Corpo da Issue -->
## Descrição
Ao fazer login com e-mail "Usuario@Email.com", o sistema retorna
"Usuário não encontrado", mesmo que o usuário exista no banco.

## Passos para Reproduzir
1. Acesse /login
2. Digite e-mail com letras maiúsculas
3. Clique em Entrar
4. Observe o erro

## Comportamento Esperado
Login deve funcionar independente de maiúsculas/minúsculas.

## Ambiente
- Browser: Chrome 120
- OS: Windows 11
- Versão: v2.3.1
```

**Referenciando Issues em commits:**
```bash
git commit -m "fix: normaliza email para minúsculas no login

Closes #15"
```

---

### Code Review — Revisando PRs

```bash
# Baixar uma PR para testar localmente
git fetch origin pull/42/head:pr-42
git switch pr-42

# Ou usando GitHub CLI
gh pr checkout 42
```

**O que verificar no Code Review:**
- ✅ O código faz o que a PR diz que faz?
- ✅ Está legível e bem nomeado?
- ✅ Tem testes para as mudanças?
- ✅ Pode causar problemas de performance?
- ✅ Tem algum risco de segurança?
- ✅ Segue os padrões do projeto?

---

### GitHub CLI — Usando o GitHub no Terminal

```bash
# Instalar: https://cli.github.com

# Autenticar
gh auth login

# Criar PR direto do terminal
gh pr create --title "feat: login com Google" --body "Closes #10"

# Listar PRs abertas
gh pr list

# Verificar status da PR
gh pr status

# Fazer merge de uma PR
gh pr merge 42

# Criar issue
gh issue create --title "Bug no login" --body "Descrição..."

# Listar issues
gh issue list

# Clonar qualquer repositório
gh repo clone usuario/repositorio

# Ver repositórios
gh repo list
```

---

## Módulo 9 — Desfazendo Coisas

Esta é uma das partes mais importantes do Git — e a que mais causa ansiedade em iniciantes.

```
┌──────────────────────────────────────────────────────────┐
│  DESFAZENDO MUDANÇAS — MAPA MENTAL                       │
│                                                          │
│  Arquivo editado (não adicionado):                       │
│    git restore <arquivo>                                 │
│                                                          │
│  Arquivo no stage (adicionado, não commitado):           │
│    git restore --staged <arquivo>                        │
│                                                          │
│  Último commit (mantendo as mudanças):                   │
│    git reset --soft HEAD~1                               │
│                                                          │
│  Último commit (descartando as mudanças):                │
│    git reset --hard HEAD~1  ← CUIDADO!                  │
│                                                          │
│  Commit já enviado ao remoto (seguro):                   │
│    git revert <hash>                                     │
└──────────────────────────────────────────────────────────┘
```

---

### git restore — Desfazendo Edições

```bash
# Descartar mudanças em um arquivo (volta ao último commit)
git restore index.html

# Descartar mudanças em todos os arquivos
git restore .

# Remover arquivo do stage (mantém as mudanças no arquivo)
git restore --staged index.html
git restore --staged .    # remover tudo do stage

# Restaurar arquivo para uma versão de um commit específico
git restore --source=a3f8c2d index.html
```

---

### git reset — Movendo o HEAD

```bash
# --soft: desfaz o commit, mantém arquivos no STAGE
git reset --soft HEAD~1
# Útil para: desfazer o commit mas querer recomitar com outra mensagem

# --mixed (padrão): desfaz o commit, mantém arquivos no WORKING DIRECTORY
git reset HEAD~1
git reset --mixed HEAD~1
# Útil para: desfazer o commit e o add, mas manter as edições

# --hard: desfaz o commit E descarta todas as mudanças
git reset --hard HEAD~1
# ⚠️ CUIDADO! As mudanças são perdidas para sempre

# Voltar para um commit específico
git reset --hard a3f8c2d

# HEAD~1 = 1 commit atrás
# HEAD~3 = 3 commits atrás
```

---

### git revert — Desfazendo com Segurança

**Use sempre `git revert` para desfazer commits já enviados ao remoto.** Ele cria um novo commit que desfaz as mudanças, sem reescrever o histórico:

```bash
# Reverter o último commit
git revert HEAD

# Reverter um commit específico
git revert a3f8c2d

# Reverter sem abrir o editor (usa mensagem padrão)
git revert a3f8c2d --no-edit

# Reverter múltiplos commits
git revert HEAD~3..HEAD   # reverte os últimos 3 commits
```

**Diferença visual:**

```
git reset --hard HEAD~1:
  A ── B ── C          # C é removido do histórico

git revert C:
  A ── B ── C ── C'    # C' desfaz as mudanças de C, mas C ainda existe
```

---

### git reflog — O Resgate Final

O `reflog` guarda **todas as ações** que você fez, mesmo as que apagaram commits. É o último recurso quando você acha que perdeu algo:

```bash
# Ver o histórico de todas as ações (até 90 dias)
git reflog

# Saída:
# a3f8c2d HEAD@{0}: commit: feat: adiciona login
# 7b2e1a0 HEAD@{1}: reset: moving to HEAD~1
# 4d9c1f2 HEAD@{2}: commit: fix: bug no formulário
# ...

# Recuperar um commit "perdido"
git checkout 4d9c1f2          # voltar para aquele estado
git switch -c branch-recuperada  # salvar em uma branch nova

# Ou direto:
git reset --hard 4d9c1f2
```

---

## Módulo 10 — Stash, Tags e Cherry-pick

### git stash — Guardar Mudanças Temporariamente

Stash "guarda na gaveta" suas mudanças sem fazer commit, útil para trocar de branch rapidamente:

```bash
# Guardar mudanças atuais
git stash

# Guardar com uma descrição (muito recomendado!)
git stash push -m "WIP: implementando carrinho de compras"

# Guardar incluindo arquivos novos (untracked)
git stash push -u -m "feature login em progresso"

# Listar o que está no stash
git stash list
# stash@{0}: On feature/login: WIP: implementando carrinho
# stash@{1}: On main: fix rápido ainda não finalizado

# Aplicar o stash mais recente (mantém no stash)
git stash apply

# Aplicar e remover do stash
git stash pop

# Aplicar um stash específico
git stash apply stash@{1}

# Remover um stash
git stash drop stash@{0}

# Limpar todos os stashes
git stash clear

# Ver o que está em um stash antes de aplicar
git stash show -p stash@{0}
```

**Fluxo de uso típico:**
```bash
# Você está no meio de algo quando surge uma urgência

# 1. Guardar o trabalho em progresso
git stash push -m "WIP: novo sistema de busca"

# 2. Corrigir o bug urgente em outra branch
git switch main
git switch -c hotfix/bug-critico
# ... fazer o fix ...
git commit -m "fix: corrige crash no checkout"
git switch main
git merge hotfix/bug-critico

# 3. Voltar para o trabalho anterior
git switch feature/busca
git stash pop
```

---

### git tag — Marcando Versões

Tags marcam pontos específicos do histórico, geralmente para versões de lançamento:

```bash
# Criar tag simples (lightweight)
git tag v1.0.0

# Criar tag anotada (com mensagem — recomendado para releases)
git tag -a v1.0.0 -m "Release v1.0.0: primeira versão estável"

# Criar tag em um commit específico
git tag -a v0.9.0 a3f8c2d -m "Release v0.9.0: beta"

# Listar tags
git tag
git tag -l "v1.*"    # filtra por padrão

# Ver detalhes de uma tag
git show v1.0.0

# Enviar tags para o GitHub (tags não são enviadas por padrão!)
git push origin v1.0.0        # envia uma tag específica
git push origin --tags        # envia todas as tags

# Deletar tag
git tag -d v1.0.0             # local
git push origin --delete v1.0.0  # remota
```

---

### git cherry-pick — Pegando Commits Específicos

Cherry-pick aplica um commit específico de outra branch na sua branch atual:

```bash
# Aplicar um commit específico
git cherry-pick a3f8c2d

# Aplicar sem fazer commit automaticamente (para revisar antes)
git cherry-pick a3f8c2d --no-commit

# Aplicar um range de commits
git cherry-pick a3f8c2d..7b2e1a0

# Caso de uso clássico: aplicar um hotfix tanto na main quanto na release
git switch release/v1.2
git cherry-pick a3f8c2d    # traz o fix do hotfix
git push origin release/v1.2
```

---

## Módulo 11 — GitHub Actions (CI/CD)

**GitHub Actions** permite automatizar tarefas (rodar testes, fazer deploy, gerar releases) direto no GitHub, disparadas por eventos no repositório.

### Estrutura de um Workflow

```
.github/
└── workflows/
    ├── ci.yml         ← rodar testes em cada PR
    ├── deploy.yml     ← fazer deploy ao mergear na main
    └── release.yml    ← criar release ao criar uma tag
```

---

### Exemplo 1 — CI: Rodar Testes em Cada PR

```yaml
# .github/workflows/ci.yml

name: CI — Testes e Lint

# Quando este workflow roda:
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    name: Rodar Testes
    runs-on: ubuntu-latest   # tipo de máquina

    steps:
      - name: Checkout do código
        uses: actions/checkout@v4

      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Instalar dependências
        run: npm ci

      - name: Rodar lint
        run: npm run lint

      - name: Rodar testes
        run: npm test

      - name: Verificar cobertura
        run: npm run test:coverage
```

---

### Exemplo 2 — Deploy Automático

```yaml
# .github/workflows/deploy.yml

name: Deploy — Produção

on:
  push:
    branches: [main]   # dispara ao mergear na main

jobs:
  deploy:
    name: Deploy para produção
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Build da aplicação
        run: npm run build
        env:
          NODE_ENV: production

      - name: Deploy para o servidor
        run: |
          echo "${{ secrets.SSH_KEY }}" > key.pem
          chmod 600 key.pem
          rsync -avz --delete dist/ user@servidor:/var/www/app/
        env:
          SSH_KEY: ${{ secrets.SSH_KEY }}  # segredo configurado no GitHub

      - name: Notificar time no Slack
        uses: slackapi/slack-github-action@v1
        with:
          payload: '{"text": "✅ Deploy realizado com sucesso!"}'
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

---

### Exemplo 3 — Workflow para Python

```yaml
# .github/workflows/python-ci.yml

name: CI Python

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: ['3.10', '3.11', '3.12']  # testa em 3 versões!

    steps:
      - uses: actions/checkout@v4

      - name: Setup Python ${{ matrix.python-version }}
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}

      - name: Instalar dependências
        run: |
          pip install -r requirements.txt
          pip install pytest pytest-cov flake8

      - name: Lint com flake8
        run: flake8 . --max-line-length=120

      - name: Testes com pytest
        run: pytest --cov=. --cov-report=xml

      - name: Upload coverage para Codecov
        uses: codecov/codecov-action@v3
```

---

### Conceitos Essenciais do GitHub Actions

| Conceito | O que é |
|---|---|
| **Workflow** | O arquivo YAML completo (`.github/workflows/*.yml`) |
| **Event** | O que dispara o workflow (`push`, `pull_request`, `schedule`...) |
| **Job** | Um grupo de steps que rodam numa máquina |
| **Step** | Uma tarefa individual dentro de um job |
| **Action** | Um step reutilizável criado pela comunidade (`uses:`) |
| **Runner** | A máquina virtual onde o job roda (`ubuntu-latest`) |
| **Secret** | Variável sensível configurada nas Settings do repositório |

---

## Módulo 12 — Fluxos de Trabalho Profissionais

### Git Flow — Para Projetos com Releases

```
main        ──────────────────────────────── v1.0 ── v1.1
              \                             /     \
develop        ──────────────────────────            \
                 \       \         /                  \
feature/login     ──────  \       /       hotfix/bug   ──
                           \     /
feature/pagamento            ───
```

**Branches do Git Flow:**

| Branch | Função |
|---|---|
| `main` | Código em produção — **sempre estável** |
| `develop` | Integração das features — próxima release |
| `feature/*` | Novas funcionalidades |
| `release/*` | Preparação de uma nova versão |
| `hotfix/*` | Correções urgentes em produção |

---

### GitHub Flow — Para Deploy Contínuo

Mais simples, ideal para times que fazem deploy frequente:

```
main        ──────────────────────────────────────
              \     \     \   /   \   /
feature        ──    ──    ─        ─
                  PR↑   PR↑     PR↑
```

**As regras do GitHub Flow:**
1. `main` é **sempre deployável**
2. Novas features sempre em uma **branch com nome descritivo**
3. Commit para a branch regularmente
4. Abra um **PR** para discussão e revisão
5. Merge apenas após **aprovação** e **CI verde**
6. Deploy imediato após merge na main

---

### Trunk Based Development — Para Times Avançados

```
main   ──────────────────────────────────────────
        ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑   ↑
       commits diretos (com feature flags)
       ou branches com vida máxima de 1-2 dias
```

- Todos commitam direto na `main` ou em branches muito curtas
- Feature Flags controlam o que está ativo ou não em produção
- Exige alto nível de testes automatizados

---

## Módulo 13 — Boas Práticas

### Commits

```bash
# ✅ Commits pequenos e focados em uma coisa só
git commit -m "feat: adiciona validação de CPF"

# ❌ Commit gigante com várias mudanças misturadas
git commit -m "adiciona várias coisas e corrige bugs"

# ✅ Mensagem no imperativo presente
git commit -m "feat: adiciona autenticação de dois fatores"

# ❌ Mensagem no passado
git commit -m "adicionei autenticação de dois fatores"

# ✅ Commite cedo e com frequência (salva o trabalho)
# ❌ Trabalhar 2 dias e fazer 1 commit enorme
```

---

### Segurança — O Que Nunca Commitar

```bash
# ❌ NUNCA commite isso:
.env                    # variáveis de ambiente
config/database.yml     # credenciais de banco
*.pem / *.key           # chaves privadas
secrets.json            # segredos de API
passwords.txt           # senhas

# Se commitou por acidente, NÃO é suficiente só deletar o arquivo!
# A credencial está no histórico. Você PRECISA:
# 1. Revogar a credencial no serviço (AWS, GitHub, etc.)
# 2. Usar BFG Repo-Cleaner ou git-filter-repo para limpar o histórico

# Limpar segredo do histórico com BFG:
bfg --delete-files .env
git push --force

# Usar git-filter-repo (mais moderno):
git filter-repo --invert-paths --path .env
```

---

### .gitignore Essencial por Tecnologia

```gitignore
# Node.js
node_modules/
.env
.env.local
dist/
build/
npm-debug.log*

# Python
__pycache__/
*.py[cod]
*.pyc
.venv/
venv/
.env
dist/
*.egg-info/

# Java
*.class
*.jar
target/
.classpath
.project

# Geral (sempre inclua)
.DS_Store        # macOS
Thumbs.db        # Windows
*.log
.idea/
.vscode/
*.swp
```

---

### Aliases Úteis

```bash
# Configurar aliases para comandos frequentes
git config --global alias.st "status -sb"
git config --global alias.lg "log --oneline --graph --all --decorate"
git config --global alias.co "checkout"
git config --global alias.sw "switch"
git config --global alias.br "branch"
git config --global alias.last "log -1 HEAD"
git config --global alias.undo "reset HEAD~1 --mixed"
git config --global alias.aliases "config --get-regexp '^alias\.'"

# Usar:
git st       # status compacto
git lg       # log visual com grafo
git last     # ver o último commit
git undo     # desfazer o último commit mantendo as mudanças
```

---

## 🚀 Cheatsheet Git

```bash
# =============================================
# CONFIGURAÇÃO
# =============================================
git config --global user.name "Nome"
git config --global user.email "email@email.com"
git config --global init.defaultBranch main
git config --list

# =============================================
# REPOSITÓRIO
# =============================================
git init                        # novo repositório local
git clone <url>                 # clonar repositório
git clone <url> <pasta>         # clonar em pasta específica

# =============================================
# STATUS E HISTÓRICO
# =============================================
git status                      # estado atual
git status -s                   # formato compacto
git log                         # histórico completo
git log --oneline               # uma linha por commit
git log --oneline --graph --all # grafo de branches
git diff                        # mudanças não staged
git diff --staged               # mudanças staged
git show <hash>                 # detalhes de um commit
git blame <arquivo>             # quem alterou cada linha

# =============================================
# STAGE E COMMIT
# =============================================
git add <arquivo>               # adicionar ao stage
git add .                       # adicionar tudo
git add -p                      # adicionar interativamente
git restore --staged <arquivo>  # remover do stage
git restore <arquivo>           # descartar mudanças
git commit -m "mensagem"        # commitar
git commit --amend              # editar o último commit
git commit --amend --no-edit    # adicionar ao último commit sem editar mensagem

# =============================================
# BRANCHES
# =============================================
git branch                      # listar locais
git branch -a                   # listar todas
git switch <branch>             # trocar de branch
git switch -c <branch>          # criar e trocar
git branch -d <branch>          # deletar (seguro)
git branch -D <branch>          # forçar deleção
git branch -m <novo-nome>       # renomear atual

# =============================================
# MERGE E REBASE
# =============================================
git merge <branch>              # merge na branch atual
git merge --no-ff <branch>      # forçar commit de merge
git merge --abort               # cancelar merge com conflito
git rebase <branch>             # rebase na branch
git rebase -i HEAD~N            # rebase interativo (N commits)
git rebase --abort              # cancelar rebase

# =============================================
# REMOTO
# =============================================
git remote -v                   # listar remotos
git remote add origin <url>     # adicionar remoto
git push origin <branch>        # enviar branch
git push -u origin <branch>     # enviar e definir upstream
git push --force-with-lease     # force push seguro
git pull                        # fetch + merge
git pull --rebase               # fetch + rebase
git fetch origin                # baixar sem aplicar
git fetch --prune               # limpar branches deletadas

# =============================================
# DESFAZENDO
# =============================================
git restore <arquivo>           # descartar edições
git restore --staged <arquivo>  # tirar do stage
git reset --soft HEAD~1         # desfazer commit (mantém stage)
git reset HEAD~1                # desfazer commit (mantém working)
git reset --hard HEAD~1         # desfazer commit (perde tudo) ⚠️
git revert <hash>               # reverter com novo commit (seguro)
git reflog                      # histórico de ações (resgate!)

# =============================================
# STASH
# =============================================
git stash                       # guardar mudanças
git stash push -m "descrição"   # guardar com descrição
git stash list                  # listar stashes
git stash pop                   # aplicar e remover
git stash apply stash@{N}       # aplicar específico
git stash drop stash@{N}        # remover específico
git stash clear                 # remover todos

# =============================================
# TAGS
# =============================================
git tag v1.0.0                  # tag simples
git tag -a v1.0.0 -m "msg"      # tag anotada
git push origin --tags          # enviar tags
git tag -d v1.0.0               # deletar local

# =============================================
# UTILITÁRIOS
# =============================================
git cherry-pick <hash>          # aplicar commit específico
git bisect start                # iniciar busca binária de bug
git shortlog -sn                # contribuições por autor
git archive --format=zip HEAD > projeto.zip
```

---

## 📝 Exercícios Práticos

### 🟢 Nível 1 — Iniciante

**Exercício 1.1 — Primeiro Repositório**

- [ ] Crie uma pasta `curso-git` e inicialize um repositório Git
- [ ] Crie um arquivo `README.md` com uma descrição qualquer
- [ ] Crie um `.gitignore` ignorando arquivos `.log` e `node_modules/`
- [ ] Faça o primeiro commit com a mensagem `docs: initial commit`
- [ ] Verifique o log com `git log --oneline`

**Exercício 1.2 — Subindo para o GitHub**

- [ ] Crie um repositório vazio no GitHub
- [ ] Conecte seu repositório local ao GitHub com `git remote add`
- [ ] Envie seus commits com `git push`
- [ ] Adicione uma foto ao README e faça um novo commit

---

### 🟡 Nível 2 — Intermediário

**Exercício 2.1 — Trabalhando com Branches**

- [ ] No repositório do exercício anterior, crie a branch `feature/pagina-sobre`
- [ ] Crie um arquivo `sobre.md` e faça 2 commits nessa branch
- [ ] Volte para a `main` e crie outra branch `feature/pagina-contato`
- [ ] Crie `contato.md` com 1 commit
- [ ] Faça merge de `feature/pagina-sobre` na `main`
- [ ] Faça merge de `feature/pagina-contato` na `main`
- [ ] Delete as duas branches de feature
- [ ] Visualize o grafo com `git log --oneline --graph --all`

**Exercício 2.2 — Conflito Intencional**

- [ ] Crie a branch `feature/a` e edite a primeira linha de `README.md`
- [ ] Volte para `main`, crie `feature/b` e edite a mesma linha de outra forma
- [ ] Tente fazer merge de `feature/b` na `main` → conflito!
- [ ] Resolva o conflito manualmente
- [ ] Complete o merge com um commit

---

### 🔴 Nível 3 — Avançado

**Exercício 3.1 — Contribuindo para um Projeto Open Source**

- [ ] Encontre um projeto open source pequeno no GitHub
- [ ] Faça um **Fork** do repositório
- [ ] Clone o seu fork localmente
- [ ] Adicione o repositório original como `upstream`
- [ ] Crie uma branch, faça uma melhoria pequena (fix de typo, melhoria de docs)
- [ ] Abra um **Pull Request** para o repositório original
- [ ] Escreva uma boa descrição de PR

**Exercício 3.2 — GitHub Actions**

- [ ] Crie um repositório com um script Python simples
- [ ] Crie o arquivo `.github/workflows/ci.yml`
- [ ] Configure o workflow para rodar `python -m pytest` em cada push
- [ ] Faça um push e observe o workflow rodar na aba Actions do GitHub
- [ ] Propositalmente quebre um teste e veja o workflow falhar em vermelho
- [ ] Corrija o teste e veja o workflow passar em verde

---

## 📚 Recursos Recomendados

| Recurso | Tipo | Link |
|---|---|---|
| **Pro Git Book** | Livro gratuito e completo | [git-scm.com/book](https://git-scm.com/book/pt-br/v2) |
| **Learn Git Branching** | Jogo interativo visual | [learngitbranching.js.org](https://learngitbranching.js.org/?locale=pt_BR) |
| **Oh My Git!** | Jogo de cartas para aprender Git | [ohmygit.org](https://ohmygit.org) |
| **GitHub Skills** | Cursos oficiais do GitHub | [skills.github.com](https://skills.github.com) |
| **Conventional Commits** | Padrão de mensagens | [conventionalcommits.org](https://www.conventionalcommits.org/pt-br) |
| **gitignore.io** | Gerador de .gitignore | [gitignore.io](https://gitignore.io) |
| **GitHub CLI** | Git no terminal | [cli.github.com](https://cli.github.com) |

---

<div align="center">

**Feito com ❤️ e muitos `git commit --amend`**

*"Todo mundo comete erros. É por isso que o Git tem o `git revert`."*

⭐ Se este curso te ajudou, dê uma estrela no repositório!

</div>
