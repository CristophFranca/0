# 🧠 Curso Completo de Lógica de Programação

> **Do zero ao avançado** — aprenda a pensar como um programador com exemplos em **Python real**, que você pode copiar e executar agora mesmo. Python foi escolhido por ter sintaxe próxima ao português e ser a linguagem mais usada para ensino no mundo.

> 💡 **Como usar este curso:** Cada bloco de código pode ser executado em [python.org/shell](https://www.python.org/shell/) online ou instalando Python em seu computador. Experimente modificar os exemplos — é a melhor forma de aprender!

---

## 📋 Índice

1. [O que é Lógica de Programação?](#-o-que-é-lógica-de-programação)
2. [Como os Computadores Pensam](#-como-os-computadores-pensam)
3. [Módulo 1 — Algoritmos](#módulo-1--algoritmos)
4. [Módulo 2 — Variáveis e Tipos de Dados](#módulo-2--variáveis-e-tipos-de-dados)
5. [Módulo 3 — Operadores](#módulo-3--operadores)
6. [Módulo 4 — Estruturas de Decisão](#módulo-4--estruturas-de-decisão)
7. [Módulo 5 — Estruturas de Repetição (Loops)](#módulo-5--estruturas-de-repetição-loops)
8. [Módulo 6 — Listas e Matrizes](#módulo-6--listas-e-matrizes)
9. [Módulo 7 — Funções](#módulo-7--funções)
10. [Módulo 8 — Recursão](#módulo-8--recursão)
11. [Módulo 9 — Busca e Ordenação](#módulo-9--busca-e-ordenação)
12. [Módulo 10 — Introdução a Estruturas de Dados](#módulo-10--introdução-a-estruturas-de-dados)
13. [Módulo 11 — Depuração e Boas Práticas](#módulo-11--depuração-e-boas-práticas)
14. [Exercícios Resolvidos por Nível](#-exercícios-resolvidos-por-nível)
15. [Cheatsheet Python](#-cheatsheet-python)
16. [Próximos Passos](#-próximos-passos)

---

## 🤔 O que é Lógica de Programação?

**Lógica de programação** é a habilidade de organizar o pensamento de forma estruturada para resolver problemas por meio de passos lógicos, sequenciais e precisos — exatamente como um computador precisa que você faça.

> **Analogia perfeita:** Imagine que você está escrevendo uma receita de bolo para um robô extremamente literal. Se você escrever *"adicione sal a gosto"*, ele não sabe o que fazer. Você precisa dizer: *"adicione exatamente 5 gramas de sal"*. Esse nível de precisão é o que a programação exige.

### Por que aprender lógica antes de tudo?

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

Pense na memória RAM como uma **rua com casas numeradas**. Cada casa tem um endereço e pode guardar um valor:

```
Endereço:  [0x001] [0x002] [0x003] [0x004]
Valor:        42    "Ana"   True    3.14
Nome:       [idade] [nome] [ativo]  [pi]
```

Quando você cria uma **variável**, está reservando uma dessas "casas" na memória para guardar um dado.

---

## Módulo 1 — Algoritmos

### O que é um Algoritmo?

Um **algoritmo** é uma sequência finita de instruções bem definidas para resolver um problema. Todo programa é um algoritmo.

### As 3 características obrigatórias

| Característica | Significa | Exemplo ruim | Exemplo bom |
|---|---|---|---|
| **Finito** | Deve terminar em algum momento | Contar até infinito | Contar até 100 |
| **Definido** | Cada passo deve ser claro e sem ambiguidade | "Adicione sal a gosto" | "Adicione 5g de sal" |
| **Eficaz** | Cada passo deve ser executável | "Divida por zero" | "Divida por 2" |

---

### Formas de Representar Algoritmos

#### 1. Descrição Narrativa

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

#### 2. Fluxograma

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
         │   Água já filtrou?       │
         └──────┬──────────┬────────┘
               SIM        NÃO
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

| Forma | Representa |
|---|---|
| Oval (arredondado) | Início e fim do programa |
| Retângulo | Instrução ou ação |
| Losango | Decisão (sim/não) |
| Paralelogramo | Entrada/Saída de dados |
| Seta | Direção do fluxo |

---

#### 3. Código Python

A versão executável — o que vamos usar neste curso:

```python
def fazer_cafe():
    fervar_agua()
    adicionar_po(colheres=2)
    despejar_agua_no_coador()

    while not agua_filtrou():
        aguardar(minutos=1)

    servir_na_xicara()
    print("Café pronto! ☕")
```

---

### Exemplo: Algoritmo para Atravessar a Rua

**Narrativa:**
```
1. Chegue na calçada
2. Enquanto houver carro, espere
3. Quando não houver carro, atravesse
```

**Em Python:**

```python
def atravessar_rua():
    while tem_carro_vindo():
        esperar()

    atravessar()
    print("Chegou com segurança! ✅")
```

---

## Módulo 2 — Variáveis e Tipos de Dados

### O que é uma Variável?

Uma **variável** é um espaço na memória com um **nome** e um **valor** que pode mudar ao longo do programa.

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

### Criando Variáveis em Python

Em Python não é preciso declarar o tipo — ele é detectado automaticamente:

```python
# Criando variáveis (basta nomear e atribuir com =)
idade = 25
nome = "Carlos"
salario = 3500.50
aprovado = True

print(idade)    # 25
print(nome)     # Carlos
print(salario)  # 3500.5
print(aprovado) # True
```

> ⚠️ **Importante:** O sinal `=` em programação significa **atribuição** (guardar um valor). Para comparar igualdade, usa-se `==`. São coisas completamente diferentes!

```python
x = 10      # atribuição: guarda 10 em x
x == 10     # comparação: pergunta "x é igual a 10?"  → True
x == 5      # comparação: pergunta "x é igual a 5?"   → False
```

---

### Tipos de Dados Fundamentais

#### 🔢 int — Números Inteiros

Números **sem casas decimais**, positivos ou negativos:

```python
idade = 25
temperatura = -10
quantidade = 0
ano = 2024

print(type(idade))  # <class 'int'>

# Operações específicas de inteiros:
print(10 // 3)   # 3   → divisão inteira (descarta o resto)
print(10 % 3)    # 1   → resto da divisão (módulo)
print(2 ** 8)    # 256 → potência
```

---

#### 🔣 float — Números Decimais

Números **com casas decimais**:

```python
preco = 29.99
altura = 1.75
pi = 3.14159
desconto = -5.5

print(type(preco))  # <class 'float'>
```

> ⚠️ **Armadilha clássica — imprecisão de ponto flutuante:**
```python
print(0.1 + 0.2)         # 0.30000000000000004  ← não é exatamente 0.3!
print(0.1 + 0.2 == 0.3)  # False ← cuidado!

# Solução: compare com uma margem de tolerância
epsilon = 0.0001
resultado = abs(0.1 + 0.2 - 0.3) < epsilon
print(resultado)  # True ✅
```

---

#### 📝 str — Texto (String)

Sequência de caracteres, entre aspas simples ou duplas:

```python
nome = "Ana"
mensagem = 'Olá, mundo!'
cpf = "123.456.789-00"   # CPF é str, não int!
vazio = ""               # string vazia

print(type(nome))  # <class 'str'>

# Operações com strings:
print("Olá" + ", " + "mundo!")  # "Olá, mundo!"  → concatenação
print("Ha" * 3)                 # "HaHaHa"        → repetição
print(len("Python"))            # 6               → tamanho
print("python".upper())         # "PYTHON"        → maiúsculas
print("  espaços  ".strip())    # "espaços"       → remove bordas

# f-strings (a forma mais moderna de formatar):
nome = "Ana"
idade = 25
print(f"Olá, {nome}! Você tem {idade} anos.")
# "Olá, Ana! Você tem 25 anos."
```

> 💡 **Por que CPF é `str` e não `int`?** Porque você não faz contas com CPF. E zeros à esquerda (como `007.000.000-01`) seriam perdidos se fosse número.

---

#### ✅ bool — Booleano

Só pode ser `True` ou `False`:

```python
esta_chovendo = True
tem_desconto = False
usuario_logado = True

print(type(esta_chovendo))  # <class 'bool'>

# Booleans surgem de comparações:
print(10 > 5)    # True
print(3 == 7)    # False
print(5 != 5)    # False
print("a" in "banana")  # True
```

---

#### 📊 Resumo dos Tipos

| Tipo Python | Nome | Exemplos | Uso |
|---|---|---|---|
| `int` | Inteiro | `1`, `42`, `-7`, `0` | Contadores, idades, IDs |
| `float` | Decimal | `3.14`, `-0.5`, `100.0` | Preços, médias, medidas |
| `str` | Texto | `"Ana"`, `"CPF"`, `""` | Nomes, mensagens, códigos |
| `bool` | Booleano | `True`, `False` | Flags, condições, status |

```python
# Verificando o tipo de qualquer valor:
print(type(42))       # <class 'int'>
print(type(3.14))     # <class 'float'>
print(type("olá"))    # <class 'str'>
print(type(True))     # <class 'bool'>
```

---

### Constantes

Python não tem constantes nativas. Por **convenção**, variáveis em MAIÚSCULAS indicam que não devem ser modificadas:

```python
PI = 3.14159265
VELOCIDADE_LUZ = 299792458
MAX_TENTATIVAS = 3
TAXA_MENSAL = 0.0125  # 1.25% ao mês
```

---

### Conversão Entre Tipos

```python
# str → int / float
numero = int("42")        # 42
preco = float("29.99")    # 29.99

# int / float → str
texto = str(100)          # "100"
texto = str(3.14)         # "3.14"

# float → int (TRUNCA — não arredonda!)
inteiro = int(9.9)        # 9  ← não é 10!
arredondado = round(9.9)  # 10 ← isso sim arredonda

# ⚠️ input() sempre retorna str — converta!
# idade = input("Idade: ")      → "25" (string)
# idade = int(input("Idade: ")) → 25 (int)
```

---

### Boas Práticas para Nomear Variáveis

Python usa `snake_case` (palavras em minúsculo separadas por `_`):

| ✅ Bom | ❌ Ruim | Por quê |
|---|---|---|
| `idade_usuario` | `x` | Descritivo vs vago |
| `total_vendas` | `tv` | Claro vs abreviação confusa |
| `esta_ativo` | `flag1` | Indica booleano vs genérico |
| `preco_produto` | `PrecoProduto` | Convenção Python (não Java) |
| `MAX_TENTATIVAS` | `maxtent` | Constante clara vs abreviação |

---

## Módulo 3 — Operadores

### Operadores Aritméticos

```python
a, b = 10, 3

print(a + b)   # 13     → adição
print(a - b)   # 7      → subtração
print(a * b)   # 30     → multiplicação
print(a / b)   # 3.333  → divisão real (sempre retorna float)
print(a // b)  # 3      → divisão inteira (descarta decimais)
print(a % b)   # 1      → módulo (resto da divisão)
print(a ** b)  # 1000   → potência (10³)
```

#### O poder do % (módulo)

O operador `%` é um dos mais úteis em programação:

```python
# Verificar se é par ou ímpar
print(8 % 2 == 0)   # True  → par
print(7 % 2 == 0)   # False → ímpar

# Verificar se é múltiplo
print(15 % 5 == 0)  # True  → múltiplo de 5
print(17 % 5 == 0)  # False → não é múltiplo

# Obter último dígito de um número
print(2847 % 10)    # 7 → último dígito

# Verificar se o ano é bissexto
ano = 2024
bissexto = (ano % 4 == 0 and ano % 100 != 0) or (ano % 400 == 0)
print(f"{ano} é bissexto: {bissexto}")  # 2024 é bissexto: True
```

---

### Operadores Relacionais (Comparação)

Sempre retornam `True` ou `False`:

```python
print(5 == 5)   # True  → igual
print(5 != 3)   # True  → diferente
print(8 > 10)   # False → maior que
print(3 < 7)    # True  → menor que
print(5 >= 5)   # True  → maior ou igual
print(4 <= 3)   # False → menor ou igual
```

---

### Operadores Lógicos

```python
# and → True SOMENTE se os DOIS forem True
print(True and True)    # True
print(True and False)   # False
print(False and False)  # False

# or → True se PELO MENOS UM for True
print(True or False)    # True
print(False or False)   # False

# not → INVERTE o valor
print(not True)         # False
print(not False)        # True
```

#### Tabelas-Verdade

**`and` — "exigente" (precisa dos dois):**

| A | B | A `and` B |
|:---:|:---:|:---:|
| True | True | ✅ True |
| True | False | ❌ False |
| False | True | ❌ False |
| False | False | ❌ False |

**`or` — "generoso" (basta um):**

| A | B | A `or` B |
|:---:|:---:|:---:|
| True | True | ✅ True |
| True | False | ✅ True |
| False | True | ✅ True |
| False | False | ❌ False |

---

#### Exemplo prático combinando operadores

```python
# Sistema de verificação de acesso
usuario = "admin"
senha = "1234"
esta_banido = False

acesso_valido = (usuario == "admin" and senha == "1234")

if acesso_valido and not esta_banido:
    print("Acesso liberado! ✅")
elif esta_banido:
    print("Usuário banido. ❌")
else:
    print("Usuário ou senha incorretos. ❌")
```

---

### Precedência de Operadores

```python
# Assim como na matemática, há uma ordem de execução:
# 1. ()          → parênteses (sempre primeiro!)
# 2. **          → potência
# 3. * / // %    → multiplicação e divisão
# 4. + -         → adição e subtração
# 5. == != > <   → comparações
# 6. not         → negação lógica
# 7. and         → e lógico
# 8. or          → ou lógico

print(2 + 3 * 4)     # 14  (não 20! * vem antes de +)
print((2 + 3) * 4)   # 20  (parênteses forçam a ordem)
print(2 ** 3 + 1)    # 9   (potência antes de adição: 8 + 1)

# Dica de ouro: quando tiver dúvida, use parênteses!
pode_entrar = (idade >= 18) and (tem_ingresso or eh_convidado)
```

---

## Módulo 4 — Estruturas de Decisão

### if / elif / else

A estrutura mais fundamental da programação — permite que o programa escolha caminhos diferentes:

```python
if condição:
    # executa se condição for True
elif outra_condição:
    # executa se a segunda condição for True
else:
    # executa se nenhuma condição anterior for True
```

> ⚠️ **Atenção à indentação!** Python usa **espaços** para definir blocos — não usa `{}` como outras linguagens!

```python
# ✅ Correto — 4 espaços de indentação
if True:
    print("dentro do if")

# ❌ IndentationError — sem indentação
if True:
print("vai dar erro!")
```

---

#### Exemplo 1 — Verificar maioridade

```python
idade = int(input("Qual é a sua idade? "))

if idade >= 18:
    print("Você é maior de idade. ✅")
    print("Pode entrar no site.")
else:
    print("Você é menor de idade. ❌")
    print("Acesso negado.")
```

**Simulando a execução:**
```
Entrada: 25  →  25 >= 18? True   →  "Você é maior de idade. ✅"
Entrada: 15  →  15 >= 18? False  →  "Você é menor de idade. ❌"
```

---

#### Exemplo 2 — Classificar nota com elif encadeado

```python
nota = float(input("Digite a nota (0-10): "))

if nota >= 9:
    resultado = "🏆 Excelente!"
elif nota >= 7:
    resultado = "✅ Aprovado"
elif nota >= 5:
    resultado = "⚠️ Recuperação"
else:
    resultado = "❌ Reprovado"

print(f"Resultado: {resultado}")
```

**Tabela de resultados:**

| Nota | Resultado |
|---|---|
| 9.5 | 🏆 Excelente! |
| 8.0 | ✅ Aprovado |
| 6.0 | ⚠️ Recuperação |
| 3.0 | ❌ Reprovado |

---

#### if sem else

Quando você só quer agir se a condição for verdadeira:

```python
estoque = 2

if estoque < 5:
    print("⚠️ Estoque baixo! Fazer pedido de reposição.")

# O programa continua normalmente daqui
print("Verificação concluída.")
```

---

### match / case — Python 3.10+

Equivalente ao `switch/case` de outras linguagens. Ideal quando você compara um valor com várias opções fixas:

```python
dia = int(input("Número do dia (1-7): "))

match dia:
    case 1:
        print("Domingo 😴")
    case 2:
        print("Segunda-feira 😰")
    case 3:
        print("Terça-feira 💪")
    case 4:
        print("Quarta-feira 🐪")
    case 5:
        print("Quinta-feira 🤔")
    case 6:
        print("Sexta-feira 🎉")
    case 7:
        print("Sábado 🥳")
    case _:           # _ é o "default" — captura qualquer outro valor
        print("Dia inválido ❌")
```

> 💡 **Use `match/case` quando:** comparando um valor com muitas opções fixas.
> **Use `if/elif/else` quando:** a condição envolve intervalos ou expressões complexas.

---

### Operador Ternário

Atalho para `if/else` simples escrito em uma linha:

```python
# Sintaxe: valor_se_true if condição else valor_se_false

idade = 20
status = "adulto" if idade >= 18 else "menor"
print(status)  # "adulto"

# Outros exemplos práticos:
desconto = 0.20 if eh_cliente_vip else 0.05
sinal = "positivo" if numero > 0 else "não positivo"
abs_valor = numero if numero >= 0 else -numero
```

---

## Módulo 5 — Estruturas de Repetição (Loops)

Loops executam um bloco de código **várias vezes** sem precisar reescrevê-lo.

```python
# Sem loop (código repetitivo e ruim):
print("Olá")
print("Olá")
print("Olá")
print("Olá")
print("Olá")

# Com loop (limpo e escalável):
for i in range(5):
    print("Olá")
```

---

### for — Quando se sabe quantas repetições

```python
# range(fim)                → 0 até fim-1
# range(inicio, fim)        → inicio até fim-1
# range(inicio, fim, passo) → com passo personalizado

for i in range(5):           # 0, 1, 2, 3, 4
    print(i)

for i in range(1, 6):        # 1, 2, 3, 4, 5
    print(i)

for i in range(0, 11, 2):    # 0, 2, 4, 6, 8, 10
    print(i)
```

#### Exemplo 1 — Contar de 1 a 10

```python
for i in range(1, 11):
    print(i, end=" ")

# Saída: 1 2 3 4 5 6 7 8 9 10
```

---

#### Exemplo 2 — Tabuada do 7

```python
numero = 7
print(f"=== Tabuada do {numero} ===")

for i in range(1, 11):
    print(f"{numero} × {i:2} = {numero * i:3}")
```

```
=== Tabuada do 7 ===
7 ×  1 =   7
7 ×  2 =  14
...
7 × 10 =  70
```

---

#### Exemplo 3 — Contagem regressiva (passo negativo)

```python
for i in range(10, -1, -1):   # de 10 até 0, descendo
    print(i, end=" ")

print("🚀 LANÇAMENTO!")
# Saída: 10 9 8 7 6 5 4 3 2 1 0 🚀 LANÇAMENTO!
```

---

#### Iterando sobre strings e listas

```python
# Cada caractere de uma string
for letra in "Python":
    print(letra, end="-")
# P-y-t-h-o-n-

# Cada item de uma lista
frutas = ["maçã", "banana", "laranja"]
for fruta in frutas:
    print(f"Fruta: {fruta}")
```

---

### while — Quando não se sabe quantas repetições

Executa **enquanto** a condição for `True`. Se já for `False` no início, **nunca executa**:

```python
# ⚠️ Sempre garanta que algo dentro do while mude a condição!

contador = 1
while contador <= 5:
    print(contador)
    contador += 1   # sem essa linha → loop infinito!
```

---

#### Exemplo — Solicitar senha até acertar

```python
SENHA_CORRETA = "abc123"
MAX_TENTATIVAS = 3
tentativas = 0

senha = input("Digite a senha: ")

while senha != SENHA_CORRETA and tentativas < MAX_TENTATIVAS:
    tentativas += 1
    print(f"Senha incorreta! Tentativa {tentativas} de {MAX_TENTATIVAS}.")
    senha = input("Tente novamente: ")

if senha == SENHA_CORRETA:
    print("✅ Acesso liberado!")
else:
    print("❌ Conta bloqueada após 3 tentativas.")
```

---

#### Simulando do-while com while True + break

Python não tem `do-while` nativo. Mas você pode simular assim:

```python
# Executa pelo menos 1 vez, repete se entrada for inválida
while True:
    opcao = input("Digite uma opção (1, 2 ou 3): ")
    if opcao in ["1", "2", "3"]:
        break   # sai do loop quando a entrada for válida
    print("Opção inválida, tente novamente.")

print(f"Você escolheu: {opcao}")
```

---

### Comparando for vs while

```
┌──────────┬────────────────────────────────┬───────────────────────────┐
│  Loop    │        Quando usar             │      Característica       │
├──────────┼────────────────────────────────┼───────────────────────────┤
│  for     │ Número de repetições conhecido │ Itera sobre sequências    │
│  while   │ Repetição baseada em condição  │ Pode não executar nenhuma │
└──────────┴────────────────────────────────┴───────────────────────────┘
```

---

### break e continue

```python
# break → encerra o loop imediatamente
for i in range(10):
    if i == 5:
        break
    print(i, end=" ")
# Saída: 0 1 2 3 4

# continue → pula a iteração atual, vai para a próxima
for i in range(10):
    if i % 2 == 0:
        continue    # pula os pares
    print(i, end=" ")
# Saída: 1 3 5 7 9
```

#### Exemplo real — Buscar em lista com break

```python
nomes = ["Ana", "Bruno", "Carlos", "Diana"]
busca = "Carlos"

for i, nome in enumerate(nomes):
    if nome == busca:
        print(f"✅ '{busca}' encontrado na posição {i}!")
        break
else:
    # 'else' do for roda SOMENTE se o loop terminar sem break
    print(f"❌ '{busca}' não encontrado.")
```

---

### ⚠️ Cuidado: Loop Infinito!

```python
# ❌ Loop infinito — programa trava! (NÃO RODE ISSO)
contador = 1
while contador > 0:
    print(contador)
    contador += 1   # cresce para sempre, nunca para!

# ✅ Correto — a condição eventualmente se torna False
contador = 1
while contador <= 10:
    print(contador)
    contador += 1
```

> 🛡️ Se travar acidentalmente, pressione `Ctrl+C` para interromper.

---

## Módulo 6 — Listas e Matrizes

### O que é uma Lista?

Em Python, o equivalente ao array é a `list` — uma coleção de valores acessados por **índice** (começando em 0):

```
lista: notas = [7.5, 8.0, 6.5, 9.0, 5.0]

Índice:   [0]   [1]   [2]   [3]   [4]
Valor:    7.5   8.0   6.5   9.0   5.0

notas[0]  → 7.5  (primeiro)
notas[-1] → 5.0  (último — índice negativo conta do final!)
notas[-2] → 9.0
```

---

### Criando e Manipulando Listas

```python
# Criar
notas = [7.5, 8.0, 6.5, 9.0, 5.0]
frutas = ["maçã", "banana", "laranja"]
vazia = []

# Acessar
print(notas[0])    # 7.5 (primeiro)
print(notas[-1])   # 5.0 (último)

# Modificar
notas[2] = 7.0
print(notas)  # [7.5, 8.0, 7.0, 9.0, 5.0]

# Tamanho
print(len(notas))  # 5

# Adicionar
notas.append(8.5)    # adiciona no final
notas.insert(0, 6.0) # insere na posição 0

# Remover
notas.remove(5.0)    # remove por valor
del notas[0]         # remove por índice
ultimo = notas.pop() # remove e retorna o último

# Verificar presença
print(8.0 in notas)   # True
print(10.0 in notas)  # False

# Ordenar
notas.sort()               # modifica a lista original
notas_ord = sorted(notas)  # retorna nova lista, sem modificar original
```

---

### Percorrendo Listas

```python
notas = [7.5, 8.0, 6.5, 9.0, 5.0]

# Forma 1 — iterar diretamente (mais pythônico)
for nota in notas:
    print(nota)

# Forma 2 — usando índice
for i in range(len(notas)):
    print(f"notas[{i}] = {notas[i]}")

# Forma 3 — enumerate() ← PREFERIDA quando precisa do índice!
for i, nota in enumerate(notas):
    print(f"Aluno {i+1}: {nota}")
```

---

### Operações Comuns em Listas

```python
notas = [7.5, 8.0, 6.5, 9.0, 5.0]

# Funções nativas do Python — use sempre estas!
print(sum(notas))            # 36.0   → soma de todos
print(max(notas))            # 9.0    → maior valor
print(min(notas))            # 5.0    → menor valor
print(len(notas))            # 5      → quantidade de elementos

media = sum(notas) / len(notas)
print(f"Média: {media:.2f}") # Média: 7.20
```

---

#### Encontrar o maior manualmente (entendendo a lógica)

```python
numeros = [4, 7, 2, 9, 1, 5]
maior = numeros[0]   # assume que o primeiro é o maior

for num in numeros:
    if num > maior:
        maior = num  # atualiza o maior quando encontra um número maior

print(f"Maior valor: {maior}")  # 9
```

---

### List Comprehension

Forma elegante e pythônica de criar listas filtradas ou transformadas:

```python
notas = [7.5, 4.0, 8.5, 3.0, 9.0, 6.0, 2.5, 7.0]

# Forma tradicional (verbosa):
aprovados = []
for nota in notas:
    if nota >= 6.0:
        aprovados.append(nota)

# Forma pythônica (list comprehension) — muito mais limpa!
aprovados = [nota for nota in notas if nota >= 6.0]
quadrados = [x**2 for x in range(1, 6)]   # [1, 4, 9, 16, 25]
dobros = [x * 2 for x in notas]           # cada nota dobrada

print(aprovados)   # [7.5, 8.5, 9.0, 6.0, 7.0]
print(f"Aprovados: {len(aprovados)} de {len(notas)}")
```

---

### Slicing — Fatiar Listas

```python
letras = ["a", "b", "c", "d", "e", "f"]
#índice:   0    1    2    3    4    5

print(letras[1:4])   # ['b', 'c', 'd']  → índice 1 até 3
print(letras[:3])    # ['a', 'b', 'c']  → início até índice 2
print(letras[3:])    # ['d', 'e', 'f']  → índice 3 até o fim
print(letras[::2])   # ['a', 'c', 'e']  → de 2 em 2
print(letras[::-1])  # ['f','e','d','c','b','a'] → invertida!
```

---

### Matrizes — Listas de Listas

Uma **matriz** é uma lista que contém outras listas — pense como uma tabela com linhas e colunas:

```python
# Matriz 3x3
matriz = [
    [1, 2, 3],   # linha 0
    [4, 5, 6],   # linha 1
    [7, 8, 9]    # linha 2
]

print(matriz[0][0])   # 1 → linha 0, coluna 0
print(matriz[1][2])   # 6 → linha 1, coluna 2
print(matriz[2][1])   # 8 → linha 2, coluna 1

# Percorrendo a matriz (loop aninhado)
for linha in matriz:
    for elemento in linha:
        print(elemento, end="\t")
    print()  # quebra de linha ao fim de cada linha

# 1    2    3
# 4    5    6
# 7    8    9
```

---

#### Exemplo — Notas por bimestre

```python
# 3 alunos × 4 bimestres
turma = [
    [7.5, 8.0, 6.5, 9.0],   # Aluno 0
    [5.0, 6.0, 7.0, 8.0],   # Aluno 1
    [9.5, 9.0, 8.5, 10.0]   # Aluno 2
]

print("=== MÉDIAS POR ALUNO ===")
for i, notas_aluno in enumerate(turma):
    media = sum(notas_aluno) / len(notas_aluno)
    status = "✅ Aprovado" if media >= 6 else "❌ Reprovado"
    print(f"Aluno {i+1}: média {media:.1f} → {status}")
```

```
=== MÉDIAS POR ALUNO ===
Aluno 1: média 7.8 → ✅ Aprovado
Aluno 2: média 6.5 → ✅ Aprovado
Aluno 3: média 9.2 → ✅ Aprovado
```

---

## Módulo 7 — Funções

### O que são e por que usar?

Funções são blocos de código **nomeados e reutilizáveis**:

```python
# Sem função — repete a mesma lógica:
area1 = 5 * 3 / 2
area2 = 8 * 4 / 2
area3 = 2 * 7 / 2

# Com função — escreve uma vez, usa várias:
def calcular_area(base, altura):
    return base * altura / 2

area1 = calcular_area(5, 3)   # 7.5
area2 = calcular_area(8, 4)   # 16.0
area3 = calcular_area(2, 7)   # 7.0
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

### Definindo Funções

```python
def nome_da_funcao(parametro1, parametro2):
    """Docstring: descreve o que a função faz."""
    # corpo da função
    return resultado   # opcional
```

---

#### Função sem retorno (só executa uma ação)

```python
def exibir_saudacao(nome):
    """Exibe uma saudação personalizada na tela."""
    print("=" * 30)
    print(f"  Olá, {nome}! 👋")
    print("  Bem-vindo ao sistema!")
    print("=" * 30)

# Chamando:
exibir_saudacao("Maria")
exibir_saudacao("João")
```

---

#### Função com retorno

```python
def calcular_area_triangulo(base, altura):
    """Calcula a área de um triângulo."""
    area = base * altura / 2
    return area

# Usando o valor retornado:
area1 = calcular_area_triangulo(6, 4)   # 12.0
area2 = calcular_area_triangulo(3, 8)   # 12.0
print(f"Área: {area1}")
```

---

### Valores Padrão (Default Parameters)

```python
def saudacao(nome, cumprimento="Olá"):
    print(f"{cumprimento}, {nome}!")

saudacao("Maria")             # "Olá, Maria!"  ← usa o padrão
saudacao("João", "Oi")        # "Oi, João!"    ← sobrescreve o padrão
saudacao("Ana", "Bom dia")    # "Bom dia, Ana!"
```

---

### Múltiplos Retornos

```python
def calcular_estatisticas(numeros):
    """Retorna média, maior e menor valor de uma lista."""
    media = sum(numeros) / len(numeros)
    return media, max(numeros), min(numeros)  # retorna uma tupla

notas = [7.5, 8.0, 6.5, 9.0, 5.0]

# Desempacotando os retornos:
media, maior, menor = calcular_estatisticas(notas)
print(f"Média: {media:.2f} | Maior: {maior} | Menor: {menor}")
# Média: 7.20 | Maior: 9.0 | Menor: 5.0
```

---

### Escopo de Variáveis

```python
mensagem_global = "Olá do global"   # variável GLOBAL

def exemplo():
    mensagem_local = "Olá do local"  # variável LOCAL (só existe aqui dentro)
    print(mensagem_global)           # ✅ acessa global
    print(mensagem_local)            # ✅ acessa local

exemplo()
print(mensagem_global)    # ✅ funciona
# print(mensagem_local)   # ❌ NameError — local não existe fora da função
```

> ⚠️ **Boa prática:** Evite `global`. Prefira passar valores como parâmetros e receber via `return` — código mais previsível e fácil de testar.

---

### Exemplo Completo — Calculadora de Salário

```python
def calcular_imposto_ir(salario):
    """Calcula o IR com base na tabela progressiva brasileira."""
    if salario <= 1903.98:
        return 0
    elif salario <= 2826.65:
        return salario * 0.075 - 142.80
    elif salario <= 3751.05:
        return salario * 0.15 - 354.80
    elif salario <= 4664.68:
        return salario * 0.225 - 636.13
    else:
        return salario * 0.275 - 869.36

def calcular_inss(salario):
    """Calcula o desconto de INSS (11%)."""
    return salario * 0.11

def calcular_salario_liquido(salario_bruto):
    """Calcula o salário líquido após todos os descontos."""
    inss = calcular_inss(salario_bruto)
    ir = calcular_imposto_ir(salario_bruto)
    return salario_bruto - inss - ir

# Programa principal
bruto = float(input("Salário bruto: R$ "))

inss = calcular_inss(bruto)
ir = calcular_imposto_ir(bruto)
liquido = calcular_salario_liquido(bruto)

print(f"\nSalário bruto:   R$ {bruto:,.2f}")
print(f"Desconto INSS:   R$ {inss:,.2f}")
print(f"Desconto IR:     R$ {ir:,.2f}")
print(f"Salário líquido: R$ {liquido:,.2f}")
```

---

## Módulo 8 — Recursão

### O que é Recursão?

**Recursão** é quando uma função **chama a si mesma** para resolver um problema. Funciona quando o problema pode ser dividido em subproblemas idênticos e menores.

```
Toda função recursiva tem OBRIGATORIAMENTE 2 partes:
  1. Caso Base      → condição de parada (quando PARAR de chamar a si mesma)
  2. Caso Recursivo → chama a si mesma com um problema MENOR
```

---

### Exemplo 1 — Fatorial

`n! = n × (n-1) × ... × 2 × 1`, e `0! = 1`

```python
def fatorial(n):
    if n == 0 or n == 1:  # caso base → para aqui
        return 1
    return n * fatorial(n - 1)   # caso recursivo → chama com n-1

print(fatorial(5))    # 120
print(fatorial(10))   # 3628800
```

**Rastreando `fatorial(4)` passo a passo:**

```
fatorial(4)
  → 4 * fatorial(3)
         → 3 * fatorial(2)
                → 2 * fatorial(1)
                       → retorna 1    ← caso base!
                → retorna 2 * 1 = 2
         → retorna 3 * 2 = 6
  → retorna 4 * 6 = 24
```

---

### Exemplo 2 — Fibonacci

Sequência: `0, 1, 1, 2, 3, 5, 8, 13, 21, 34...` — cada número é a soma dos dois anteriores.

```python
def fibonacci(n):
    if n <= 1:                              # casos base
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)   # caso recursivo

for i in range(10):
    print(fibonacci(i), end=" ")
# 0 1 1 2 3 5 8 13 21 34
```

---

### Exemplo 3 — Soma de lista

```python
def soma_lista(lista):
    """Soma todos os elementos recursivamente."""
    if len(lista) == 0:   # caso base: lista vazia
        return 0
    return lista[0] + soma_lista(lista[1:])   # primeiro + soma do resto

print(soma_lista([1, 2, 3, 4, 5]))  # 15
```

---

### Recursão vs Iteração

```python
# Fatorial ITERATIVO
def fatorial_iterativo(n):
    resultado = 1
    for i in range(2, n + 1):
        resultado *= i
    return resultado

# Fatorial RECURSIVO
def fatorial_recursivo(n):
    if n <= 1:
        return 1
    return n * fatorial_recursivo(n - 1)

print(fatorial_iterativo(5))   # 120
print(fatorial_recursivo(5))   # 120  ← mesmo resultado, lógica diferente
```

| Aspecto | Iterativo | Recursivo |
|---|---|---|
| **Legibilidade** | Às vezes verbosa | Frequentemente elegante |
| **Performance** | Geralmente mais rápido | Pode ser mais lento |
| **Memória** | Usa menos memória | Usa a pilha de chamadas |
| **Quando usar** | Problemas sequenciais | Problemas divididos em subproblemas |

---

## Módulo 9 — Busca e Ordenação

### Busca Linear (Sequential Search)

Percorre a lista **do início ao fim** até encontrar o elemento:

```python
def busca_linear(lista, alvo):
    """Retorna o índice do alvo, ou -1 se não encontrar."""
    for i, elemento in enumerate(lista):
        if elemento == alvo:
            return i
    return -1

numeros = [64, 34, 25, 12, 22, 11, 90]

print(busca_linear(numeros, 22))   # 4 (encontrado no índice 4)
print(busca_linear(numeros, 99))   # -1 (não encontrado)
```

**Complexidade:** O(n) — no pior caso, verifica todos os n elementos.

---

### Busca Binária (Binary Search)

Muito mais eficiente, mas **a lista precisa estar ordenada**. Divide o problema ao meio a cada passo:

```python
def busca_binaria(lista, alvo):
    """Busca binária — requer lista ORDENADA."""
    inicio = 0
    fim = len(lista) - 1

    while inicio <= fim:
        meio = (inicio + fim) // 2

        if lista[meio] == alvo:
            return meio                # encontrou!
        elif lista[meio] < alvo:
            inicio = meio + 1          # busca na metade direita
        else:
            fim = meio - 1             # busca na metade esquerda

    return -1   # não encontrado

numeros = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
print(busca_binaria(numeros, 7))    # 3
print(busca_binaria(numeros, 10))   # -1
```

**Visualizando a busca do número 7 em `[1, 3, 5, 7, 9, 11, 13]`:**

```
[1, 3, 5, 7, 9, 11, 13]
            ↑ meio = 9
            9 > 7 → busca na ESQUERDA

[1, 3, 5, 7]
      ↑ meio = 3
      3 < 7 → busca na DIREITA

[5, 7]
   ↑ meio = 5
   5 < 7 → busca na DIREITA

[7] → meio = 7 == 7 → ENCONTROU! ✅
```

**Por que a busca binária é tão poderosa?**

| Tamanho da Lista | Busca Linear | Busca Binária |
|---:|---:|---:|
| 10 | 10 passos | 4 passos |
| 1.000 | 1.000 passos | 10 passos |
| 1.000.000 | 1.000.000 passos | 20 passos |
| 1.000.000.000 | 1 bilhão de passos | **30 passos** |

---

### Bubble Sort — Ordenação por Bolha

O mais simples. Compara pares adjacentes e troca se estiverem fora de ordem:

```python
def bubble_sort(lista):
    """Ordena a lista in-place usando Bubble Sort."""
    n = len(lista)
    for i in range(n - 1):
        for j in range(n - 1 - i):
            if lista[j] > lista[j + 1]:
                # Swap pythônico — sem variável temporária!
                lista[j], lista[j + 1] = lista[j + 1], lista[j]
    return lista

numeros = [64, 34, 25, 12, 22, 11, 90]
print(f"Antes:  {numeros}")
bubble_sort(numeros)
print(f"Depois: {numeros}")
# Antes:  [64, 34, 25, 12, 22, 11, 90]
# Depois: [11, 12, 22, 25, 34, 64, 90]
```

**Visualizando `[5, 3, 8, 1]`:**

```
Passo 1: [5,3,8,1] → [3,5,8,1] → [3,5,8,1] → [3,5,1,8]  (8 foi para o fim)
Passo 2: [3,5,1,8] → [3,5,1,8] → [3,1,5,8]               (5 no lugar)
Passo 3: [3,1,5,8] → [1,3,5,8]                            ✅ Ordenado!
```

> 💡 **Na prática**, use `lista.sort()` (modifica) ou `sorted(lista)` (nova lista) do Python — são muito mais eficientes.

---

## Módulo 10 — Introdução a Estruturas de Dados

### Dicionários — dict

Estrutura **chave → valor**, como um dicionário real ou um banco de dados simples:

```python
# Criando um dicionário
aluno = {
    "nome": "Maria",
    "idade": 20,
    "curso": "Ciência da Computação",
    "ativo": True
}

# Acessar valor por chave
print(aluno["nome"])    # "Maria"
print(aluno["idade"])   # 20

# Adicionar/atualizar
aluno["email"] = "maria@email.com"
aluno["idade"] = 21

# Verificar se chave existe
if "email" in aluno:
    print(f"Email: {aluno['email']}")

# Iterando sobre tudo
for chave, valor in aluno.items():
    print(f"  {chave}: {valor}")
```

---

### Pilha (Stack) — list como LIFO

**LIFO = Last In, First Out** — último a entrar, primeiro a sair. Como uma pilha de pratos:

```python
pilha = []

# push — empilha no topo
pilha.append(3)
pilha.append(7)
pilha.append(1)
print(pilha)       # [3, 7, 1]

# pop — desempilha do topo
topo = pilha.pop()
print(topo)        # 1 (último que entrou)
print(pilha)       # [3, 7]

# peek — vê o topo sem remover
print(pilha[-1])   # 7

# verificar se está vazia
print(len(pilha) == 0)   # False
```

**Aplicação real — histórico de desfazer (Ctrl+Z):**

```python
historico = []

def executar_acao(acao):
    historico.append(acao)   # empilha ação executada
    print(f"Executado: {acao}")

def desfazer():
    if historico:
        acao = historico.pop()  # remove a última ação
        print(f"Desfeito: {acao}")
    else:
        print("Nada para desfazer!")

executar_acao("digitar 'olá'")
executar_acao("negrito")
executar_acao("mudar fonte")
desfazer()   # Desfeito: mudar fonte
desfazer()   # Desfeito: negrito
```

---

### Fila (Queue) — deque como FIFO

**FIFO = First In, First Out** — primeiro a entrar, primeiro a sair. Como uma fila de banco:

```python
from collections import deque

fila = deque()

# enqueue — adiciona no final
fila.append("Ana")
fila.append("Bob")
fila.append("Carlos")
print(fila)   # deque(['Ana', 'Bob', 'Carlos'])

# dequeue — remove do início
proximo = fila.popleft()
print(proximo)   # "Ana" (primeiro que entrou)
print(fila)      # deque(['Bob', 'Carlos'])
```

---

### Conjuntos — set

Coleção de valores **únicos**, sem ordem definida:

```python
# Criar
nums = {1, 2, 3, 2, 1}   # duplicatas são removidas automaticamente!
print(nums)  # {1, 2, 3}

# Operações matemáticas de conjuntos
a = {1, 2, 3, 4, 5}
b = {4, 5, 6, 7, 8}

print(a | b)   # União:           {1, 2, 3, 4, 5, 6, 7, 8}
print(a & b)   # Interseção:      {4, 5}
print(a - b)   # Diferença (a-b): {1, 2, 3}
```

**Aplicação real — remover duplicatas de uma lista:**

```python
lista_com_dups = [1, 3, 2, 1, 5, 3, 2, 4]
sem_duplicatas = list(set(lista_com_dups))
print(sem_duplicatas)  # [1, 2, 3, 4, 5] (ordem pode variar)
```

---

### Comparativo de Estruturas

| Estrutura | Sintaxe | Ordenada | Mutável | Duplicatas | Acesso |
|---|---|:---:|:---:|:---:|---|
| **list** | `[1, 2, 3]` | ✅ | ✅ | ✅ | Por índice |
| **tuple** | `(1, 2, 3)` | ✅ | ❌ | ✅ | Por índice |
| **dict** | `{"a": 1}` | ✅* | ✅ | Chaves: ❌ | Por chave |
| **set** | `{1, 2, 3}` | ❌ | ✅ | ❌ | — |

---

## Módulo 11 — Depuração e Boas Práticas

### Os 3 Tipos de Erros

#### 1. SyntaxError — Erro de Sintaxe

O código foi escrito de forma gramaticalmente incorreta — Python não consegue nem lê-lo:

```python
# ❌ SyntaxError — faltou o ':'
if x > 0
    print(x)

# ❌ SyntaxError — parêntese não fechado
print("olá"

# ✅ Correto
if x > 0:
    print(x)
```

---

#### 2. RuntimeError — Erro em Tempo de Execução

O código é sintaticamente válido, mas **trava ao rodar**:

```python
# ❌ ZeroDivisionError
resultado = 10 / 0

# ❌ IndexError
lista = [1, 2, 3]
print(lista[10])    # índice fora do range

# ❌ TypeError
print("5" + 5)      # não dá para somar str com int

# ✅ Tratando com try/except
try:
    divisor = int(input("Divisor: "))
    resultado = 100 / divisor
    print(f"Resultado: {resultado}")
except ZeroDivisionError:
    print("Erro: divisão por zero é impossível!")
except ValueError:
    print("Erro: isso não é um número válido!")
except Exception as e:
    print(f"Erro inesperado: {e}")
finally:
    print("Operação finalizada.")   # executa sempre, com ou sem erro
```

---

#### 3. LogicError — Erro de Lógica (o mais traiçoeiro!)

O código roda sem erros, mas **produz resultados errados**:

```python
# ❌ Erro de precedência — parênteses no lugar errado
nota1, nota2, nota3 = 7, 8, 9
media = nota1 + nota2 + nota3 / 3    # divisão só no nota3!
# calcula: 7 + 8 + 3.0 = 18.0  ← ERRADO!

# ✅ Correto
media = (nota1 + nota2 + nota3) / 3
# calcula: (7 + 8 + 9) / 3 = 8.0  ← CORRETO!

# ❌ Outro clássico — == vs =
x = 5
if x == 10:   # correto: compara
    print("dez")

# x = 10 dentro de um if seria SyntaxError em Python (boa proteção!)
# Em C/Java isso compilaria e sempre seria True — bug grave!
```

---

### Técnicas de Depuração

#### Print Debugging (rápido e simples)

```python
def calcular_media(notas):
    print(f"DEBUG: notas recebidas = {notas}")
    soma = 0
    for nota in notas:
        soma += nota
        print(f"DEBUG: soma acumulada = {soma}")
    media = soma / len(notas)
    print(f"DEBUG: média final = {media}")
    return media
```

---

#### Trace Table (rastreamento manual no papel)

Simule o código linha por linha, anotando os valores das variáveis:

```python
i = 1
soma = 0
while i <= 5:
    soma = soma + i
    i = i + 1
print(soma)
```

| Passo | `i` | `soma` | `i <= 5`? |
|:---:|:---:|:---:|:---:|
| Início | 1 | 0 | — |
| 1 | 2 | 1 | ✅ True |
| 2 | 3 | 3 | ✅ True |
| 3 | 4 | 6 | ✅ True |
| 4 | 5 | 10 | ✅ True |
| 5 | 6 | 15 | ✅ True |
| 6 | 6 | 15 | ❌ False → sai |

Saída: `15` ✅

---

### Boas Práticas em Python

#### 1. Nomes descritivos (snake_case)

```python
# ❌ Ruim
d = 30
c = 0
def f(x, y): return x * y / 2

# ✅ Bom
dias_no_mes = 30
contagem_erros = 0
def calcular_area_triangulo(base, altura):
    return base * altura / 2
```

---

#### 2. Uma função, uma responsabilidade

```python
# ❌ Função fazendo tudo
def processar_pedido(pedido):
    validar()
    calcular_preco()
    aplicar_desconto()
    gerar_nota()
    enviar_email()
    atualizar_estoque()

# ✅ Responsabilidades separadas — cada função faz uma coisa
def validar_pedido(pedido): ...
def calcular_total(pedido): ...
def gerar_nota_fiscal(pedido): ...
def notificar_cliente(pedido): ...
```

---

#### 3. Comentários explicam o "porquê", não o "o quê"

```python
# ❌ Inútil — descreve o óbvio
i += 1   # incrementa i em 1

# ✅ Útil — explica o motivo
i += 1   # pula o delimitador que não deve ser processado

# ❌ Número mágico — o que é 168?
if horas > 168:
    pagar_hora_extra()

# ✅ Constante com nome autoexplicativo
HORAS_MENSAIS_NORMAIS = 168   # 44h/semana × 4.33 semanas/mês
if horas > HORAS_MENSAIS_NORMAIS:
    pagar_hora_extra()
```

---

#### 4. Docstrings em todas as funções

```python
def calcular_imc(peso, altura):
    """
    Calcula o Índice de Massa Corporal.

    Args:
        peso (float): Peso em quilogramas
        altura (float): Altura em metros

    Returns:
        float: O valor do IMC

    Example:
        >>> calcular_imc(70, 1.75)
        22.86
    """
    return peso / (altura ** 2)
```

---

## 📝 Exercícios Resolvidos por Nível

### 🟢 Nível 1 — Iniciante

#### Exercício 1.1 — Calculadora de IMC

```python
def calcular_imc(peso, altura):
    return peso / (altura ** 2)

def classificar_imc(imc):
    if imc < 18.5:
        return "Abaixo do peso 🔵"
    elif imc < 25.0:
        return "Peso normal ✅"
    elif imc < 30.0:
        return "Sobrepeso 🟡"
    elif imc < 35.0:
        return "Obesidade Grau I 🟠"
    elif imc < 40.0:
        return "Obesidade Grau II 🔴"
    else:
        return "Obesidade Grau III ⛔"

peso = float(input("Peso (kg): "))
altura = float(input("Altura (m): "))

imc = calcular_imc(peso, altura)
print(f"\nSeu IMC: {imc:.2f}")
print(f"Classificação: {classificar_imc(imc)}")
```

---

#### Exercício 1.2 — Tabuada Completa

```python
def exibir_tabuada(numero):
    print(f"\n{'='*22}")
    print(f"    Tabuada do {numero}")
    print(f"{'='*22}")
    for i in range(1, 11):
        print(f"  {numero} × {i:2} = {numero * i:3}")

numero = int(input("Digite um número: "))
exibir_tabuada(numero)
```

---

### 🟡 Nível 2 — Intermediário

#### Exercício 2.1 — Verificador de Número Primo

```python
import math

def eh_primo(n):
    """Retorna True se n é primo, False caso contrário."""
    if n < 2:
        return False
    if n == 2:
        return True
    if n % 2 == 0:
        return False
    for i in range(3, int(math.sqrt(n)) + 1, 2):
        if n % i == 0:
            return False
    return True

numero = int(input("Digite um número: "))

if eh_primo(numero):
    print(f"✅ {numero} é primo!")
else:
    print(f"❌ {numero} não é primo.")

# Bônus: listar todos os primos até 50
primos = [i for i in range(2, 51) if eh_primo(i)]
print(f"\nPrimos até 50: {primos}")
```

---

#### Exercício 2.2 — Estatísticas de Notas com Validação

```python
def coletar_notas(quantidade):
    notas = []
    for i in range(quantidade):
        while True:
            try:
                nota = float(input(f"Nota {i+1} (0-10): "))
                if 0 <= nota <= 10:
                    notas.append(nota)
                    break
                else:
                    print("  ⚠️ Nota deve ser entre 0 e 10.")
            except ValueError:
                print("  ⚠️ Digite um número válido.")
    return notas

notas = coletar_notas(5)
media = sum(notas) / len(notas)
aprovados = [n for n in notas if n >= 6]

print(f"\n📊 RELATÓRIO")
print(f"Notas:       {notas}")
print(f"Média:       {media:.2f}")
print(f"Maior:       {max(notas):.1f}")
print(f"Menor:       {min(notas):.1f}")
print(f"Aprovados:   {len(aprovados)} de {len(notas)}")
```

---

### 🔴 Nível 3 — Avançado

#### Exercício 3.1 — Palíndromo

```python
def eh_palindromo(texto):
    """Verifica se uma string é palíndromo, ignorando espaços e maiúsculas."""
    limpo = texto.lower().replace(" ", "")
    return limpo == limpo[::-1]   # compara com a versão invertida

testes = ["arara", "racecar", "Python", "A man a plan a canal Panama", "ovo"]

for palavra in testes:
    icone = "✅" if eh_palindromo(palavra) else "❌"
    print(f"  {icone} '{palavra}'")
```

```
✅ 'arara'
✅ 'racecar'
❌ 'Python'
✅ 'A man a plan a canal Panama'
✅ 'ovo'
```

---

#### Exercício 3.2 — Torre de Hanói (Recursão)

```python
movimentos = []   # registra todos os movimentos

def hanoi(n, origem, destino, auxiliar):
    """
    Resolve a Torre de Hanói recursivamente.
    n: número de discos
    """
    if n == 1:
        passo = f"Mova disco 1: {origem} → {destino}"
        movimentos.append(passo)
        print(f"  {passo}")
        return

    hanoi(n - 1, origem, auxiliar, destino)  # move n-1 discos para auxiliar

    passo = f"Mova disco {n}: {origem} → {destino}"
    movimentos.append(passo)
    print(f"  {passo}")

    hanoi(n - 1, auxiliar, destino, origem)  # move n-1 do auxiliar para destino


n = int(input("Número de discos: "))
print(f"\n🗼 Torre de Hanói com {n} disco(s):\n")
hanoi(n, "A", "C", "B")
print(f"\nTotal de movimentos: {len(movimentos)} (fórmula: 2^{n}-1 = {2**n - 1})")
```

```
🗼 Torre de Hanói com 3 disco(s):

  Mova disco 1: A → C
  Mova disco 2: A → B
  Mova disco 1: C → B
  Mova disco 3: A → C
  Mova disco 1: B → A
  Mova disco 2: B → C
  Mova disco 1: A → C

Total de movimentos: 7 (fórmula: 2^3-1 = 7)
```

---

## 🚀 Cheatsheet Python

```python
# === VARIÁVEIS E TIPOS ===
x = 10           # int
y = 3.14         # float
nome = "Ana"     # str
ativo = True     # bool

type(x)          # <class 'int'>
int("42")        # 42    → conversão str→int
float("3.14")    # 3.14  → str→float
str(100)         # "100" → int→str

# === OPERADORES ===
+  -  *  /       # aritméticos básicos
//               # divisão inteira
%                # módulo (resto)
**               # potência
==  !=  >  <  >=  <=   # comparação
and  or  not     # lógicos

# === STRINGS ===
len("Python")         # 6
"py".upper()          # "PY"
"PY".lower()          # "py"
"  ok  ".strip()      # "ok"
"a,b,c".split(",")    # ["a","b","c"]
f"Olá, {nome}!"       # f-string

# === LISTAS ===
lista = [1, 2, 3]
lista.append(4)       # adiciona no final
lista.remove(2)       # remove por valor
lista.pop()           # remove/retorna o último
lista.pop(0)          # remove por índice
lista.sort()          # ordena in-place
sorted(lista)         # nova lista ordenada
len(lista)            # tamanho
lista[0]              # primeiro
lista[-1]             # último
lista[1:3]            # slice → [2, 3]
lista[::-1]           # invertida
2 in lista            # True/False
[x**2 for x in lista] # list comprehension

# === DICIONÁRIOS ===
d = {"chave": "valor"}
d["chave"]            # acessar
d["nova"] = "x"       # adicionar/atualizar
del d["chave"]        # remover
"chave" in d          # verificar existência
d.keys()              # todas as chaves
d.values()            # todos os valores
d.items()             # pares (chave, valor)

# === IF / ELIF / ELSE ===
if condição:
    ...
elif outra:
    ...
else:
    ...

x = "sim" if condição else "não"   # ternário

# === FOR / WHILE ===
for i in range(10):      # 0 a 9
    ...

for i in range(1, 11):   # 1 a 10
    ...

for item in lista:
    ...

for i, item in enumerate(lista):
    ...

while condição:
    ...

break       # sai do loop
continue    # próxima iteração

# === FUNÇÕES ===
def nome(param, opcional="padrão"):
    """Docstring."""
    return valor

lambda x: x * 2   # função anônima

# === TRY / EXCEPT ===
try:
    resultado = 10 / 0
except ZeroDivisionError:
    print("Divisão por zero!")
except Exception as e:
    print(f"Erro: {e}")
finally:
    print("Sempre executa")

# === PILHA (LIFO) e FILA (FIFO) ===
pilha = []
pilha.append(x)   # push
pilha.pop()       # pop

from collections import deque
fila = deque()
fila.append(x)    # enqueue
fila.popleft()    # dequeue
```

---

## 🎓 Próximos Passos

Parabéns! Você concluiu o curso. Com essa base, qualquer linguagem ficará mais fácil. Veja o caminho recomendado:

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
   │  Python       │ → Orientação a Objetos (OOP)
   │  Intermediário│ → Módulos e pacotes (pip)
   │               │ → Arquivos, JSON, APIs
   └───────┬───────┘ → Bibliotecas (pandas, requests, flask...)
           │
           ▼
   ┌───────────────┐
   │ Estruturas de │ → Listas Ligadas, Árvores,
   │ Dados         │   Grafos, Tabelas Hash
   └───────┬───────┘
           │
           ▼
   ┌───────────────┐
   │ Algoritmos    │ → Complexidade (Big O)
   │ Avançados     │ → Programação Dinâmica
   └───────┬───────┘ → Algoritmos Gulosos
           │
           ▼
   ┌───────────────┐
   │ Especialização│ → Backend (Django, FastAPI)
   │ (escolha a    │ → Data Science (pandas, numpy)
   │  sua!)        │ → IA/ML (scikit-learn, PyTorch)
   └───────────────┘ → Segurança, DevOps, Mobile...
```

---

### 📚 Recursos Recomendados

| Recurso | Tipo | Link |
|---|---|---|
| **CS50P** (Harvard — Python) | Curso gratuito | [cs50.harvard.edu/python](https://cs50.harvard.edu/python) |
| **Python Tutor** | Visualiza execução passo a passo | [pythontutor.com](https://pythontutor.com) |
| **Visualgo** | Visualizador de algoritmos | [visualgo.net](https://visualgo.net) |
| **Automate the Boring Stuff** | Livro gratuito online | [automatetheboringstuff.com](https://automatetheboringstuff.com) |
| **LeetCode** | Prática de algoritmos | [leetcode.com](https://leetcode.com) |
| **Real Python** | Tutoriais práticos | [realpython.com](https://realpython.com) |

---

### 🏁 Desafios para continuar praticando

- [ ] Execute e modifique **cada exemplo** deste curso
- [ ] Implemente um jogo de **Pedra, Papel, Tesoura** com placar
- [ ] Crie um **mini banco** com saldo, depósito e saque
- [ ] Resolva 30 problemas no LeetCode (categoria Easy)
- [ ] Implemente **Selection Sort** e **Insertion Sort** do zero
- [ ] Estude **Complexidade de Algoritmos** (Notação Big O)
- [ ] Faça o curso **CS50P** da Harvard (gratuito e excelente)

---

<div align="center">

**Feito com ❤️, Python e muita lógica**

*"Todo mundo neste país deveria aprender a programar um computador,*
*porque isso te ensina a pensar."* — Steve Jobs

⭐ Se este curso te ajudou, dê uma estrela no repositório!

</div>
