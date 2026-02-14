# 🧠 Curso Completo de Lógica de Programação

> **Do zero ao avançado** — aprenda a pensar como um programador antes mesmo de aprender uma linguagem. Este curso usa **pseudocódigo** e **exemplos visuais** para que você entenda os conceitos de forma universal.

---

## 📋 Índice

1. [O que é Lógica de Programação?](#-o-que-é-lógica-de-programação)
2. [Como os Computadores Pensam](#-como-os-computadores-pensam)
3. [Módulo 1 — Algoritmos](#módulo-1--algoritmos)
4. [Módulo 2 — Variáveis e Tipos de Dados](#módulo-2--variáveis-e-tipos-de-dados)
5. [Módulo 3 — Operadores](#módulo-3--operadores)
6. [Módulo 4 — Estruturas de Decisão](#módulo-4--estruturas-de-decisão)
7. [Módulo 5 — Estruturas de Repetição (Loops)](#módulo-5--estruturas-de-repetição-loops)
8. [Módulo 6 — Vetores e Matrizes](#módulo-6--vetores-e-matrizes)
9. [Módulo 7 — Funções e Procedimentos](#módulo-7--funções-e-procedimentos)
10. [Módulo 8 — Recursão](#módulo-8--recursão)
11. [Módulo 9 — Busca e Ordenação](#módulo-9--busca-e-ordenação)
12. [Módulo 10 — Introdução a Estruturas de Dados](#módulo-10--introdução-a-estruturas-de-dados)
13. [Módulo 11 — Depuração e Boas Práticas](#módulo-11--depuração-e-boas-práticas)
14. [Exercícios Resolvidos por Nível](#-exercícios-resolvidos-por-nível)
15. [Cheatsheet de Pseudocódigo](#-cheatsheet-de-pseudocódigo)
16. [Próximos Passos](#-próximos-passos)

---

## 🤔 O que é Lógica de Programação?

**Lógica de programação** é a habilidade de organizar o pensamento de forma estruturada para resolver problemas por meio de passos lógicos, sequenciais e precisos — exatamente como um computador precisa que você faça.

> **Analogia perfeita:** Imagine que você está escrevendo uma receita de bolo para um robô extremamente literal. Se você escrever *"adicione sal a gosto"*, ele não sabe o que fazer. Você precisa dizer: *"adicione exatamente 5 gramas de sal"*. Esse nível de precisão é o que a programação exige.

### Por que aprender lógica antes de uma linguagem?

```
Linguagem de programação = Ferramenta
Lógica de programação   = Habilidade de pensar

Você pode trocar de ferramenta.
Sua habilidade de pensar vai com você.
```

- 🐍 Python, ☕ Java, 🌐 JavaScript, 🦀 Rust... são diferentes, mas a **lógica é a mesma**
- Quem aprende lógica bem, aprende qualquer linguagem em muito menos tempo
- É o que diferencia um programador iniciante de um desenvolvedor sênior

---

## 💻 Como os Computadores Pensam

Computadores são **literais** e **sequenciais**. Eles fazem exatamente o que você manda, na ordem que você manda — nem mais, nem menos.

### O modelo básico de execução

```
┌─────────────────────────────────────────────────────┐
│                   PROGRAMA                          │
│                                                     │
│  ENTRADA  →  PROCESSAMENTO  →  SAÍDA                │
│  (input)     (algoritmo)       (output)             │
│                                                     │
│  Exemplos:                                          │
│  Teclado  →  Calcular média  →  Mostrar na tela     │
│  Arquivo  →  Filtrar dados   →  Salvar resultado    │
│  Sensor   →  Detectar padrão →  Acionar alarme      │
└─────────────────────────────────────────────────────┘
```

### A memória do computador

Pense na memória RAM como uma **rua com casas numeradas**. Cada casa tem um endereço (número) e pode guardar um valor:

```
Endereço:  [0001] [0002] [0003] [0004] [0005]
Valor:       42    "Ana"  true   3.14    ?
Nome:      [idade][nome] [ativo][pi]  [vazio]
```

Quando você cria uma **variável** no seu programa, está reservando uma "casa" na memória para guardar um dado.

---

## Módulo 1 — Algoritmos

### O que é um Algoritmo?

Um **algoritmo** é uma sequência finita de instruções bem definidas para resolver um problema. Todo programa é, em essência, um algoritmo.

### As 3 características obrigatórias

| Característica | Significa | Exemplo ruim | Exemplo bom |
|---|---|---|---|
| **Finito** | Deve terminar em algum momento | Contar até infinito | Contar até 100 |
| **Definido** | Cada passo deve ser claro e sem ambiguidade | "Adicione sal a gosto" | "Adicione 5g de sal" |
| **Eficaz** | Cada passo deve ser executável | "Divida por zero" | "Divida por 2" |

---

### Formas de Representar Algoritmos

#### 1. Descrição Narrativa (linguagem natural)

```
Para fazer um café:
1. Ferva água
2. Coloque 2 colheres de pó no coador
3. Despeje a água sobre o pó
4. Aguarde filtrar
5. Sirva na xícara
```

Fácil de entender, mas imprecisa demais para computadores.

---

#### 2. Pseudocódigo

Uma linguagem intermediária entre o português e a programação real:

```
ALGORITMO FazerCafe
  INICIO
    ferva_agua()
    adicione_po(quantidade = 2, unidade = "colheres")
    despeje_agua_no_coador()
    aguarde(tempo = 3, unidade = "minutos")
    sirva_na_xicara()
  FIM
```

> 💡 Pseudocódigo é o que vamos usar neste curso! Ele é universal — não depende de nenhuma linguagem específica.

---

#### 3. Fluxograma

Representação visual usando formas geométricas:

```
         ┌──────────────┐
         │    INÍCIO    │
         └──────┬───────┘
                │
         ┌──────▼───────┐
         │  Ferva água  │
         └──────┬───────┘
                │
         ┌──────▼──────────────┐
         │ Adicione 2 colheres │
         └──────┬──────────────┘
                │
         ┌──────▼───────────────────┐
         │ Água já filtrou?         │
         └──────┬──────────┬────────┘
               SIM         NÃO
                │           │
                │    ┌──────▼───────┐
                │    │  Aguarde 1   │
                │    │   minuto     │
                │    └──────┬───────┘
                │           │ (volta para a pergunta)
         ┌──────▼───────┐   │
         │  Sirva café  │◄──┘
         └──────┬───────┘
                │
         ┌──────▼───────┐
         │     FIM      │
         └──────────────┘
```

**Legenda dos símbolos:**

| Símbolo | Forma | Representa |
|---|---|---|
| Início/Fim | Oval (arredondado) | Começo e fim do programa |
| Processo | Retângulo | Instrução ou ação |
| Decisão | Losango | Pergunta (sim/não) |
| Entrada/Saída | Paralelogramo | Ler ou mostrar dados |
| Fluxo | Seta | Direção da execução |

---

### Exemplo Completo: Algoritmo para Atravessar a Rua

**Narrativa:**
```
Para atravessar a rua com segurança:
1. Chegue na calçada
2. Olhe para os dois lados
3. Se vier carro, espere
4. Se não vier carro, atravesse
5. Chegou do outro lado? Fim.
```

**Pseudocódigo:**
```
ALGORITMO AtravessarRua
  INICIO
    ENQUANTO tem_carro_vindo() FAÇA
      espere()
    FIM_ENQUANTO
    atravesse()
    ESCREVA "Chegou com segurança!"
  FIM
```

---

## Módulo 2 — Variáveis e Tipos de Dados

### O que é uma Variável?

Uma **variável** é um espaço na memória do computador com um **nome** e um **valor** que pode mudar ao longo do programa.

```
        NOME         VALOR
       ┌─────────┐  ┌───────┐
       │  idade  │→ │  25   │
       └─────────┘  └───────┘
       ┌─────────┐  ┌───────────┐
       │  nome   │→ │  "Maria"  │
       └─────────┘  └───────────┘
       ┌─────────┐  ┌───────┐
       │  saldo  │→ │ 150.75│
       └─────────┘  └───────┘
```

### Declarando Variáveis (Pseudocódigo)

```
DECLARE idade: INTEIRO
DECLARE nome: TEXTO
DECLARE salario: REAL
DECLARE aprovado: BOOLEANO

idade ← 25
nome ← "Carlos"
salario ← 3500.50
aprovado ← VERDADEIRO
```

> ⚠️ **Importante:** O símbolo `←` significa **atribuição** (guardar um valor na variável). Não confunda com `=` de igualdade matemática!

---

### Tipos de Dados Fundamentais

#### 🔢 Inteiro (Integer)

Números **sem casas decimais**, positivos ou negativos:

```
idade ← 25
temperatura ← -10
quantidade ← 0
ano ← 2024
```

**Limite:** Depende do sistema, mas geralmente de -2.147.483.648 a 2.147.483.647.

---

#### 🔣 Real / Float (Ponto Flutuante)

Números **com casas decimais**:

```
preco ← 29.99
altura ← 1.75
pi ← 3.14159
desconto ← -5.5
```

> ⚠️ **Cuidado com comparações!** Devido à forma como computadores armazenam números reais, `0.1 + 0.2` pode não ser exatamente `0.3` na memória. Sempre use margens de erro (`epsilon`) ao comparar floats.

---

#### 📝 Texto / String (Cadeia de caracteres)

Sequência de caracteres, sempre entre aspas:

```
nome ← "Ana"
mensagem ← "Olá, mundo!"
cpf ← "123.456.789-00"   ← CPF é texto, não número!
vazio ← ""               ← String vazia
```

> 💡 **Por que CPF é texto e não número?** Porque você não faz contas com CPF. Além disso, zeros à esquerda (como `007`) seriam perdidos em um número.

---

#### ✅ Booleano (Boolean)

Só pode ter **dois valores**: `VERDADEIRO` ou `FALSO` (true/false):

```
esta_chovendo ← VERDADEIRO
tem_desconto ← FALSO
usuario_logado ← VERDADEIRO
maior_de_idade ← FALSO
```

Este tipo é a base de toda lógica de decisão em programação.

---

#### 📊 Resumo dos Tipos

| Tipo | Exemplos | Uso |
|---|---|---|
| **Inteiro** | `1`, `42`, `-7`, `0` | Contadores, idades, IDs |
| **Real** | `3.14`, `-0.5`, `100.0` | Preços, médias, medidas |
| **Texto** | `"Ana"`, `"CPF"`, `""` | Nomes, mensagens, códigos |
| **Booleano** | `VERDADEIRO`, `FALSO` | Flags, condições, status |

---

### Constantes

Uma **constante** é como uma variável, mas seu valor **nunca muda** após ser definido:

```
CONSTANTE PI ← 3.14159265
CONSTANTE VELOCIDADE_LUZ ← 299792458
CONSTANTE MAX_TENTATIVAS ← 3
```

Por convenção, constantes são escritas em **MAIÚSCULAS**.

---

### Boas Práticas para Nomear Variáveis

| ✅ Bom | ❌ Ruim | Por quê |
|---|---|---|
| `idade_usuario` | `x` | Descritivo vs vago |
| `total_vendas` | `tv` | Claro vs abreviação confusa |
| `esta_ativo` | `flag1` | Indica booleano vs genérico |
| `preco_produto` | `preco produto` | Sem espaços! |
| `nomeCliente` | `NomeCliente` | Convenção consistente |

> 📏 **Regra de ouro:** Se você precisar de um comentário para explicar o nome da variável, escolha um nome melhor.

---

## Módulo 3 — Operadores

Operadores são símbolos que realizam operações sobre valores.

### Operadores Aritméticos

| Operador | Operação | Exemplo | Resultado |
|:---:|---|---|:---:|
| `+` | Adição | `5 + 3` | `8` |
| `-` | Subtração | `10 - 4` | `6` |
| `*` | Multiplicação | `3 * 7` | `21` |
| `/` | Divisão real | `10 / 3` | `3.333...` |
| `DIV` | Divisão inteira | `10 DIV 3` | `3` |
| `MOD` | Resto (módulo) | `10 MOD 3` | `1` |
| `^` | Potência | `2 ^ 8` | `256` |

#### O poder do MOD (resto da divisão)

O operador `MOD` é extremamente útil em programação:

```
Verificar se número é par:     numero MOD 2 = 0
Verificar se é ímpar:          numero MOD 2 = 1
Verificar se é múltiplo de 5:  numero MOD 5 = 0
Obter último dígito de número: numero MOD 10
```

```
ALGORITMO VerificarParOuImpar
  INICIO
    ESCREVA "Digite um número: "
    LEIA numero
    SE numero MOD 2 = 0 ENTÃO
      ESCREVA numero, " é par"
    SENÃO
      ESCREVA numero, " é ímpar"
    FIM_SE
  FIM
```

---

### Operadores Relacionais (Comparação)

Comparam dois valores e retornam **VERDADEIRO** ou **FALSO**:

| Operador | Significado | Exemplo | Resultado |
|:---:|---|---|:---:|
| `=` | Igual a | `5 = 5` | `VERDADEIRO` |
| `≠` ou `!=` | Diferente de | `5 ≠ 3` | `VERDADEIRO` |
| `>` | Maior que | `8 > 10` | `FALSO` |
| `<` | Menor que | `3 < 7` | `VERDADEIRO` |
| `≥` ou `>=` | Maior ou igual | `5 ≥ 5` | `VERDADEIRO` |
| `≤` ou `<=` | Menor ou igual | `4 ≤ 3` | `FALSO` |

---

### Operadores Lógicos

Combinam expressões booleanas:

| Operador | Símbolo | Descrição |
|---|---|---|
| **E** | `E`, `AND`, `&&` | Verdadeiro **somente** se os **dois** forem verdadeiros |
| **OU** | `OU`, `OR`, `\|\|` | Verdadeiro se **pelo menos um** for verdadeiro |
| **NÃO** | `NÃO`, `NOT`, `!` | **Inverte** o valor lógico |

#### Tabelas-Verdade

**Operador E (AND):**

| A | B | A E B |
|:---:|:---:|:---:|
| V | V | ✅ V |
| V | F | ❌ F |
| F | V | ❌ F |
| F | F | ❌ F |

> 🧠 **Mnemônico:** Para o **E**, pense *"exigente"* — precisa que os **dois** sejam verdadeiros.

**Operador OU (OR):**

| A | B | A OU B |
|:---:|:---:|:---:|
| V | V | ✅ V |
| V | F | ✅ V |
| F | V | ✅ V |
| F | F | ❌ F |

> 🧠 **Mnemônico:** Para o **OU**, pense *"generoso"* — basta **um** ser verdadeiro.

**Operador NÃO (NOT):**

| A | NÃO A |
|:---:|:---:|
| V | ❌ F |
| F | ✅ V |

---

#### Exemplo prático combinando operadores

```
ALGORITMO VerificarAcesso
  INICIO
    LEIA usuario, senha, esta_banido

    SE (usuario = "admin" E senha = "1234") E NÃO esta_banido ENTÃO
      ESCREVA "Acesso liberado! ✅"
    SENÃO
      SE esta_banido ENTÃO
        ESCREVA "Usuário banido. ❌"
      SENÃO
        ESCREVA "Usuário ou senha incorretos. ❌"
      FIM_SE
    FIM_SE
  FIM
```

---

### Precedência de Operadores

Assim como na matemática, os operadores têm ordem de execução:

```
1. ( )         → Parênteses primeiro
2. ^           → Potência
3. * / DIV MOD → Multiplicação e divisão
4. + -         → Adição e subtração
5. = ≠ > < ≥ ≤ → Comparações
6. NÃO         → Negação lógica
7. E           → E lógico
8. OU          → Ou lógico
```

```
Exemplo: 2 + 3 * 4 = 14  (e não 20!)
         2 + (3 * 4) = 2 + 12 = 14 ✅

Dica: Use parênteses quando tiver dúvida!
         (2 + 3) * 4 = 5 * 4 = 20
```

---

## Módulo 4 — Estruturas de Decisão

Estruturas de decisão permitem que o programa **escolha caminhos diferentes** dependendo de condições.

### SE / ENTÃO / SENÃO

A estrutura mais fundamental da programação:

```
SE <condição> ENTÃO
  <bloco executado se condição for VERDADEIRA>
SENÃO
  <bloco executado se condição for FALSA>
FIM_SE
```

#### Exemplo 1 — Verificar maioridade

```
ALGORITMO VerificarMaioridade
  INICIO
    ESCREVA "Qual é a sua idade? "
    LEIA idade

    SE idade >= 18 ENTÃO
      ESCREVA "Você é maior de idade. ✅"
      ESCREVA "Pode entrar no site."
    SENÃO
      ESCREVA "Você é menor de idade. ❌"
      ESCREVA "Acesso negado."
    FIM_SE
  FIM
```

**Simulando a execução:**

```
Entrada: 25
→ 25 >= 18? SIM (VERDADEIRO)
→ Executa bloco do SE
→ Saída: "Você é maior de idade. ✅"

Entrada: 15
→ 15 >= 18? NÃO (FALSO)
→ Executa bloco do SENÃO
→ Saída: "Você é menor de idade. ❌"
```

---

### SE sem SENÃO

Quando você só quer fazer algo se a condição for verdadeira:

```
SE produto_em_falta ENTÃO
  ESCREVA "⚠️ Atenção: estoque esgotado!"
  enviar_alerta_compras()
FIM_SE
```

---

### SE aninhado (encadeado)

Para múltiplas condições:

```
ALGORITMO ClassificarNota
  INICIO
    ESCREVA "Digite a nota (0-10): "
    LEIA nota

    SE nota >= 9 ENTÃO
      ESCREVA "🏆 Excelente!"
    SENÃO SE nota >= 7 ENTÃO
      ESCREVA "✅ Aprovado"
    SENÃO SE nota >= 5 ENTÃO
      ESCREVA "⚠️ Recuperação"
    SENÃO
      ESCREVA "❌ Reprovado"
    FIM_SE
  FIM
```

**Tabela de resultados:**

| Nota | Resultado |
|---|---|
| 9.5 | 🏆 Excelente! |
| 8.0 | ✅ Aprovado |
| 6.0 | ⚠️ Recuperação |
| 3.0 | ❌ Reprovado |

---

### ESCOLHA / CASO (Switch/Case)

Ideal quando você compara uma variável com **vários valores possíveis**:

```
ALGORITMO DiaDaSemana
  INICIO
    ESCREVA "Digite o número do dia (1-7): "
    LEIA dia

    ESCOLHA dia
      CASO 1: ESCREVA "Domingo 😴"
      CASO 2: ESCREVA "Segunda-feira 😰"
      CASO 3: ESCREVA "Terça-feira 💪"
      CASO 4: ESCREVA "Quarta-feira 🐪"
      CASO 5: ESCREVA "Quinta-feira 🤔"
      CASO 6: ESCREVA "Sexta-feira 🎉"
      CASO 7: ESCREVA "Sábado 🥳"
      CASO CONTRÁRIO: ESCREVA "Dia inválido ❌"
    FIM_ESCOLHA
  FIM
```

> 💡 **Use ESCOLHA quando:** comparando um valor com muitas opções fixas.
> **Use SE/SENÃO quando:** a condição envolve intervalos ou expressões complexas.

---

### Operador Ternário (Expressão Condicional)

Um atalho para SE/SENÃO simples:

```
Sintaxe: resultado ← (condição) ? valor_se_verdadeiro : valor_se_falso

Exemplo:
  status ← (idade >= 18) ? "adulto" : "menor"
  desconto ← (eh_cliente_vip) ? 0.20 : 0.05
  sinal ← (numero > 0) ? "positivo" : "não positivo"
```

---

## Módulo 5 — Estruturas de Repetição (Loops)

Loops permitem executar um bloco de código **múltiplas vezes** sem precisar reescrevê-lo.

```
Sem loop:                    Com loop:
  ESCREVA "Olá"              REPITA 5 VEZES
  ESCREVA "Olá"                ESCREVA "Olá"
  ESCREVA "Olá"              FIM_REPITA
  ESCREVA "Olá"
  ESCREVA "Olá"
```

---

### PARA (For) — Quando se sabe quantas repetições

Use quando você sabe **exatamente** quantas vezes quer repetir:

```
PARA variavel ← inicio ATÉ fim [PASSO incremento] FAÇA
  <bloco de código>
FIM_PARA
```

#### Exemplo 1 — Contar de 1 a 10

```
ALGORITMO ContarAte10
  INICIO
    PARA i ← 1 ATÉ 10 FAÇA
      ESCREVA i
    FIM_PARA
  FIM
```

Saída: `1 2 3 4 5 6 7 8 9 10`

---

#### Exemplo 2 — Tabuada do 5

```
ALGORITMO Tabuada
  INICIO
    numero ← 5
    PARA i ← 1 ATÉ 10 FAÇA
      resultado ← numero * i
      ESCREVA numero, " x ", i, " = ", resultado
    FIM_PARA
  FIM
```

Saída:
```
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

---

#### Exemplo 3 — Contagem regressiva (passo negativo)

```
ALGORITMO ContagemRegressiva
  INICIO
    PARA i ← 10 ATÉ 0 PASSO -1 FAÇA
      ESCREVA i
    FIM_PARA
    ESCREVA "🚀 LANÇAMENTO!"
  FIM
```

Saída: `10 9 8 7 6 5 4 3 2 1 0 🚀 LANÇAMENTO!`

---

### ENQUANTO (While) — Quando não se sabe quantas repetições

Verifica a condição **antes** de executar. Se a condição já for falsa no início, o bloco **nunca executa**:

```
ENQUANTO <condição> FAÇA
  <bloco de código>
FIM_ENQUANTO
```

#### Exemplo — Solicitar senha até acertar

```
ALGORITMO VerificarSenha
  INICIO
    CONSTANTE SENHA_CORRETA ← "abc123"
    tentativas ← 0

    ESCREVA "Digite a senha: "
    LEIA senha_digitada

    ENQUANTO senha_digitada ≠ SENHA_CORRETA E tentativas < 3 FAÇA
      tentativas ← tentativas + 1
      ESCREVA "Senha incorreta! Tentativa ", tentativas, " de 3."
      ESCREVA "Tente novamente: "
      LEIA senha_digitada
    FIM_ENQUANTO

    SE senha_digitada = SENHA_CORRETA ENTÃO
      ESCREVA "✅ Acesso liberado!"
    SENÃO
      ESCREVA "❌ Conta bloqueada após 3 tentativas."
    FIM_SE
  FIM
```

---

### REPITA / ATÉ (Do-While) — Executa pelo menos uma vez

Verifica a condição **depois** de executar. O bloco executa **pelo menos uma vez**, mesmo se a condição for falsa:

```
REPITA
  <bloco de código>
ATÉ <condição de parada>
```

#### Exemplo — Menu de opções

```
ALGORITMO MenuPrincipal
  INICIO
    REPITA
      ESCREVA "=== MENU ==="
      ESCREVA "1. Nova conta"
      ESCREVA "2. Depositar"
      ESCREVA "3. Sacar"
      ESCREVA "0. Sair"
      ESCREVA "Escolha: "
      LEIA opcao

      ESCOLHA opcao
        CASO 1: criarConta()
        CASO 2: depositar()
        CASO 3: sacar()
        CASO 0: ESCREVA "Até logo! 👋"
        CASO CONTRÁRIO: ESCREVA "Opção inválida!"
      FIM_ESCOLHA

    ATÉ opcao = 0
  FIM
```

---

### Comparando os 3 tipos de loop

```
┌─────────────┬──────────────────────────────────┬─────────────────────────┐
│    Loop     │         Quando usar              │     Característica      │
├─────────────┼──────────────────────────────────┼─────────────────────────┤
│ PARA        │ Número de repetições conhecido   │ Contador automático     │
│ ENQUANTO    │ Repetição baseada em condição    │ Pode não executar       │
│ REPITA/ATÉ  │ Precisa executar ao menos 1 vez  │ Sempre executa 1 vez    │
└─────────────┴──────────────────────────────────┴─────────────────────────┘
```

---

### Controle de Loop: PARE e CONTINUE

```
PARE (break)     → Encerra o loop imediatamente
CONTINUE         → Pula para a próxima iteração
```

#### Exemplo com PARE — Encontrar primeiro número negativo

```
ALGORITMO EncontrarNegativo
  INICIO
    PARA i ← 1 ATÉ 10 FAÇA
      LEIA numero
      SE numero < 0 ENTÃO
        ESCREVA "Primeiro negativo encontrado: ", numero
        PARE   ← sai do loop
      FIM_SE
    FIM_PARA
  FIM
```

#### Exemplo com CONTINUE — Pular números pares

```
ALGORITMO MostrarImpares
  INICIO
    PARA i ← 1 ATÉ 10 FAÇA
      SE i MOD 2 = 0 ENTÃO
        CONTINUE   ← pula para o próximo i
      FIM_SE
      ESCREVA i    ← só chega aqui se i for ímpar
    FIM_PARA
  FIM
```

Saída: `1 3 5 7 9`

---

### ⚠️ Cuidado: Loop Infinito!

Um **loop infinito** é quando a condição de parada nunca é atingida. O programa trava:

```
❌ Loop infinito (bug clássico):
   contador ← 1
   ENQUANTO contador > 0 FAÇA
     ESCREVA contador
     contador ← contador + 1   ← contador sempre cresce, nunca para!
   FIM_ENQUANTO

✅ Correto:
   contador ← 1
   ENQUANTO contador <= 10 FAÇA
     ESCREVA contador
     contador ← contador + 1
   FIM_ENQUANTO
```

> 🛡️ **Boa prática:** Todo loop deve ter uma condição de parada **garantida**. Se usar `ENQUANTO`, certifique-se de que algo dentro do loop vai eventualmente tornar a condição falsa.

---

## Módulo 6 — Vetores e Matrizes

### O que é um Vetor?

Um **vetor** (array unidimensional) é uma coleção de variáveis do **mesmo tipo** armazenadas sequencialmente na memória, acessadas por um **índice**:

```
Vetor: notas[5]

Índice:  [0]   [1]   [2]   [3]   [4]
Valor:   7.5   8.0   6.5   9.0   5.0
         ↑
      notas[0] = 7.5
      notas[2] = 6.5
      notas[4] = 5.0
```

> ⚠️ **Atenção:** A maioria das linguagens começa o índice em **0** (zero), não em 1!

---

### Declarando e Usando Vetores

```
ALGORITMO UsandoVetores
  INICIO
    DECLARE notas[5]: REAL
    DECLARE soma: REAL ← 0

    // Preenchendo o vetor
    PARA i ← 0 ATÉ 4 FAÇA
      ESCREVA "Digite a nota ", (i+1), ": "
      LEIA notas[i]
    FIM_PARA

    // Somando todos os valores
    PARA i ← 0 ATÉ 4 FAÇA
      soma ← soma + notas[i]
    FIM_PARA

    media ← soma / 5
    ESCREVA "Média da turma: ", media
  FIM
```

---

### Operações Comuns em Vetores

#### Encontrar o maior valor

```
ALGORITMO EncontrarMaior
  INICIO
    DECLARE numeros[6] ← [4, 7, 2, 9, 1, 5]
    maior ← numeros[0]   ← assume que o primeiro é o maior

    PARA i ← 1 ATÉ 5 FAÇA
      SE numeros[i] > maior ENTÃO
        maior ← numeros[i]
      FIM_SE
    FIM_PARA

    ESCREVA "Maior valor: ", maior   → 9
  FIM
```

---

#### Contar ocorrências

```
ALGORITMO ContarAprovados
  INICIO
    DECLARE notas[8] ← [7.5, 4.0, 8.5, 3.0, 9.0, 6.0, 2.5, 7.0]
    aprovados ← 0

    PARA i ← 0 ATÉ 7 FAÇA
      SE notas[i] >= 6.0 ENTÃO
        aprovados ← aprovados + 1
      FIM_SE
    FIM_PARA

    ESCREVA "Aprovados: ", aprovados, " de 8"
  FIM
```

---

### Matrizes — Vetores em 2 Dimensões

Uma **matriz** é um vetor de vetores — pense como uma tabela com linhas e colunas:

```
Matriz 3x3 chamada "m":

           col0  col1  col2
  linha0: [  1     2     3  ]
  linha1: [  4     5     6  ]
  linha2: [  7     8     9  ]

  m[0][0] = 1
  m[1][2] = 6
  m[2][1] = 8
```

#### Exemplo — Preenchendo e exibindo uma matriz

```
ALGORITMO MatrizNotas
  INICIO
    DECLARE turma[3][4]: REAL   // 3 alunos, 4 notas cada

    // Preencher
    PARA aluno ← 0 ATÉ 2 FAÇA
      ESCREVA "=== Aluno ", (aluno+1), " ==="
      PARA bimestre ← 0 ATÉ 3 FAÇA
        ESCREVA "  Nota do ", (bimestre+1), "º bimestre: "
        LEIA turma[aluno][bimestre]
      FIM_PARA
    FIM_PARA

    // Calcular e exibir médias
    ESCREVA "=== MÉDIAS ==="
    PARA aluno ← 0 ATÉ 2 FAÇA
      soma ← 0
      PARA bimestre ← 0 ATÉ 3 FAÇA
        soma ← soma + turma[aluno][bimestre]
      FIM_PARA
      ESCREVA "Aluno ", (aluno+1), ": ", soma/4
    FIM_PARA
  FIM
```

---

## Módulo 7 — Funções e Procedimentos

### O que são e por que usar?

**Funções** e **procedimentos** são blocos de código nomeados que podem ser chamados de qualquer parte do programa.

```
SEM funções:                        COM funções:
  calculo1 = a * b / 2              area1 = calcularArea(5, 3)
  calculo2 = c * d / 2              area2 = calcularArea(8, 4)
  calculo3 = e * f / 2              area3 = calcularArea(2, 7)
  ...
```

**Benefícios:**

| Benefício | Descrição |
|---|---|
| **Reutilização** | Escreva uma vez, use em vários lugares |
| **Organização** | Divide o problema em partes menores |
| **Manutenção** | Corrija um bug em um lugar, corrige em todos |
| **Legibilidade** | Código mais fácil de ler e entender |
| **Testabilidade** | Teste cada parte separadamente |

---

### Procedimento — Não retorna valor

```
PROCEDIMENTO exibirSaudacao(nome: TEXTO)
  INICIO
    ESCREVA "============================="
    ESCREVA "  Olá, ", nome, "! 👋"
    ESCREVA "  Bem-vindo ao sistema!"
    ESCREVA "============================="
  FIM

// Chamando o procedimento:
exibirSaudacao("Maria")
exibirSaudacao("João")
```

---

### Função — Retorna um valor

```
FUNÇÃO calcularArea(base: REAL, altura: REAL): REAL
  INICIO
    area ← base * altura / 2
    RETORNE area
  FIM

// Usando a função:
area_triangulo1 ← calcularArea(6, 4)   → 12.0
area_triangulo2 ← calcularArea(3, 8)   → 12.0
ESCREVA "A área é: ", area_triangulo1
```

---

### Parâmetros vs Argumentos

```
FUNÇÃO somar(a: INTEIRO, b: INTEIRO): INTEIRO
         ↑              ↑
    Estes são os PARÂMETROS (definição da função)

resultado ← somar(5, 3)
                  ↑  ↑
             Estes são os ARGUMENTOS (chamada da função)
```

---

### Escopo de Variáveis

**Escopo** define onde uma variável pode ser acessada:

```
DECLARE contador_global ← 0   ← Variável GLOBAL (visível em todo o programa)

FUNÇÃO exemploEscopo()
  INICIO
    DECLARE mensagem_local ← "Olá"   ← Variável LOCAL (só existe dentro desta função)
    contador_global ← contador_global + 1   ← acessa global ✅
    ESCREVA mensagem_local   ← acessa local ✅
  FIM

// Fora da função:
ESCREVA mensagem_local   ← ❌ ERRO! variável local não existe aqui
ESCREVA contador_global  ← ✅ funciona, é global
```

> ⚠️ **Boa prática:** Evite variáveis globais ao máximo. Prefira passar valores como parâmetros — isso torna o código mais previsível e fácil de testar.

---

### Exemplo Completo — Sistema de Cálculo de Salário

```
FUNÇÃO calcularImpostoIR(salario: REAL): REAL
  INICIO
    SE salario <= 1903.98 ENTÃO
      RETORNE 0
    SENÃO SE salario <= 2826.65 ENTÃO
      RETORNE salario * 0.075 - 142.80
    SENÃO SE salario <= 3751.05 ENTÃO
      RETORNE salario * 0.15 - 354.80
    SENÃO SE salario <= 4664.68 ENTÃO
      RETORNE salario * 0.225 - 636.13
    SENÃO
      RETORNE salario * 0.275 - 869.36
    FIM_SE
  FIM

FUNÇÃO calcularSalarioLiquido(salario_bruto: REAL): REAL
  INICIO
    inss ← salario_bruto * 0.11
    ir ← calcularImpostoIR(salario_bruto)
    RETORNE salario_bruto - inss - ir
  FIM

ALGORITMO Principal
  INICIO
    ESCREVA "Salário bruto: "
    LEIA bruto

    liquido ← calcularSalarioLiquido(bruto)

    ESCREVA "Salário bruto:  R$ ", bruto
    ESCREVA "Desconto INSS:  R$ ", bruto * 0.11
    ESCREVA "Desconto IR:    R$ ", calcularImpostoIR(bruto)
    ESCREVA "Salário líquido: R$ ", liquido
  FIM
```

---

## Módulo 8 — Recursão

### O que é Recursão?

**Recursão** é quando uma função **chama a si mesma** para resolver um problema. É como um espelho apontado para outro espelho — mas com uma condição de parada!

```
Função recursiva tem SEMPRE 2 partes:
  1. Caso Base     → Condição de parada (quando parar de chamar)
  2. Caso Recursivo → Chama a si mesma com problema menor
```

---

### Exemplo 1 — Fatorial

O fatorial de n (escrito n!) é:
- `0! = 1`
- `n! = n × (n-1)!`

```
5! = 5 × 4 × 3 × 2 × 1 = 120
```

```
FUNÇÃO fatorial(n: INTEIRO): INTEIRO
  INICIO
    SE n = 0 ENTÃO         ← CASO BASE
      RETORNE 1
    SENÃO                  ← CASO RECURSIVO
      RETORNE n * fatorial(n - 1)
    FIM_SE
  FIM
```

**Rastreando a execução de `fatorial(4)`:**

```
fatorial(4)
  → 4 * fatorial(3)
         → 3 * fatorial(2)
                → 2 * fatorial(1)
                       → 1 * fatorial(0)
                              → retorna 1    ← caso base!
                       → retorna 1 * 1 = 1
                → retorna 2 * 1 = 2
         → retorna 3 * 2 = 6
  → retorna 4 * 6 = 24
```

---

### Exemplo 2 — Fibonacci

A sequência de Fibonacci: `0, 1, 1, 2, 3, 5, 8, 13, 21, 34...`

Cada número é a soma dos dois anteriores.

```
FUNÇÃO fibonacci(n: INTEIRO): INTEIRO
  INICIO
    SE n <= 1 ENTÃO         ← CASOS BASE
      RETORNE n
    SENÃO                   ← CASO RECURSIVO
      RETORNE fibonacci(n-1) + fibonacci(n-2)
    FIM_SE
  FIM

fibonacci(0) = 0
fibonacci(1) = 1
fibonacci(5) = fibonacci(4) + fibonacci(3) = 3 + 2 = 5
fibonacci(10) = 55
```

---

### Recursão vs Iteração

```
Solução ITERATIVA do fatorial:
  FUNÇÃO fatorialIterativo(n: INTEIRO): INTEIRO
    resultado ← 1
    PARA i ← 2 ATÉ n FAÇA
      resultado ← resultado * i
    FIM_PARA
    RETORNE resultado

Solução RECURSIVA do fatorial:
  FUNÇÃO fatorialRecursivo(n: INTEIRO): INTEIRO
    SE n = 0 ENTÃO RETORNE 1
    RETORNE n * fatorialRecursivo(n - 1)
```

| Aspecto | Iterativo | Recursivo |
|---|---|---|
| **Legibilidade** | Às vezes verbosa | Frequentemente elegante |
| **Performance** | Geralmente mais rápido | Pode ser mais lento |
| **Memória** | Usa menos memória | Usa a pilha de chamadas |
| **Quando usar** | Problemas sequenciais | Problemas divididos em subproblemas |

> 🧠 **Regra prática:** Se você consegue pensar no problema como *"este problema é um problema menor do mesmo tipo"*, a recursão pode ser elegante. Caso contrário, prefira iteração.

---

## Módulo 9 — Busca e Ordenação

### Busca Linear (Sequential Search)

Percorre o vetor **do início ao fim** até encontrar o elemento:

```
FUNÇÃO buscaLinear(vetor[], tamanho: INTEIRO, alvo: INTEIRO): INTEIRO
  INICIO
    PARA i ← 0 ATÉ tamanho-1 FAÇA
      SE vetor[i] = alvo ENTÃO
        RETORNE i   ← retorna o índice onde encontrou
      FIM_SE
    FIM_PARA
    RETORNE -1   ← -1 indica "não encontrado"
  FIM
```

**Complexidade:** O(n) — no pior caso, verifica todos os n elementos.

---

### Busca Binária (Binary Search)

Muito mais eficiente, mas **o vetor precisa estar ordenado**. Divide o problema ao meio a cada passo:

```
FUNÇÃO buscaBinaria(vetor[], alvo: INTEIRO): INTEIRO
  INICIO
    inicio ← 0
    fim ← tamanho - 1

    ENQUANTO inicio <= fim FAÇA
      meio ← (inicio + fim) DIV 2

      SE vetor[meio] = alvo ENTÃO
        RETORNE meio          ← encontrou!
      SENÃO SE vetor[meio] < alvo ENTÃO
        inicio ← meio + 1    ← busca na metade direita
      SENÃO
        fim ← meio - 1       ← busca na metade esquerda
      FIM_SE
    FIM_ENQUANTO

    RETORNE -1   ← não encontrado
  FIM
```

**Visualizando a busca binária do número 7 no vetor `[1,3,5,7,9,11,13]`:**

```
[1, 3, 5, 7, 9, 11, 13]
 ↑           ↑        ↑
início       meio     fim

meio = 9. Alvo (7) < 9? Busca na metade ESQUERDA.

[1, 3, 5, 7]
 ↑     ↑   ↑
início meio fim

meio = 3. Alvo (7) > 3? Busca na metade DIREITA.

[5, 7]
 ↑  ↑↑
ini mei fim

meio = 5. Alvo (7) > 5? Busca na DIREITA.

[7]
 ↑
meio = 7. ENCONTROU! ✅
```

**Complexidade:** O(log n) — para 1 bilhão de elementos, faz no máximo 30 comparações!

| Tamanho | Busca Linear | Busca Binária |
|---:|---:|---:|
| 10 | 10 passos | 4 passos |
| 1.000 | 1.000 passos | 10 passos |
| 1.000.000 | 1.000.000 passos | 20 passos |
| 1.000.000.000 | 1 bilhão de passos | 30 passos |

---

### Ordenação por Bolha (Bubble Sort)

O mais simples (mas não o mais eficiente). Compara pares adjacentes e os troca se estiverem fora de ordem:

```
FUNÇÃO bubbleSort(vetor[], n: INTEIRO)
  INICIO
    PARA i ← 0 ATÉ n-2 FAÇA
      PARA j ← 0 ATÉ n-2-i FAÇA
        SE vetor[j] > vetor[j+1] ENTÃO
          // Troca os elementos
          temp ← vetor[j]
          vetor[j] ← vetor[j+1]
          vetor[j+1] ← temp
        FIM_SE
      FIM_PARA
    FIM_PARA
  FIM
```

**Visualizando `[5, 3, 8, 1, 2]`:**

```
Passo 1: [5,3,8,1,2] → [3,5,8,1,2] → [3,5,8,1,2] → [3,5,1,8,2] → [3,5,1,2,8]
Passo 2: [3,5,1,2,8] → [3,5,1,2,8] → [3,1,5,2,8] → [3,1,2,5,8] → [3,1,2,5,8]
Passo 3: [3,1,2,5,8] → [1,3,2,5,8] → [1,2,3,5,8] → ...
Passo 4: [1,2,3,5,8] → [1,2,3,5,8] ✅ Ordenado!
```

---

## Módulo 10 — Introdução a Estruturas de Dados

### Pilha (Stack) — LIFO

**LIFO = Last In, First Out** (último a entrar, primeiro a sair)

Pense em uma pilha de pratos: você coloca em cima e retira de cima.

```
Operações:
  EMPILHAR (push)  → adiciona no topo
  DESEMPILHAR (pop) → remove do topo
  TOPO (peek)      → vê o topo sem remover

Visualização:
  Empilha 3:  [3]
  Empilha 7:  [3, 7]     ← topo é 7
  Empilha 1:  [3, 7, 1]  ← topo é 1
  Pop:        [3, 7]     ← retorna 1
  Pop:        [3]        ← retorna 7
```

**Onde é usado:** Desfazer (Ctrl+Z), navegação no histórico, chamadas de funções, expressões matemáticas.

---

### Fila (Queue) — FIFO

**FIFO = First In, First Out** (primeiro a entrar, primeiro a sair)

Como uma fila de banco: quem chegou primeiro é atendido primeiro.

```
Operações:
  ENFILEIRAR (enqueue) → adiciona no final
  DESENFILEIRAR (dequeue) → remove do início

Visualização:
  Enfileira "Ana":   [Ana]
  Enfileira "Bob":   [Ana, Bob]
  Enfileira "Cia":   [Ana, Bob, Cia]
  Dequeue:           [Bob, Cia]      ← retorna "Ana"
  Dequeue:           [Cia]           ← retorna "Bob"
```

**Onde é usado:** Filas de impressão, requisições de servidor, processamento em lote.

---

### Comparativo de Estruturas

| Estrutura | Ordem de saída | Analogia | Uso típico |
|---|---|---|---|
| **Array/Vetor** | Por índice | Rua com casas numeradas | Coleções com acesso aleatório |
| **Pilha** | LIFO | Pilha de pratos | Undo/Redo, recursão |
| **Fila** | FIFO | Fila de banco | Processamento em ordem |
| **Lista Ligada** | Sequencial | Trem com vagões | Inserções/remoções frequentes |

---

## Módulo 11 — Depuração e Boas Práticas

### O que é Depuração (Debugging)?

**Debugging** é o processo de encontrar e corrigir erros (bugs) no código.

### Os 3 Tipos de Erros

#### 1. Erro de Sintaxe

O código foi escrito de forma **gramaticalmente incorreta**. O computador nem consegue ler o programa:

```
❌ Erro de sintaxe:
   SE x > 0    ← faltou o ENTÃO
     ESCREVA x
   FIM_SE

✅ Correto:
   SE x > 0 ENTÃO
     ESCREVA x
   FIM_SE
```

---

#### 2. Erro em Tempo de Execução (Runtime Error)

O código está sintaticamente correto, mas **trava durante a execução**:

```
❌ Erro de runtime:
   LEIA divisor
   resultado ← 100 / divisor   ← e se o usuário digitar 0?

✅ Correto (com tratamento):
   LEIA divisor
   SE divisor = 0 ENTÃO
     ESCREVA "Erro: não é possível dividir por zero!"
   SENÃO
     resultado ← 100 / divisor
     ESCREVA resultado
   FIM_SE
```

---

#### 3. Erro de Lógica (Semantic Error)

O código roda sem travar, mas **produz resultados errados**:

```
❌ Erro de lógica (mais traiçoeiro!):
   // Calcular média de 3 notas
   media ← nota1 + nota2 + nota3 / 3   ← divisão só ocorre em nota3!

   Com notas 7, 8 e 9: resultado = 7 + 8 + 3 = 18 (ERRADO!)

✅ Correto:
   media ← (nota1 + nota2 + nota3) / 3

   Com notas 7, 8 e 9: resultado = 24 / 3 = 8 (CORRETO!)
```

---

### Técnicas de Depuração

#### Trace Table (Rastreamento Manual)

Simule a execução do código passo a passo, anotando os valores das variáveis:

```
ALGORITMO ExemploPara
  i ← 1
  soma ← 0
  ENQUANTO i <= 5 FAÇA
    soma ← soma + i
    i ← i + 1
  FIM_ENQUANTO
  ESCREVA soma
```

| Passo | `i` | `soma` | Condição `i <= 5` |
|:---:|:---:|:---:|:---:|
| Início | 1 | 0 | - |
| 1 | 2 | 1 | ✅ V |
| 2 | 3 | 3 | ✅ V |
| 3 | 4 | 6 | ✅ V |
| 4 | 5 | 10 | ✅ V |
| 5 | 6 | 15 | ✅ V |
| 6 | 6 | 15 | ❌ F → sai do loop |

Saída: `15` ✅

---

### Boas Práticas de Programação

#### 1. Nomes descritivos

```
❌ Ruim:          ✅ Bom:
  d = 30            dias_no_mes = 30
  c = 0             contagem_erros = 0
  f(x, y)           calcularDistancia(ponto_origem, ponto_destino)
```

---

#### 2. Uma função, uma responsabilidade

```
❌ Função faz muita coisa:
  FUNÇÃO processarPedido(pedido)
    validar_dados()
    calcular_preco()
    aplicar_desconto()
    gerar_nota_fiscal()
    enviar_email()
    atualizar_estoque()

✅ Responsabilidades separadas:
  validarPedido(pedido)
  calcularTotal(pedido)
  gerarNotaFiscal(pedido)
  notificarCliente(pedido)
```

---

#### 3. Comentários que explicam o "porquê", não o "o quê"

```
❌ Comentário inútil (explica o óbvio):
  i ← i + 1   // incrementa i em 1

✅ Comentário útil (explica a razão):
  i ← i + 1   // pula o elemento delimitador que não deve ser processado

❌ Código sem comentário necessário:
  x ← n * 0.0125   // o que diabos é 0.0125?

✅ Com explicação:
  CONSTANTE TAXA_MENSAL ← 0.0125   // 1.25% ao mês (juros do produto)
  juros ← principal * TAXA_MENSAL
```

---

#### 4. Evitar números mágicos

```
❌ Número mágico (o que é 168?):
  SE horas_trabalhadas > 168 ENTÃO
    pagar_hora_extra()

✅ Constante com nome:
  CONSTANTE HORAS_MENSAIS_NORMAIS ← 168   // 44h/semana × 4.33 semanas
  SE horas_trabalhadas > HORAS_MENSAIS_NORMAIS ENTÃO
    pagar_hora_extra()
```

---

## 📝 Exercícios Resolvidos por Nível

### 🟢 Nível 1 — Iniciante

#### Exercício 1.1 — Calculadora de IMC

**Problema:** Dado o peso e a altura de uma pessoa, calcule o IMC e classifique.

```
ALGORITMO CalcularIMC
  INICIO
    ESCREVA "Peso (kg): "
    LEIA peso
    ESCREVA "Altura (m): "
    LEIA altura

    imc ← peso / (altura * altura)

    ESCREVA "Seu IMC é: ", imc

    SE imc < 18.5 ENTÃO
      ESCREVA "Classificação: Abaixo do peso 🔵"
    SENÃO SE imc < 25.0 ENTÃO
      ESCREVA "Classificação: Peso normal ✅"
    SENÃO SE imc < 30.0 ENTÃO
      ESCREVA "Classificação: Sobrepeso 🟡"
    SENÃO SE imc < 35.0 ENTÃO
      ESCREVA "Classificação: Obesidade Grau I 🟠"
    SENÃO SE imc < 40.0 ENTÃO
      ESCREVA "Classificação: Obesidade Grau II 🔴"
    SENÃO
      ESCREVA "Classificação: Obesidade Grau III (Mórbida) ⛔"
    FIM_SE
  FIM
```

---

#### Exercício 1.2 — Tabuada Completa

**Problema:** Mostre a tabuada de um número digitado pelo usuário (de 1 a 10).

```
ALGORITMO Tabuada
  INICIO
    ESCREVA "Digite um número: "
    LEIA numero
    ESCREVA "=== Tabuada do ", numero, " ==="
    PARA i ← 1 ATÉ 10 FAÇA
      ESCREVA numero, " × ", i, " = ", numero * i
    FIM_PARA
  FIM
```

---

### 🟡 Nível 2 — Intermediário

#### Exercício 2.1 — Verificador de Número Primo

**Problema:** Determine se um número é primo ou não.

```
FUNÇÃO ehPrimo(n: INTEIRO): BOOLEANO
  INICIO
    SE n < 2 ENTÃO
      RETORNE FALSO
    FIM_SE

    PARA i ← 2 ATÉ raiz(n) FAÇA
      SE n MOD i = 0 ENTÃO
        RETORNE FALSO   ← encontrou divisor, não é primo
      FIM_SE
    FIM_PARA

    RETORNE VERDADEIRO   ← nenhum divisor encontrado, é primo!
  FIM

ALGORITMO Principal
  INICIO
    ESCREVA "Digite um número: "
    LEIA numero

    SE ehPrimo(numero) ENTÃO
      ESCREVA numero, " é primo! ✅"
    SENÃO
      ESCREVA numero, " não é primo ❌"
    FIM_SE
  FIM
```

**Teste:**
- `ehPrimo(7)` → Testa 2, 3 (até √7 ≈ 2.6). Nenhum divide. → `VERDADEIRO` ✅
- `ehPrimo(12)` → Testa 2. 12 MOD 2 = 0. → `FALSO` ❌

---

#### Exercício 2.2 — Calculadora de Média com Vetor

**Problema:** Leia 5 notas, calcule e exiba média, maior nota e menor nota.

```
ALGORITMO EstatisticasNotas
  INICIO
    DECLARE notas[5]: REAL

    PARA i ← 0 ATÉ 4 FAÇA
      ESCREVA "Nota ", (i+1), ": "
      LEIA notas[i]
    FIM_PARA

    soma ← 0
    maior ← notas[0]
    menor ← notas[0]

    PARA i ← 0 ATÉ 4 FAÇA
      soma ← soma + notas[i]
      SE notas[i] > maior ENTÃO maior ← notas[i] FIM_SE
      SE notas[i] < menor ENTÃO menor ← notas[i] FIM_SE
    FIM_PARA

    ESCREVA "Média:  ", soma / 5
    ESCREVA "Maior:  ", maior
    ESCREVA "Menor:  ", menor
  FIM
```

---

### 🔴 Nível 3 — Avançado

#### Exercício 3.1 — Palíndromo

**Problema:** Verifique se uma palavra é palíndromo (lê-se igual de frente e de trás).

```
FUNÇÃO ehPalindromo(texto: TEXTO): BOOLEANO
  INICIO
    texto ← paraMinusculo(texto)
    n ← tamanho(texto)

    PARA i ← 0 ATÉ (n DIV 2) - 1 FAÇA
      SE texto[i] ≠ texto[n - 1 - i] ENTÃO
        RETORNE FALSO
      FIM_SE
    FIM_PARA

    RETORNE VERDADEIRO
  FIM

ALGORITMO Principal
  INICIO
    LEIA palavra
    SE ehPalindromo(palavra) ENTÃO
      ESCREVA "✅ '", palavra, "' é um palíndromo!"
    SENÃO
      ESCREVA "❌ '", palavra, "' não é palíndromo."
    FIM_SE
  FIM
```

**Teste com "arara":**
```
n = 5
i=0: texto[0]='a' = texto[4]='a' ✅
i=1: texto[1]='r' = texto[3]='r' ✅
i=2: (5 DIV 2)-1 = 1, para aqui

RETORNE VERDADEIRO ✅
```

---

#### Exercício 3.2 — Torre de Hanói (Recursão)

**Problema clássico:** Mova n discos do pino A para o pino C, usando B como auxiliar. Regra: nunca coloque um disco maior sobre um menor.

```
PROCEDIMENTO hanoi(n: INTEIRO, origem: TEXTO, destino: TEXTO, auxiliar: TEXTO)
  INICIO
    SE n = 1 ENTÃO
      ESCREVA "Mova disco 1 de ", origem, " para ", destino
      RETORNE
    FIM_SE

    hanoi(n-1, origem, auxiliar, destino)   ← move n-1 discos para auxiliar
    ESCREVA "Mova disco ", n, " de ", origem, " para ", destino
    hanoi(n-1, auxiliar, destino, origem)   ← move n-1 discos do auxiliar para destino
  FIM

ALGORITMO Principal
  INICIO
    LEIA num_discos
    hanoi(num_discos, "A", "C", "B")
  FIM
```

**Para `hanoi(3, "A", "C", "B")`:**
```
Mova disco 1 de A para C
Mova disco 2 de A para B
Mova disco 1 de C para B
Mova disco 3 de A para C
Mova disco 1 de B para A
Mova disco 2 de B para C
Mova disco 1 de A para C
```

Número de movimentos para n discos: **2ⁿ - 1**
- 3 discos: 7 movimentos
- 10 discos: 1.023 movimentos
- 64 discos: 18.446.744.073.709.551.615 movimentos 😱

---

## 🚀 Cheatsheet de Pseudocódigo

```
=== ESTRUTURA BÁSICA ===
ALGORITMO NomeDoAlgoritmo
  INICIO
    // seu código aqui
  FIM

=== VARIÁVEIS ===
DECLARE nome: tipo
nome ← valor
CONSTANTE NOME ← valor

=== TIPOS ===
INTEIRO  REAL  TEXTO  BOOLEANO
VERDADEIRO  FALSO

=== ENTRADA/SAÍDA ===
LEIA variavel
ESCREVA "mensagem", variavel

=== DECISÃO ===
SE condição ENTÃO
  ...
SENÃO SE condição ENTÃO
  ...
SENÃO
  ...
FIM_SE

ESCOLHA variavel
  CASO valor1: ...
  CASO valor2: ...
  CASO CONTRÁRIO: ...
FIM_ESCOLHA

=== REPETIÇÃO ===
PARA i ← inicio ATÉ fim [PASSO n] FAÇA
  ...
FIM_PARA

ENQUANTO condição FAÇA
  ...
FIM_ENQUANTO

REPITA
  ...
ATÉ condição

=== FUNÇÕES ===
FUNÇÃO nome(param: tipo): tipo_retorno
  INICIO
    ...
    RETORNE valor
  FIM

PROCEDIMENTO nome(param: tipo)
  INICIO
    ...
  FIM

=== VETORES ===
DECLARE vetor[tamanho]: tipo
vetor[indice] ← valor

=== OPERADORES ===
+ - * /         Aritméticos
DIV MOD ^       Divisão int, resto, potência
= ≠ > < ≥ ≤    Relacionais
E OU NÃO        Lógicos

=== CONTROLE DE LOOP ===
PARE            → sai do loop (break)
CONTINUE        → próxima iteração
```

---

## 🎓 Próximos Passos

Parabéns! Você concluiu o curso de lógica de programação. Agora você tem a base para aprender qualquer linguagem. Veja o caminho recomendado:

```
     VOCÊ ESTÁ AQUI
           │
           ▼
   ┌───────────────┐
   │ Lógica de     │ ← Você está saindo daqui! ✅
   │ Programação   │
   └───────┬───────┘
           │
           ▼
   ┌───────────────┐
   │ Escolha uma   │ Python (recomendado para iniciantes)
   │ Linguagem     │ JavaScript (web)
   │               │ Java / C# (corporativo)
   └───────┬───────┘ C / C++ (sistemas/baixo nível)
           │
           ▼
   ┌───────────────┐
   │ Estruturas de │ Listas, Árvores, Grafos,
   │ Dados Avançadas│ Tabelas Hash, Heaps
   └───────┬───────┘
           │
           ▼
   ┌───────────────┐
   │ Algoritmos    │ Complexidade (Big O),
   │ Avançados     │ Programação Dinâmica,
   └───────┬───────┘ Algoritmos Gulosos
           │
           ▼
   ┌───────────────┐
   │ Especializações│ Backend, Frontend,
   │ (escolha a    │ Data Science, IA,
   │  sua!)        │ Segurança, Mobile...
   └───────────────┘
```

---

### 📚 Recursos Recomendados

| Recurso | Tipo | Link |
|---|---|---|
| **CS50** (Harvard) | Curso gratuito | [cs50.harvard.edu](https://cs50.harvard.edu) |
| **Visualgo** | Visualizador de algoritmos | [visualgo.net](https://visualgo.net) |
| **Khan Academy - Programação** | Curso gratuito | [khanacademy.org](https://www.khanacademy.org/computing) |
| **LeetCode** | Prática de algoritmos | [leetcode.com](https://leetcode.com) |
| **The Coding Train** | YouTube / projetos | [thecodingtrain.com](https://thecodingtrain.com) |

---

### 🏁 Desafios para continuar praticando

- [ ] Implemente todos os algoritmos deste curso em uma linguagem real (Python, JS...)
- [ ] Resolva 30 problemas no LeetCode (fáceis primeiro!)
- [ ] Implemente um jogo simples: Pedra, Papel, Tesoura
- [ ] Crie um sistema de cadastro com menu (usando arrays e funções)
- [ ] Implemente os algoritmos de ordenação: Selection Sort, Insertion Sort
- [ ] Estude Complexidade de Algoritmos (Notação Big O)

---

<div align="center">

**Feito com ❤️, pseudocódigo e muita lógica**

*"Todo mundo neste país deveria aprender a programar um computador,*
*porque isso te ensina a pensar."* — Steve Jobs

⭐ Se este curso te ajudou, dê uma estrela no repositório!

</div>
