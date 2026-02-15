# ⛏️ Curso Completo de Skript — Minecraft

> **Do zero ao avançado** — aprenda a criar plugins para o seu servidor Minecraft usando **Skript**, a linguagem em inglês simples que qualquer pessoa consegue aprender. Sem precisar saber Java, sem compilar nada — só escrever, salvar e recarregar.

> 🎮 **Versão:** Skript 2.14+ | **Servidor:** Paper 1.21+ | **Arquivo:** `.sk` dentro de `plugins/Skript/scripts/`

---

## 📋 Índice

1. [O que é Skript?](#-o-que-é-skript)
2. [Instalação e Configuração](#-instalação-e-configuração)
3. [Módulo 1 — Estrutura e Sintaxe Básica](#módulo-1--estrutura-e-sintaxe-básica)
4. [Módulo 2 — Eventos (Events)](#módulo-2--eventos-events)
5. [Módulo 3 — Condições (Conditions)](#módulo-3--condições-conditions)
6. [Módulo 4 — Efeitos (Effects)](#módulo-4--efeitos-effects)
7. [Módulo 5 — Variáveis (Variables)](#módulo-5--variáveis-variables)
8. [Módulo 6 — Comandos Customizados](#módulo-6--comandos-customizados)
9. [Módulo 7 — Loops](#módulo-7--loops)
10. [Módulo 8 — Funções](#módulo-8--funções)
11. [Módulo 9 — Formatação de Mensagens](#módulo-9--formatação-de-mensagens)
12. [Módulo 10 — Projetos Completos](#módulo-10--projetos-completos)
13. [Addons Populares](#-addons-populares)
14. [Erros Comuns e Soluções](#-erros-comuns-e-soluções)
15. [Cheatsheet Skript](#-cheatsheet-skript)
16. [Recursos e Comunidade](#-recursos-e-comunidade)

---

## 🤔 O que é Skript?

**Skript** é um plugin para servidores Bukkit/Paper que permite ao administrador do servidor personalizar o servidor facilmente, sem a complicação de programar um plugin em Java.

Em vez de escrever código Java complexo, você escreve frases em inglês simples:

```
# Java (complicado):
player.sendMessage(ChatColor.GREEN + "Bem-vindo!");

# Skript (simples):
send "&aWell-come!" to player
```

### Por que usar Skript?

| Vantagem | Descrição |
|---|---|
| 🟢 **Sem Java** | Não precisa aprender Java ou compilar nada |
| ⚡ **Reload sem restart** | Altere e recarregue sem reiniciar o servidor |
| 📖 **Sintaxe em inglês** | Frases quase naturais, fáceis de ler |
| 🧩 **Extensível** | Centenas de addons da comunidade |
| 🛡️ **Erros claros** | Mensagens de erro em linguagem simples |

### O modelo mental do Skript

Todo script Skript segue um padrão simples:

```
EVENTO → CONDIÇÕES → EFEITOS

Quando algo acontece (evento):
  Se certas coisas são verdadeiras (condições):
    Faça alguma coisa (efeitos)
```

**Exemplo prático:**
```vb
on join:            # EVENTO: jogador entrou
    player is op    # CONDIÇÃO: é operador?
        send "Bem-vindo, Admin!" to player  # EFEITO
```

---

## 🛠️ Instalação e Configuração

### Requisitos

| Componente | Versão mínima | Download |
|---|---|---|
| **Java** | 21+ | [adoptium.net](https://adoptium.net) |
| **Paper** | 1.21+ | [papermc.io](https://papermc.io) |
| **Skript** | 2.14+ | [GitHub Releases](https://github.com/SkriptLang/Skript/releases) |

> ⚠️ **Importante:** Skript 2.14 suporta Minecraft 1.21.0 a 1.21.11. O Paper é obrigatório — Spigot não é mais suportado.

---

### Instalação Passo a Passo

**1. Instale o Paper no seu servidor**

**2. Baixe o Skript.jar e coloque em `plugins/`**

**3. Inicie o servidor uma vez — ele vai gerar as pastas:**
```
plugins/
└── Skript/
    ├── scripts/        ← seus .sk ficam aqui!
    ├── config.sk
    └── aliases/
```

**4. Crie seu primeiro script:**
```
plugins/Skript/scripts/meu-primeiro-script.sk
```

**5. Escreva algo, salve e recarregue:**
```
/skript reload meu-primeiro-script
```

---

### Comandos Essenciais do Skript

| Comando | O que faz |
|---|---|
| `/skript reload all` | Recarrega todos os scripts |
| `/skript reload <nome>` | Recarrega um script específico |
| `/skript enable <nome>` | Ativa um script desativado |
| `/skript disable <nome>` | Desativa um script sem deletar |
| `/skript info` | Informações sobre o Skript instalado |

---

### Estrutura de Arquivos Recomendada

```
scripts/
├── sistema-join.sk       ← mensagens de entrada/saída
├── comandos-gerais.sk    ← comandos do servidor
├── sistema-economia.sk   ← economia e loja
├── mini-games/
│   ├── pvp.sk
│   └── parkour.sk
└── utils/
    └── funcoes.sk        ← funções reutilizáveis
```

---

## Módulo 1 — Estrutura e Sintaxe Básica

### A regra mais importante: Indentação!

Skript usa **indentação** (espaços ou tabs) para definir blocos de código — exatamente como Python. Cada nível é recuado com 4 espaços ou 1 tab:

```vb
on join:                          # nível 0 — evento
    send "Olá!" to player         # nível 1 — efeito do evento
    if player is op:              # nível 1 — condição dentro do evento
        send "Olá, Admin!" to player  # nível 2 — efeito da condição
```

> ⚠️ **Erro mais comum de iniciantes:** Esquecer a indentação ou misturar tabs e espaços. Use sempre um padrão consistente.

---

### Comentários

```vb
# Isso é um comentário de linha única

## Isso também é um comentário

### Comentário de múltiplas linhas
    pode continuar aqui
    e aqui também
###
```

---

### Estrutura de um Script Completo

```vb
# ================================================
# Nome: sistema-bem-vindo.sk
# Descrição: Mensagens de boas-vindas no servidor
# Autor: Seu Nome
# ================================================

options:
    prefix: &8[&aServidor&8] &r    # variável global do script

on join:
    send "{@prefix}&aWelcome, &e%player%&a!" to player
    send "{@prefix}&7You are player number &e%{player-count}%" to all players

on quit:
    send "{@prefix}&c%player% &7left the server." to all players
```

---

### Options — Variáveis do Script

A seção `options:` define constantes reutilizáveis no arquivo:

```vb
options:
    prefix: &8[&6MyServer&8]&r
    admin-perm: meuservidor.admin
    spawn: world, 0, 64, 0

on join:
    send "{@prefix} Welcome!" to player

command /spawn:
    permission: {@admin-perm}
    trigger:
        teleport player to {@spawn}
```

---

## Módulo 2 — Eventos (Events)

Skript é uma linguagem orientada a eventos. Isso é alcançado com triggers (gatilhos), onde cada um é uma coleção de condições e efeitos. Cada vez que um trigger é chamado, todas as condições são verificadas e, se todas forem satisfeitas, os efeitos são executados.

### Eventos de Jogador

```vb
# Jogador entra no servidor
on join:
    send "Welcome to the server!" to player

# Jogador sai do servidor
on quit:
    broadcast "&c%player% left the game."

# Jogador morre
on death of player:
    send "&4You died at %location of player%!" to player

# Jogador respawna
on respawn:
    teleport player to spawn of world "world"
    send "&aYou respawned!" to player

# Jogador sobe de nível
on level change:
    if new level is 10:
        send "&6&lYou reached level 10! &eGood job!" to player

# Jogador troca de mundo
on world change:
    send "&7You entered world: &e%event-world%" to player
```

---

### Eventos de Bloco

```vb
# Jogador quebra um bloco
on break of diamond ore:
    send "&b✦ You found diamonds!" to player
    play sound "entity.experience_orb.pickup" to player

# Jogador coloca um bloco
on place of tnt:
    if player doesn't have permission "server.tnt":
        cancel event
        send "&cYou can't place TNT here!" to player

# Jogador interage com bloco
on right click on chest:
    send "&7You opened a chest at %location of event-block%." to player
```

---

### Eventos de Combate

```vb
# Jogador ataca entidade
on damage of player by player:
    send "&c%attacker% is attacking you!" to victim

# Jogador recebe dano
on damage of player:
    if damage > 5:
        send "&4Heavy damage! (%damage% hearts)" to player

# Entidade morre
on death of zombie:
    chance of 10%:
        drop 1 diamond at location of event-entity
```

---

### Eventos de Servidor

```vb
# Servidor carregando (ao iniciar ou recarregar o script)
on load:
    broadcast "&aServer systems loaded successfully!"
    set {server.start-time} to now

# Script sendo descarregado
on unload:
    broadcast "&cServer shutting down..."

# A cada X tempo
every 5 minutes:
    broadcast "&eRemember to vote at vote.servidor.com!"

every 1 hour:
    save all chunks
    broadcast "&aWorld saved!"
```

---

### Cancelando Eventos

```vb
# "cancel event" impede o evento de acontecer
on break of bedrock:
    cancel event
    send "&cYou can't break bedrock!" to player

on drop of item:
    if player's world is "arena":
        cancel event
        send "&cYou can't drop items in the arena!" to player
```

---

## Módulo 3 — Condições (Conditions)

Condições verificam se algo é verdadeiro antes de executar efeitos.

### Condições de Jogador

```vb
on join:
    # Verificar permissão
    if player has permission "vip.rank":
        send "&6Welcome, VIP!" to player

    # Verificar gamemode
    if player's gamemode is creative:
        send "&bYou are in creative mode." to player

    # Verificar saúde
    if player's health is less than 5:
        send "&cYou are at low health!" to player

    # Verificar nível
    if player's level is greater than or equal to 30:
        send "&aYou have enough XP to enchant!" to player

    # Verificar inventário
    if player's inventory is full:
        send "&cYour inventory is full!" to player
```

---

### Condições com if / else if / else

```vb
on join:
    if player has permission "rank.dono":
        send "&4&lDONO &fwelcome!" to player
    else if player has permission "rank.admin":
        send "&cADMIN &fwelcome!" to player
    else if player has permission "rank.mod":
        send "&bMOD &fwelcome!" to player
    else if player has permission "rank.vip":
        send "&6VIP &fwelcome!" to player
    else:
        send "&7Welcome to the server!" to player
```

---

### Condições de Item

```vb
command /craft-special:
    trigger:
        # Verifica se o jogador tem os materiais
        if player has 5 diamonds:
            if player has 3 gold ingots:
                remove 5 diamonds from player
                remove 3 gold ingots from player
                give player 1 diamond sword named "&bSword of Power"
                send "&aCrafted successfully!" to player
            else:
                send "&cYou need 3 gold ingots!" to player
        else:
            send "&cYou need 5 diamonds!" to player
```

---

### Condições de Mundo e Localização

```vb
on move:
    # Verificar mundo
    if player's world is "pvp-arena":
        if player is in region "safe-zone":
            cancel event

    # Verificar coordenadas (Y baixo = void)
    if player's y-coordinate < 0:
        teleport player to spawn of world
        send "&cYou fell into the void!" to player
```

---

### Condições com and / or / not

```vb
on break:
    # "and" — ambas precisam ser verdadeiras
    if player has permission "builder" and player's gamemode is survival:
        send "&aYou can break blocks here." to player

    # "or" — basta uma ser verdadeira
    if player is op or player has permission "admin.bypass":
        send "&7Breaking restricted block..." to player

    # "not" — inverte a condição
    if player doesn't have permission "vip":
        send "&cOnly VIPs can do this!" to player
        cancel event
```

---

### chance of — Probabilidade

```vb
on death of player:
    chance of 50%:
        send "&aYou got lucky! Keeping your XP." to player
        # jogador mantém xp
    else:
        send "&cYou lost your XP." to player

on break of stone:
    chance of 5%:
        drop 1 emerald at location of event-block
        send "&2&lRare drop!" to player
```

---

## Módulo 4 — Efeitos (Effects)

Efeitos são as ações que o Skript executa quando todas as condições são verdadeiras.

### Mensagens

```vb
on join:
    # Enviar para o jogador
    send "Hello!" to player

    # Enviar para todos
    broadcast "A new player joined!"

    # Enviar para jogadores com permissão
    send "Staff alert: %player% joined!" to all players where [input has permission "staff.alerts"]

    # Título na tela
    send title "&aWelcome!" with subtitle "&7To our server" to player

    # Actionbar (texto abaixo do hotbar)
    send actionbar "&eLives: 3" to player

    # Mensagem no chat do servidor (console)
    log "Player %player% joined from %player's ip%"
```

---

### Itens e Inventário

```vb
command /kit-starter:
    trigger:
        # Dar itens
        give player iron sword named "&7Starter Sword"
        give player 64 bread
        give player iron chestplate

        # Dar item com encantamento
        give player diamond sword of sharpness 5 named "&bSharp Blade"

        # Remover itens
        remove 1 diamond from player

        # Limpar inventário
        clear player's inventory

        # Verificar e usar item
        if player's tool is a diamond pickaxe:
            send "&bNice pickaxe!" to player
```

---

### Teleporte e Localização

```vb
command /spawn:
    trigger:
        teleport player to spawn of world "world"

command /top:
    trigger:
        teleport player to highest block at player's location
        send "&aYou were teleported to the top!" to player

command /back:
    trigger:
        if {back::%player's uuid%} is set:
            teleport player to {back::%player's uuid%}
        else:
            send "&cNo location saved." to player

on death of player:
    set {back::%player's uuid%} to player's location
```

---

### Efeitos de Poção

```vb
on join:
    apply speed 2 to player for 30 seconds
    apply saturation 1 to player for 1 minute

command /heal:
    trigger:
        heal player
        feed player
        remove all potion effects from player
        send "&aYou were healed!" to player

on break of beacon:
    apply resistance 5 to all players in radius 10 around event-block for 10 seconds
```

---

### Sons e Partículas

```vb
on join:
    play sound "entity.player.levelup" at player with volume 1 and pitch 1

command /firework:
    trigger:
        launch firework colored red and yellow at player
        send "&cBoom!" to player

on kill:
    # Efeitos visuais
    play 20 flame around victim with offset vector(0.5, 0.5, 0.5)
    play sound "entity.firework_rocket.blast" at victim
```

---

### Modificar Mundo

```vb
command /setblock <material>:
    trigger:
        set block at player's target block to arg-1

# Criar explosão
on damage of player:
    if player's health < 2:
        create an explosion of force 3 at player

# Enviar raio
command /lightning <player>:
    trigger:
        strike lightning at arg-1
```

---

## Módulo 5 — Variáveis (Variables)

Em Skript, variáveis são representadas por um nome de variável entre duas chaves, como `{variavel}`. Variáveis podem ter quase qualquer nome.

### Tipos de Variáveis

```
{variavel}         → Global: salva no disco, persiste entre restarts
{_variavel}        → Local: existe só no bloco atual, não é salva
{variavel::*}      → Lista: armazena múltiplos valores
{@opcao}           → Option: constante definida na seção options:
```

---

### Variáveis Globais

Salvas em disco e disponíveis em qualquer parte do script:

```vb
# Contando quantas vezes o jogador entrou
on join:
    add 1 to {joins::%player's uuid%}
    send "&7This is your visit number &e%{joins::%player's uuid%}%" to player

# Sistema de moedas simples
command /addcoins <player> <number>:
    permission: admin.coins
    trigger:
        add arg-2 to {coins::%arg-1's uuid%}
        send "&aAdded &e%arg-2% coins &ato %arg-1%!" to sender

command /coins:
    trigger:
        if {coins::%player's uuid%} is not set:
            set {coins::%player's uuid%} to 0
        send "&eYour coins: &6%{coins::%player's uuid%}%" to player
```

---

### Variáveis Locais

Variáveis locais são usadas quando você só quer usar uma variável por um momento e não precisa salvá-la. Para indicar que uma variável é local, use `{_variavel}` com o underscore no início.

```vb
command /media <number> <number> <number>:
    trigger:
        set {_soma} to (arg-1 + arg-2 + arg-3)
        set {_media} to {_soma} / 3
        send "&eAverage: &a%{_media}%" to player
        # {_soma} e {_media} desaparecem depois deste comando
```

---

### Variáveis de Lista

Armazenam múltiplos valores indexados:

```vb
# Adicionar à lista
command /addvip <player>:
    permission: admin
    trigger:
        add arg-1's uuid to {vips::*}
        send "&a%arg-1% added to VIP list!" to sender

# Verificar se está na lista
on join:
    if player's uuid is in {vips::*}:
        send "&6Welcome back, VIP!" to player

# Remover da lista
command /removevip <player>:
    trigger:
        remove arg-1's uuid from {vips::*}

# Listar todos
command /listvips:
    trigger:
        send "&6=== VIP List ===" to player
        loop {vips::*}:
            send "&e- %loop-value%" to player
```

---

### Deletar Variáveis

```vb
# Deletar uma variável
delete {coins::%player's uuid%}

# Deletar lista inteira
delete {vips::*}

# Verificar se está definida
if {coins::%player's uuid%} is set:
    send "You have coins!" to player
else:
    send "No coins registered." to player
```

---

### Operações com Variáveis

```vb
on join:
    # Definir valor
    set {_x} to 10

    # Adicionar
    add 5 to {_x}          # {_x} = 15

    # Subtrair
    remove 3 from {_x}     # {_x} = 12

    # Multiplicar
    set {_x} to {_x} * 2  # {_x} = 24

    # Dividir
    set {_x} to {_x} / 4  # {_x} = 6
```

---

## Módulo 6 — Comandos Customizados

A estrutura completa de um comando no Skript é:
```
command /<nome> <argumentos>:
    aliases:           # nomes alternativos
    executable by:     # players ou console
    usage:             # mensagem de uso
    description:       # descrição do comando
    permission:        # permissão necessária
    permission message: # mensagem sem permissão
    cooldown:          # tempo de recarga
    cooldown message:  # mensagem de cooldown
    trigger:           # código a executar
```


### Comando Básico

```vb
command /oi:
    description: Sends a greeting
    executable by: players
    trigger:
        send "&aHello, %player%!" to player
```

---

### Comando com Argumentos

```vb
# Argumento obrigatório
command /heal <player>:
    permission: admin.heal
    permission message: "&cYou don't have permission!"
    trigger:
        heal arg-1
        feed arg-1
        send "&aYou were healed!" to arg-1
        send "&aYou healed %arg-1%!" to player

# Argumento opcional com valor padrão
command /fly [<player=%player%>]:
    permission: admin.fly
    trigger:
        if arg-1's flight mode is false:
            set arg-1's flight mode to true
            send "&aFlight enabled for %arg-1%!" to player
        else:
            set arg-1's flight mode to false
            send "&cFlight disabled for %arg-1%!" to player
```

---

### Argumentos Tipados

```vb
# Aceita apenas números
command /givexp <integer>:
    trigger:
        give arg-1 experience levels to player
        send "&aGained %arg-1% XP levels!" to player

# Aceita texto
command /nick <text>:
    trigger:
        set display name of player to "%arg-1%"
        send "&aYour nickname is now: &f%arg-1%" to player

# Aceita item
command /drop <item>:
    trigger:
        drop arg-1 at player

# Múltiplos tipos
command /tp <player> [to] <player>:
    trigger:
        teleport arg-1 to arg-2
        send "&aTeleported %arg-1% to %arg-2%!" to player
```

---

### Comandos com Cooldown

```vb
command /kit:
    cooldown: 24 hours
    cooldown message: "&cYou can use /kit again in &e%remaining time%!"
    cooldown bypass: vip.kit.bypass
    cooldown storage: {kit.cooldown::%player's uuid%}
    trigger:
        give player 64 bread
        give player iron sword
        give player iron armor
        send "&aKit received!" to player
```

---

### Comando com Menu (Subcomandos)

```vb
command /admin <text> [<text>] [<player>]:
    permission: server.admin
    trigger:
        if arg-1 is "help":
            send "&6=== Admin Help ===" to player
            send "&e/admin kick <player>" to player
            send "&e/admin ban <player>" to player
            send "&e/admin heal <player>" to player

        else if arg-1 is "kick":
            if arg-3 is set:
                kick arg-3 due to "&cYou were kicked by %player%"
                send "&aKicked %arg-3%!" to player
            else:
                send "&cUsage: /admin kick <player>" to player

        else if arg-1 is "heal":
            if arg-3 is set:
                heal arg-3
                send "&aHealed %arg-3%!" to player
            else:
                heal player
                send "&aYou healed yourself!" to player

        else:
            send "&cUnknown subcommand. Use /admin help" to player
```

---

## Módulo 7 — Loops

Todos os valores que representam mais de um item — como 'all players', 'worlds', etc. — bem como variáveis de lista, podem ser percorridos com loop.

### loop X times

```vb
# Repetir um número fixo de vezes
command /countdown:
    trigger:
        loop 10 times:
            wait 1 second
            broadcast "&e%11 - loop-number% seconds remaining..."
        broadcast "&a&lGO!"
```

---

### loop all players

```vb
every 5 minutes:
    loop all players:
        send "&7[&eReminder&7] &fVote at vote.site.com!" to loop-player

# Aplicar efeito para todos
command /buffAll:
    permission: admin
    trigger:
        loop all players:
            apply speed 2 to loop-player for 30 seconds
        broadcast "&aSpeed boost activated for everyone!"
```

---

### loop em lista de valores

```vb
# Percorrer uma lista específica de itens
command /checkarmor:
    trigger:
        loop helmet, chestplate, leggings and boots of player:
            if loop-item is air:
                send "&cYou're missing: &e%loop-item type%" to player
```

---

### loop em variável de lista

```vb
command /warp list:
    trigger:
        send "&6=== Available Warps ===" to player
        loop {warps::*}:
            send "&e➤ %loop-index%" to player
            # loop-index = nome do warp (chave)
            # loop-value = localização (valor)
```

---

### while loop

```vb
# Repete enquanto condição for verdadeira
# ⚠️ CUIDADO: while sem delay trava o servidor!
on load:
    set {_contador} to 0
    while {_contador} < 5:
        add 1 to {_contador}
        broadcast "Contagem: %{_contador}%"
        wait 1 tick   # SEMPRE use wait em while loops!
```

---

### Controle de Loop: stop loop / continue

```vb
# "stop loop" — sai do loop completamente (equivale ao break)
command /find <player>:
    trigger:
        loop all players:
            if loop-player's name is arg-1:
                send "&aFound %loop-player%!" to player
                stop loop
        send "&cPlayer not found." to player

# "continue" — pula para a próxima iteração
loop all players:
    if loop-player is in gamemode creative:
        continue    # pula jogadores em criativo
    send "&7Reminder: PvP enabled!" to loop-player
```

---

## Módulo 8 — Funções

Funções são uma forma útil de criar seções de código reutilizáveis. Se você tem código que é frequentemente repetido, em vez de copiar e colar em muitos lugares, você pode colocar em uma função e chamá-la quando precisar.

### Função Básica (sem retorno)

```vb
# Definindo a função
function sendTitle(p: player, title: text, sub: text):
    send title {_title} with subtitle {_sub} to {_p}
    wait 3 seconds
    send title "" with subtitle "" to {_p}

# Usando a função
on join:
    sendTitle(player, "&aWelcome!", "&7To our server")

on level change:
    if new level is 10:
        sendTitle(player, "&6Level 10!", "&eYou're growing strong!")
```

---

### Função com Retorno

```vb
# Retorna o rank do jogador como texto
function getRank(p: player) :: text:
    if {_p} has permission "rank.dono":
        return "&4[DONO]"
    else if {_p} has permission "rank.admin":
        return "&c[ADMIN]"
    else if {_p} has permission "rank.mod":
        return "&9[MOD]"
    else if {_p} has permission "rank.vip":
        return "&6[VIP]"
    else:
        return "&7[PLAYER]"

# Usando a função
on chat:
    set chat format to "%getRank(player)% &f%player% &8» &f%message%"
```

---

### Função com Parâmetro Padrão

```vb
# Parâmetro com valor padrão (opcional)
function broadcast(msg: text, prefix: text = "&8[&6Server&8]&r"):
    broadcast "%{_prefix}% %{_msg}%"

# Chamadas:
broadcast("Server will restart in 5 minutes!")
broadcast("Welcome to the event!", "&8[&bEvent&8]&r")
```

---

### Função para Verificar Lista

```vb
# Verifica se um valor está em uma lista
function listContains(list: objects, value: object) :: boolean:
    loop {_list::*}:
        if loop-value is {_value}:
            return true
    return false

# Uso:
set {_frutas::*} to "apple", "banana" and "mango"

if listContains({_frutas::*}, "apple") is true:
    send "Apple found!" to player
```

---

### Função Recursiva

```vb
# Calcula fatorial recursivamente
function fatorial(n: number) :: number:
    if {_n} <= 1:
        return 1
    return {_n} * fatorial({_n} - 1)

command /fatorial <integer>:
    trigger:
        send "&e%arg-1%! = &a%fatorial(arg-1)%" to player
```

---

## Módulo 9 — Formatação de Mensagens

### Códigos de Cor (Legacy)

```vb
# Prefixo: & seguido do código
send "&aVerde"
send "&bCiano"
send "&cVermelho"
send "&dRosa"
send "&eAmarelo"
send "&fBranco"
send "&7Cinza"
send "&8Cinza escuro"
send "&9Azul"
send "&0Preto"

# Formatação
send "&lNegrito"
send "&oItálico"
send "&nSublinhado"
send "&mRiscado"
send "&kObfuscado (texto aleatório)"
send "&rReset"

# Combinando
send "&a&lTexto verde negrito"
send "&c&lErro: &r&csomething went wrong"
```

---

### Cores Hex (1.16+)

```vb
# Formato: ##RRGGBB (dois # no Skript)
send "##FF5733Texto laranja" to player
send "##00FF88Texto verde neon" to player

# Gradiente manual
send "##FF0000R##FF4400e##FF8800d##FFCC00" to player
```

---

### Expressões em Mensagens

```vb
# Use % % ao redor de expressões para mostrar seu valor
on join:
    send "Welcome &e%player%&f! Online: &e%size of all players%" to player
    send "Your health: &c%player's health%&f/&c20" to player
    send "Location: &7%player's x-coordinate%, %player's y-coordinate%, %player's z-coordinate%" to player
```

---

### Mensagens Fancy com Newline

```vb
on join:
    send "" to player
    send "&8&m-----------------------------" to player
    send "&6&l    Welcome to ServerName!" to player
    send "" to player
    send "&7  Players online: &e%size of all players%" to player
    send "&7  Your rank: &e%getRank(player)%" to player
    send "" to player
    send "&8&m-----------------------------" to player
    send "" to player
```

---

## Módulo 10 — Projetos Completos

### 🏠 Sistema de /sethome e /home

```vb
# Sistema completo de homes por jogador
# Permite múltiplos homes para VIPs

options:
    max-homes-default: 1
    max-homes-vip: 5
    prefix: &8[&6Home&8]&r

function getMaxHomes(p: player) :: integer:
    if {_p} has permission "vip.homes":
        return {@max-homes-vip}
    return {@max-homes-default}

command /sethome [<text=default>]:
    executable by: players
    trigger:
        set {_homeName} to arg-1
        set {_max} to getMaxHomes(player)
        set {_count} to size of {homes::%player's uuid%::*}

        if {homes::%player's uuid%::%{_homeName}%} is set:
            set {homes::%player's uuid%::%{_homeName}%} to player's location
            send "{@prefix} &aHome &e%{_homeName}% &aupdated!" to player
        else if {_count} >= {_max}:
            send "{@prefix} &cYou can only have &e%{_max}% &chome(s)!" to player
        else:
            set {homes::%player's uuid%::%{_homeName}%} to player's location
            send "{@prefix} &aHome &e%{_homeName}% &aset!" to player

command /home [<text=default>]:
    executable by: players
    trigger:
        set {_homeName} to arg-1
        if {homes::%player's uuid%::%{_homeName}%} is set:
            teleport player to {homes::%player's uuid%::%{_homeName}%}
            send "{@prefix} &aTeleported to &e%{_homeName}%!" to player
        else:
            send "{@prefix} &cHome &e%{_homeName}% &cnot found!" to player

command /delhome [<text=default>]:
    executable by: players
    trigger:
        set {_homeName} to arg-1
        if {homes::%player's uuid%::%{_homeName}%} is set:
            delete {homes::%player's uuid%::%{_homeName}%}
            send "{@prefix} &aHome &e%{_homeName}% &adeleted!" to player
        else:
            send "{@prefix} &cHome &e%{_homeName}% &cnot found!" to player

command /homes:
    executable by: players
    trigger:
        if {homes::%player's uuid%::*} is not set:
            send "{@prefix} &cYou have no homes set." to player
            stop
        send "{@prefix} &6Your homes:" to player
        loop {homes::%player's uuid%::*}:
            send " &e➤ %loop-index%" to player
```

---

### ⚔️ Sistema de PvP com Kit e Respawn

```vb
options:
    arena-world: pvp-arena
    spawn-location: pvp-arena, 0, 65, 0

on join:
    if player's world is world({@arena-world}):
        teleport player to location({@spawn-location})
        giveKit(player)

function giveKit(p: player):
    clear {_p}'s inventory
    give {_p} diamond sword of sharpness 3 named "&bArena Sword"
    give {_p} 1 diamond chestplate of protection 2
    give {_p} 1 diamond leggings of protection 2
    give {_p} 1 diamond helmet of protection 2
    give {_p} 1 diamond boots of protection 2
    give {_p} 10 golden apple
    apply speed 1 to {_p} for 5 seconds

on death of player:
    if player's world is world({@arena-world}):
        add 1 to {arena.deaths::%player's uuid%}

        if attacker is a player:
            add 1 to {arena.kills::%attacker's uuid%}
            send "&c%player% &7was killed by &e%attacker%!" to all players

        wait 3 seconds
        respawn player
        teleport player to location({@spawn-location})
        giveKit(player)
        send "&aYou respawned! Use your kit wisely." to player

command /stats [<player=%player%>]:
    trigger:
        set {_p} to arg-1
        set {_k} to {arena.kills::%{_p}'s uuid%} ? 0
        set {_d} to {arena.deaths::%{_p}'s uuid%} ? 0
        send "&6=== Stats: %{_p}% ===" to player
        send "&aKills: &e%{_k}%" to player
        send "&cDeaths: &e%{_d}%" to player
```

---

### 💰 Sistema de Economia Simples

```vb
options:
    prefix: &8[&6Economy&8]&r
    starting-balance: 100

# Garante saldo inicial
on join:
    if {eco::%player's uuid%} is not set:
        set {eco::%player's uuid%} to {@starting-balance}
        send "{@prefix} &aYou received &e$%{@starting-balance}% &ato get started!" to player

command /balance [<player=%player%>]:
    aliases: /bal, /money
    executable by: players
    trigger:
        set {_p} to arg-1
        if {_p} is player:
            send "{@prefix} &aYour balance: &e$%{eco::%player's uuid%}%" to player
        else:
            if player has permission "eco.admin":
                send "{@prefix} &e%{_p}%'s &abalance: &e$%{eco::%{_p}'s uuid%}%" to player
            else:
                send "{@prefix} &cNo permission." to player

command /pay <player> <number>:
    executable by: players
    trigger:
        set {_amount} to arg-2
        if {_amount} <= 0:
            send "{@prefix} &cAmount must be positive!" to player
            stop
        if {eco::%player's uuid%} < {_amount}:
            send "{@prefix} &cInsufficient funds!" to player
            stop
        remove {_amount} from {eco::%player's uuid%}
        add {_amount} to {eco::%arg-1's uuid%}
        send "{@prefix} &aSent &e$%{_amount}% &ato &e%arg-1%!" to player
        send "{@prefix} &e%player% &asent you &e$%{_amount}%!" to arg-1

command /eco <give/take/set> <player> <number>:
    permission: eco.admin
    trigger:
        if arg-1 is "give":
            add arg-3 to {eco::%arg-2's uuid%}
            send "{@prefix} &aGave &e$%arg-3% &ato &e%arg-2%!" to player
        else if arg-1 is "take":
            remove arg-3 from {eco::%arg-2's uuid%}
            send "{@prefix} &cTook &e$%arg-3% &cfrom &e%arg-2%!" to player
        else if arg-1 is "set":
            set {eco::%arg-2's uuid%} to arg-3
            send "{@prefix} &aSet &e%arg-2%'s &abalance to &e$%arg-3%!" to player
```

---

### 🎯 Sistema de Rank por Kills (automático)

```vb
options:
    prefix: &8[&6Rank&8]&r

function checkRankUp(p: player):
    set {_kills} to {kills::%{_p}'s uuid%} ? 0

    if {_kills} >= 100:
        if {rank::%{_p}'s uuid%} is not "legend":
            set {rank::%{_p}'s uuid%} to "legend"
            broadcast "{@prefix} &d%{_p}% &7reached rank &d&lLEGEND&7! (%{_kills}% kills)"
    else if {_kills} >= 50:
        if {rank::%{_p}'s uuid%} is not "diamond":
            set {rank::%{_p}'s uuid%} to "diamond"
            broadcast "{@prefix} &b%{_p}% &7reached rank &b&lDIAMOND&7! (%{_kills}% kills)"
    else if {_kills} >= 25:
        if {rank::%{_p}'s uuid%} is not "gold":
            set {rank::%{_p}'s uuid%} to "gold"
            broadcast "{@prefix} &e%{_p}% &7reached rank &e&lGOLD&7! (%{_kills}% kills)"
    else if {_kills} >= 10:
        if {rank::%{_p}'s uuid%} is not "iron":
            set {rank::%{_p}'s uuid%} to "iron"
            broadcast "{@prefix} &7%{_p}% reached rank &7&lIRON&7! (%{_kills}% kills)"

on death of player:
    if attacker is a player:
        add 1 to {kills::%attacker's uuid%}
        add 1 to {deaths::%player's uuid%}
        send "&a+1 Kill! Total: &e%{kills::%attacker's uuid%}%" to attacker
        checkRankUp(attacker)

command /rank [<player=%player%>]:
    trigger:
        set {_p} to arg-1
        set {_k} to {kills::%{_p}'s uuid%} ? 0
        set {_d} to {deaths::%{_p}'s uuid%} ? 0
        set {_r} to {rank::%{_p}'s uuid%} ? "rookie"
        send "&6=== %{_p}%'s Rank ===" to player
        send "&7Rank: &e%{_r}%" to player
        send "&aKills: &e%{_k}% &7| &cDeaths: &e%{_d}%" to player
```

---

## 🧩 Addons Populares

Addons são plugins separados escritos por outros desenvolvedores para adicionar mais funcionalidade ao Skript. Por exemplo, você pode usar bancos de dados, criar bots do Discord, enviar requisições web, gerenciar outros plugins como Citizens e WorldGuard, reproduzir efeitos de partículas e muito mais com os addons.

| Addon | Para que serve | Link |
|---|---|---|
| **SkBee** | Bossbars, scoreboards, NBT, estruturas | [GitHub](https://github.com/ShaneBeee/SkBee) |
| **Skript-reflect** | Acesso direto à API Java | [GitHub](https://github.com/SkriptLang/skript-reflect) |
| **SkQuery** | Efeitos extras, GUIs, scoreboards | [GitHub](https://github.com/SkQuery/SkQuery) |
| **Skellett** | Chat, GUIs, títulos avançados | [SpigotMC](https://www.spigotmc.org/resources/skellett.34361/) |
| **TuSKe** | GUIs (menus de inventário) | [GitHub](https://github.com/Tuke-Nuke/TuSKe) |
| **skDragon** | Partículas e efeitos visuais | [SpigotMC](https://www.spigotmc.org/resources/skdragon.26356/) |
| **skRayFall** | Scoreboards, NPC, holograma | [GitHub](https://github.com/eyesniper2/skRayFall) |

### Exemplo com SkBee — Scoreboard

```vb
# Requer addon SkBee
on join:
    create scoreboard with id "sidebar" for player:
        title: "&6&l MyServer"
        blank line
        line: " &7Rank: &e%getRank(player)%"
        line: " &7Kills: &a%{kills::%player's uuid%} ? 0%"
        line: " &7Deaths: &c%{deaths::%player's uuid%} ? 0%"
        blank line
        line: " &7Online: &e%size of all players%"
        blank line
        line: " &fplay.servidor.com"
```

---

## ❗ Erros Comuns e Soluções

### Erro de Indentação

```vb
# ❌ Errado — misturando tabs e espaços
on join:
	send "tab" to player  # tab
    send "space" to player  # 4 espaços

# ✅ Correto — consistente com 4 espaços
on join:
    send "ok" to player
    send "ok" to player
```

---

### Variável não salva entre restarts

```vb
# ❌ Errado — variável local não persiste
on join:
    set {_coins} to 100  # local, some quando o script descarrega

# ✅ Correto — variável global persiste no disco
on join:
    if {coins::%player's uuid%} is not set:
        set {coins::%player's uuid%} to 100
```

---

### While loop travando o servidor

```vb
# ❌ PERIGOSO — trava o servidor (sem delay)
while {active} is true:
    send "tick" to all players

# ✅ Correto — sempre use wait em while loops!
while {active} is true:
    send "tick" to all players
    wait 1 tick
```

---

### Erro ao comparar com null / não definido

```vb
# ❌ Erro — comparar variável que pode ser null
if {coins::%player's uuid%} > 0:  # crashar se não definida

# ✅ Correto — use "? valor padrão" para fallback
if {coins::%player's uuid%} ? 0 > 0:

# Ou verifique antes:
if {coins::%player's uuid%} is set:
    if {coins::%player's uuid%} > 0:
        send "You have coins!" to player
```

---

### Esquecer de recarregar o script

```
# Após editar qualquer arquivo .sk:
/skript reload <nome-do-arquivo>
# ou
/skript reload all
```

---

### Tipos de erros na inicialização

```
# No console você verá:
[Skript] ERROR in meu-script.sk (line 5):
  Can't understand this condition/effect: ...

# Significa: Skript não entendeu a linha
# Verifique: ortografia, indentação, sintaxe correta
```

---

## 🚀 Cheatsheet Skript

```vb
# === COMENTÁRIOS ===
# comentário de linha
## também comentário

# === EVENTOS COMUNS ===
on join:
on quit:
on death of player:
on break of <block>:
on place of <block>:
on right click on <block>:
on damage of player:
on chat:
every <time>:
on load:

# === CONDIÇÕES ===
if <condição>:
else if <condição>:
else:

player has permission "perm"
player is op
player's health > 10
player's gamemode is survival
player has 5 diamonds
{variavel} is set
{variavel} is not set
<x> is in {lista::*}
chance of 50%:

# === EFEITOS COMUNS ===
send "mensagem" to player
broadcast "mensagem"
send title "título" with subtitle "sub" to player
send actionbar "texto" to player
give player <item>
remove <item> from player
clear player's inventory
teleport player to <location>
heal player
feed player
kill player
kick player due to "motivo"
ban player due to "motivo"
cancel event
set block at <loc> to <material>
apply <potion> to player for <time>
play sound "<som>" at player
strike lightning at player

# === VARIÁVEIS ===
set {var} to <valor>
set {_local} to <valor>
add 1 to {var}
remove 1 from {var}
delete {var}
{var} ? 0              # valor padrão se não definida

# === LISTAS ===
add <valor> to {lista::*}
remove <valor> from {lista::*}
delete {lista::*}
size of {lista::*}
loop {lista::*}: ... loop-value ... loop-index

# === LOOPS ===
loop 10 times:          # loop-number = iteração atual
loop all players:       # loop-player
loop <lista>::*:        # loop-value, loop-index
while <condição>:       # SEMPRE use wait!

# === FUNÇÕES ===
function nome(param: tipo) :: retorno:
    return <valor>

# === COMANDOS ===
command /nome <tipo> [<opcional>]:
    aliases: /outro
    permission: perm.aqui
    cooldown: 1 hour
    executable by: players
    trigger:
        # código aqui
        arg-1, arg-2  ← acessar argumentos

# === CORES ===
&a verde        &b ciano       &c vermelho
&d rosa         &e amarelo     &f branco
&7 cinza        &8 cinza esc.  &0 preto
&l negrito      &o itálico     &r reset
##RRGGBB hex color (1.16+)

# === UTILITÁRIOS ===
player's uuid
player's name
player's location
location of player
player's world
size of all players
now                    ← data/hora atual
wait 1 second
wait 5 ticks
```

---

## 📚 Recursos e Comunidade

| Recurso | Tipo | Link |
|---|---|---|
| **Documentação Oficial** | Docs completa | [docs.skriptlang.org](https://docs.skriptlang.org) |
| **SkriptHub** | Docs + Addons + Tutoriais | [skripthub.net](https://skripthub.net) |
| **skUnity** | Fórum + Scripts prontos | [skunity.com](https://skunity.com) |
| **GitHub do Skript** | Código fonte e issues | [github.com/SkriptLang/Skript](https://github.com/SkriptLang/Skript) |
| **Paper (servidor)** | Download do servidor | [papermc.io](https://papermc.io) |

### 🏁 Desafios para praticar

- [ ] Crie um sistema de `/warp` com lista e teleporte
- [ ] Faça um sistema de `/report` que notifica os admins online
- [ ] Crie um kit PvP com cooldown de 24 horas
- [ ] Implemente um placar de kills com `/top kills`
- [ ] Crie uma loja com menu de inventário (com addon TuSKe ou SkBee)
- [ ] Faça um mini-game de Spleef com arena, placar e respawn
- [ ] Crie um sistema de clans/guilds com base em variáveis de lista

---

<div align="center">

**Feito com ❤️ e muitos `/skript reload all`**

*"O melhor jeito de aprender Skript é errar, ler o erro no console, corrigir e tentar de novo."*

⭐ Se este curso te ajudou, dê uma estrela no repositório!

</div>
