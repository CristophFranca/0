# 🗄️ Curso Completo de SQL — Essencial para TI

> **Do zero ao avançado** — aprenda SQL com foco em **análise de dados**, consultas reais do dia a dia de TI, troubleshooting de sistemas e geração de relatórios. Exemplos práticos com cenários reais de suporte, infraestrutura, desenvolvimento e gestão.

> 💡 **Banco usado nos exemplos:** Os exemplos funcionam em **PostgreSQL**, **MySQL** e **SQLite** com pequenas variações indicadas. Use [sqliteonline.com](https://sqliteonline.com) para praticar agora, sem instalar nada.

---

## 📋 Índice

1. [O que é SQL e por que TI precisa saber?](#-o-que-é-sql-e-por-que-ti-precisa-saber)
2. [Conceitos Fundamentais](#-conceitos-fundamentais)
3. [Módulo 1 — SELECT: Consultando Dados](#módulo-1--select-consultando-dados)
4. [Módulo 2 — WHERE: Filtrando Dados](#módulo-2--where-filtrando-dados)
5. [Módulo 3 — ORDER BY, LIMIT e OFFSET](#módulo-3--order-by-limit-e-offset)
6. [Módulo 4 — Funções de Agregação](#módulo-4--funções-de-agregação)
7. [Módulo 5 — GROUP BY e HAVING](#módulo-5--group-by-e-having)
8. [Módulo 6 — JOINs: Cruzando Tabelas](#módulo-6--joins-cruzando-tabelas)
9. [Módulo 7 — Subqueries](#módulo-7--subqueries)
10. [Módulo 8 — Manipulando Dados (DML)](#módulo-8--manipulando-dados-dml)
11. [Módulo 9 — Criando Estruturas (DDL)](#módulo-9--criando-estruturas-ddl)
12. [Módulo 10 — Funções Essenciais](#módulo-10--funções-essenciais)
13. [Módulo 11 — Window Functions](#módulo-11--window-functions)
14. [Módulo 12 — CTEs e Queries Complexas](#módulo-12--ctes-e-queries-complexas)
15. [Módulo 13 — Performance e Índices](#módulo-13--performance-e-índices)
16. [Módulo 14 — Casos Reais de TI](#módulo-14--casos-reais-de-ti)
17. [Cheatsheet SQL](#-cheatsheet-sql)

---

## 🤔 O que é SQL e por que TI precisa saber?

**SQL (Structured Query Language)** é a linguagem padrão para interagir com bancos de dados relacionais. Ela permite consultar, inserir, atualizar e deletar dados de forma precisa e eficiente.

### Por que SQL é essencial para TI?

Não importa se você é desenvolvedor, analista, DBA, suporte ou DevOps — você vai precisar de SQL em algum momento:

| Área de TI | Uso do SQL |
|---|---|
| **Suporte / Help Desk** | Consultar tickets, usuários, logs de acesso |
| **Desenvolvimento** | Depurar dados, entender o modelo de dados |
| **DevOps / Infra** | Monitorar métricas, analisar logs de sistema |
| **Analista de Dados** | Gerar relatórios, KPIs, dashboards |
| **DBA** | Manutenção, performance, backups |
| **Segurança (SecOps)** | Auditar acessos, detectar anomalias |
| **Gestão de TI** | Relatórios de SLA, produtividade da equipe |

### O modelo mental do SQL

```
┌────────────────────────────────────────────────┐
│              BANCO DE DADOS                    │
│                                                │
│  ┌──────────────┐    ┌──────────────┐          │
│  │   TABELA     │    │   TABELA     │          │
│  │  usuarios    │    │   tickets    │          │
│  │─────────────│    │──────────────│          │
│  │ id           │◄───│ usuario_id   │          │
│  │ nome         │    │ titulo       │          │
│  │ email        │    │ status       │          │
│  │ departamento │    │ criado_em    │          │
│  └──────────────┘    └──────────────┘          │
└────────────────────────────────────────────────┘

SQL = linguagem para fazer perguntas ao banco:
"Quais usuários abriram mais de 5 tickets em aberto?"
```

---

## 📐 Conceitos Fundamentais

### Tipos de Comandos SQL

```
DDL — Data Definition Language   → estrutura do banco
  CREATE, ALTER, DROP, TRUNCATE

DML — Data Manipulation Language → os dados em si
  SELECT, INSERT, UPDATE, DELETE

DCL — Data Control Language      → permissões
  GRANT, REVOKE

TCL — Transaction Control Language → transações
  BEGIN, COMMIT, ROLLBACK
```

---

### Tipos de Dados Mais Comuns

| Tipo | Exemplos | Uso |
|---|---|---|
| `INT` / `INTEGER` | `1`, `42`, `-5` | IDs, contadores, versões |
| `BIGINT` | `9999999999` | IDs grandes, timestamps Unix |
| `DECIMAL(10,2)` | `1999.99` | Valores monetários |
| `FLOAT` / `REAL` | `3.14` | Métricas, percentuais |
| `VARCHAR(n)` | `"Ana"` | Textos de tamanho variável |
| `TEXT` | Textos longos | Descrições, logs, JSON |
| `BOOLEAN` | `TRUE`/`FALSE` | Flags, status |
| `DATE` | `2024-01-15` | Datas |
| `TIMESTAMP` | `2024-01-15 14:30:00` | Data + hora |
| `JSON` / `JSONB` | `{"key":"val"}` | Dados semiestruturados |

---

### As Tabelas que Usaremos

Vamos usar um banco de dados fictício de uma empresa de TI:

```sql
-- Estrutura simplificada do nosso banco de exemplo:

usuarios         → funcionários e clientes
tickets          → chamados de suporte
servidores       → infraestrutura
logs_acesso      → auditoria de acessos
deploys          → histórico de deployments
incidentes       → incidentes de produção
```

---

## Módulo 1 — SELECT: Consultando Dados

O `SELECT` é o comando mais usado em SQL. Ele recupera dados de uma ou mais tabelas.

### Sintaxe Completa (ordem importa!)

```sql
SELECT   colunas
FROM     tabela
WHERE    condição
GROUP BY agrupamento
HAVING   condição de grupo
ORDER BY ordenação
LIMIT    quantidade;
```

> ⚠️ **Regra de ouro:** Sempre termine seus comandos com `;` (ponto e vírgula).

---

### SELECT Básico

```sql
-- Todas as colunas (use com moderação — pesado em tabelas grandes!)
SELECT * FROM usuarios;

-- Colunas específicas (sempre preferível)
SELECT nome, email, departamento
FROM usuarios;

-- Com alias (apelido) para colunas
SELECT
    nome        AS "Nome Completo",
    email       AS "E-mail",
    departamento AS "Depto"
FROM usuarios;
```

---

### Expressões no SELECT

```sql
-- Cálculos diretos
SELECT
    nome,
    salario,
    salario * 0.11          AS desconto_inss,
    salario - (salario * 0.11) AS salario_liquido
FROM funcionarios;

-- Concatenar texto
SELECT
    nome || ' - ' || departamento AS identificacao   -- PostgreSQL / SQLite
    -- CONCAT(nome, ' - ', departamento)             -- MySQL
FROM usuarios;

-- Expressão condicional inline
SELECT
    nome,
    CASE
        WHEN nivel = 1 THEN 'Júnior'
        WHEN nivel = 2 THEN 'Pleno'
        WHEN nivel = 3 THEN 'Sênior'
        ELSE 'Indefinido'
    END AS nivel_cargo
FROM funcionarios;
```

---

### SELECT DISTINCT — Valores Únicos

```sql
-- Lista todos os departamentos sem repetir
SELECT DISTINCT departamento
FROM usuarios
ORDER BY departamento;

-- Combinação única
SELECT DISTINCT departamento, cargo
FROM usuarios
ORDER BY departamento, cargo;
```

---

## Módulo 2 — WHERE: Filtrando Dados

O `WHERE` filtra as linhas retornadas pelo `SELECT`.

### Operadores de Comparação

```sql
-- Igual
SELECT * FROM tickets WHERE status = 'aberto';

-- Diferente
SELECT * FROM tickets WHERE status != 'fechado';
SELECT * FROM tickets WHERE status <> 'fechado'; -- equivalente

-- Maior / Menor
SELECT * FROM servidores WHERE cpu_uso > 90;
SELECT * FROM servidores WHERE memoria_livre < 10;

-- Maior ou igual / Menor ou igual
SELECT * FROM tickets WHERE prioridade >= 3;
SELECT * FROM incidentes WHERE duracao_minutos <= 60;
```

---

### Operadores Lógicos: AND, OR, NOT

```sql
-- AND: ambas as condições precisam ser verdadeiras
SELECT * FROM tickets
WHERE status = 'aberto'
  AND prioridade = 'alta';

-- OR: pelo menos uma condição
SELECT * FROM servidores
WHERE ambiente = 'producao'
   OR ambiente = 'staging';

-- NOT: negação
SELECT * FROM usuarios
WHERE NOT departamento = 'TI';

-- Combinando (use parênteses para garantir a precedência!)
SELECT * FROM tickets
WHERE status = 'aberto'
  AND (prioridade = 'alta' OR prioridade = 'critica');
```

---

### BETWEEN — Intervalo

```sql
-- Valores numéricos
SELECT * FROM servidores
WHERE cpu_uso BETWEEN 70 AND 100;

-- Datas (extremamente útil em TI!)
SELECT * FROM logs_acesso
WHERE timestamp BETWEEN '2024-01-01' AND '2024-01-31';

-- NOT BETWEEN
SELECT * FROM tickets
WHERE id NOT BETWEEN 100 AND 200;
```

---

### IN — Lista de Valores

```sql
-- Em vez de múltiplos OR, use IN
SELECT * FROM servidores
WHERE ambiente IN ('producao', 'staging', 'homologacao');

-- NOT IN
SELECT * FROM usuarios
WHERE departamento NOT IN ('RH', 'Financeiro');

-- IN com subquery (veremos mais no Módulo 7)
SELECT * FROM tickets
WHERE usuario_id IN (
    SELECT id FROM usuarios WHERE departamento = 'TI'
);
```

---

### LIKE — Busca por Padrão de Texto

```sql
-- % = qualquer quantidade de caracteres
-- _ = exatamente um caractere

-- Começa com "erro"
SELECT * FROM logs WHERE mensagem LIKE 'erro%';

-- Contém "timeout"
SELECT * FROM logs WHERE mensagem LIKE '%timeout%';

-- Termina com ".com.br"
SELECT * FROM usuarios WHERE email LIKE '%.com.br';

-- Exatamente 3 caracteres
SELECT * FROM codigos WHERE codigo LIKE '___';

-- ILIKE = case insensitive (PostgreSQL)
SELECT * FROM usuarios WHERE nome ILIKE '%silva%';

-- Case insensitive no MySQL/SQLite:
SELECT * FROM usuarios WHERE LOWER(nome) LIKE '%silva%';
```

---

### IS NULL / IS NOT NULL

```sql
-- Registros sem data de resolução (tickets em aberto)
SELECT * FROM tickets
WHERE resolvido_em IS NULL;

-- Tickets que já foram resolvidos
SELECT * FROM tickets
WHERE resolvido_em IS NOT NULL;

-- ⚠️ NUNCA use = NULL. Isso não funciona em SQL!
-- ❌ WHERE resolvido_em = NULL  → nunca retorna nada
-- ✅ WHERE resolvido_em IS NULL → correto
```

---

### Filtros de Data — Essencial para TI

```sql
-- Tickets criados hoje
SELECT * FROM tickets
WHERE DATE(criado_em) = CURRENT_DATE;

-- Últimas 24 horas
SELECT * FROM logs_acesso
WHERE timestamp >= NOW() - INTERVAL '24 hours';   -- PostgreSQL
-- WHERE timestamp >= DATE_SUB(NOW(), INTERVAL 24 HOUR);  -- MySQL

-- Últimos 7 dias
SELECT * FROM incidentes
WHERE iniciado_em >= CURRENT_DATE - INTERVAL '7 days';

-- Mês atual
SELECT * FROM tickets
WHERE EXTRACT(MONTH FROM criado_em) = EXTRACT(MONTH FROM CURRENT_DATE)
  AND EXTRACT(YEAR  FROM criado_em) = EXTRACT(YEAR  FROM CURRENT_DATE);

-- Ano específico
SELECT * FROM deploys
WHERE EXTRACT(YEAR FROM realizado_em) = 2024;
```

---

## Módulo 3 — ORDER BY, LIMIT e OFFSET

### ORDER BY — Ordenando Resultados

```sql
-- Crescente (padrão)
SELECT * FROM tickets
ORDER BY criado_em ASC;

-- Decrescente (mais recentes primeiro)
SELECT * FROM tickets
ORDER BY criado_em DESC;

-- Múltiplas colunas
SELECT * FROM tickets
ORDER BY prioridade DESC, criado_em ASC;

-- Por posição da coluna (não recomendado, mas existe)
SELECT nome, email, departamento FROM usuarios
ORDER BY 3;  -- ordena pela 3ª coluna (departamento)
```

---

### LIMIT e OFFSET — Paginação

```sql
-- Apenas os 10 primeiros
SELECT * FROM logs ORDER BY timestamp DESC LIMIT 10;

-- Top 5 servidores com maior CPU
SELECT nome, cpu_uso
FROM servidores
ORDER BY cpu_uso DESC
LIMIT 5;

-- Paginação: página 2 de resultados (10 por página)
SELECT * FROM tickets
ORDER BY id
LIMIT 10 OFFSET 10;   -- pula os 10 primeiros, pega os próximos 10

-- Página 3
SELECT * FROM tickets
ORDER BY id
LIMIT 10 OFFSET 20;   -- fórmula: OFFSET = (página - 1) * limite
```

---

## Módulo 4 — Funções de Agregação

Funções de agregação calculam um valor a partir de múltiplas linhas.

### As 5 Funções Principais

```sql
-- COUNT — contar linhas
SELECT COUNT(*)           FROM tickets;               -- total de linhas
SELECT COUNT(id)          FROM tickets;               -- linhas com id não nulo
SELECT COUNT(DISTINCT usuario_id) FROM tickets;       -- usuários únicos

-- SUM — somar
SELECT SUM(duracao_minutos) FROM incidentes;
SELECT SUM(salario)         FROM funcionarios WHERE departamento = 'TI';

-- AVG — média
SELECT AVG(duracao_minutos) FROM incidentes;
SELECT ROUND(AVG(cpu_uso), 2) AS media_cpu FROM servidores;

-- MIN e MAX — menor e maior valor
SELECT MIN(criado_em) AS primeiro_ticket FROM tickets;
SELECT MAX(criado_em) AS ultimo_ticket   FROM tickets;
SELECT MIN(salario)   AS menor_salario   FROM funcionarios;
SELECT MAX(salario)   AS maior_salario   FROM funcionarios;
```

---

### Combinando Múltiplas Agregações

```sql
-- Resumo completo de tickets em uma só query
SELECT
    COUNT(*)                                    AS total_tickets,
    COUNT(CASE WHEN status = 'aberto'   THEN 1 END) AS abertos,
    COUNT(CASE WHEN status = 'fechado'  THEN 1 END) AS fechados,
    ROUND(AVG(
        EXTRACT(EPOCH FROM (resolvido_em - criado_em)) / 3600
    ), 1)                                       AS media_horas_resolucao
FROM tickets;
```

---

## Módulo 5 — GROUP BY e HAVING

### GROUP BY — Agrupando Resultados

```sql
-- Contagem de tickets por status
SELECT
    status,
    COUNT(*) AS total
FROM tickets
GROUP BY status
ORDER BY total DESC;

-- Resultado:
-- status   | total
-- ---------+-------
-- aberto   |   142
-- fechado  |   891
-- pausado  |    23

-- Total de tickets por usuário
SELECT
    usuario_id,
    COUNT(*)                AS total_tickets,
    AVG(duracao_resolucao)  AS media_resolucao
FROM tickets
GROUP BY usuario_id
ORDER BY total_tickets DESC;

-- Tickets por departamento e prioridade
SELECT
    departamento,
    prioridade,
    COUNT(*) AS total
FROM tickets
JOIN usuarios ON tickets.usuario_id = usuarios.id
GROUP BY departamento, prioridade
ORDER BY departamento, prioridade;
```

---

### HAVING — Filtrando Grupos

`WHERE` filtra linhas antes de agrupar. `HAVING` filtra grupos depois de agrupar.

```sql
-- Usuários com mais de 10 tickets abertos
SELECT
    usuario_id,
    COUNT(*) AS total_abertos
FROM tickets
WHERE status = 'aberto'        -- filtra linhas ANTES de agrupar
GROUP BY usuario_id
HAVING COUNT(*) > 10           -- filtra grupos DEPOIS de agrupar
ORDER BY total_abertos DESC;

-- Departamentos com média de salário acima de 8000
SELECT
    departamento,
    ROUND(AVG(salario), 2) AS media_salarial,
    COUNT(*) AS funcionarios
FROM funcionarios
GROUP BY departamento
HAVING AVG(salario) > 8000
ORDER BY media_salarial DESC;
```

---

### WHERE vs HAVING — A Diferença Visual

```
Fluxo de execução:
  FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT

WHERE  = filtra LINHAS individuais (antes de agrupar)
HAVING = filtra GRUPOS (depois de agrupar)
```

```sql
-- ❌ Erro: não pode usar alias do SELECT no WHERE
SELECT status, COUNT(*) AS total
FROM tickets
WHERE total > 10     -- erro! "total" não existe ainda aqui
GROUP BY status;

-- ✅ Correto: usa HAVING para filtrar o resultado agregado
SELECT status, COUNT(*) AS total
FROM tickets
GROUP BY status
HAVING COUNT(*) > 10;
```

---

## Módulo 6 — JOINs: Cruzando Tabelas

JOINs combinam dados de duas ou mais tabelas com base em uma relação entre elas.

### Tipos de JOIN

```
INNER JOIN  → Apenas registros que existem em AMBAS as tabelas
LEFT JOIN   → Todos da esquerda + correspondentes da direita (null se não tiver)
RIGHT JOIN  → Todos da direita + correspondentes da esquerda
FULL JOIN   → Todos de ambas (com null onde não há correspondência)
CROSS JOIN  → Produto cartesiano (todas as combinações possíveis)
```

---

### INNER JOIN — A Base

```sql
-- Tickets com nome do usuário
SELECT
    t.id,
    t.titulo,
    t.status,
    u.nome       AS usuario,
    u.departamento
FROM tickets t
INNER JOIN usuarios u ON t.usuario_id = u.id
WHERE t.status = 'aberto'
ORDER BY t.criado_em DESC;

-- Alias de tabela (t, u) deixa a query mais limpa
-- ON define a relação entre as tabelas
```

---

### LEFT JOIN — Incluir Registros Sem Par

```sql
-- Todos os usuários, mesmo os que nunca abriram ticket
SELECT
    u.nome,
    u.departamento,
    COUNT(t.id) AS total_tickets
FROM usuarios u
LEFT JOIN tickets t ON u.id = t.usuario_id
GROUP BY u.id, u.nome, u.departamento
ORDER BY total_tickets DESC;

-- Usuários que NUNCA abriram ticket
SELECT u.nome, u.email
FROM usuarios u
LEFT JOIN tickets t ON u.id = t.usuario_id
WHERE t.id IS NULL;   -- null = sem correspondência na tabela da direita
```

---

### JOIN com Múltiplas Tabelas

```sql
-- Tickets com usuário, responsável e servidor afetado
SELECT
    t.id,
    t.titulo,
    t.prioridade,
    u.nome           AS solicitante,
    resp.nome        AS responsavel,
    s.nome           AS servidor_afetado
FROM tickets t
INNER JOIN usuarios u    ON t.usuario_id     = u.id
LEFT  JOIN usuarios resp ON t.responsavel_id = resp.id
LEFT  JOIN servidores s  ON t.servidor_id    = s.id
WHERE t.status = 'aberto'
ORDER BY t.prioridade DESC, t.criado_em ASC;
```

---

### Visualizando os JOINs

```
Tabela A (usuarios)     Tabela B (tickets)
┌────────────────┐      ┌─────────────────┐
│ id │ nome      │      │ id │ usuario_id  │
│ 1  │ Ana       │      │ 10 │ 1 (Ana)     │
│ 2  │ Bruno     │      │ 11 │ 1 (Ana)     │
│ 3  │ Carlos    │      │ 12 │ 2 (Bruno)   │
│ 4  │ Diana     │      │ 13 │ 1 (Ana)     │
└────────────────┘      └─────────────────┘
  Diana não tem tickets

INNER JOIN → Ana(3 tickets), Bruno(1 ticket)         [Diana excluída]
LEFT JOIN  → Ana(3 tickets), Bruno(1 ticket), Diana  [Diana incluída, sem ticket]
```

---

### Self JOIN — Tabela Juntando com Ela Mesma

```sql
-- Funcionários e seus gerentes (ambos na mesma tabela)
SELECT
    f.nome    AS funcionario,
    g.nome    AS gerente,
    f.departamento
FROM funcionarios f
LEFT JOIN funcionarios g ON f.gerente_id = g.id
ORDER BY f.departamento, f.nome;
```

---

## Módulo 7 — Subqueries

Uma subquery é uma query dentro de outra query.

### Subquery no WHERE

```sql
-- Tickets de usuários do departamento de TI
SELECT t.titulo, t.status, t.criado_em
FROM tickets t
WHERE t.usuario_id IN (
    SELECT id
    FROM usuarios
    WHERE departamento = 'TI'
);

-- Servidores com CPU acima da média
SELECT nome, cpu_uso
FROM servidores
WHERE cpu_uso > (
    SELECT AVG(cpu_uso) FROM servidores
);

-- Tickets criados no mesmo dia que o incidente mais recente
SELECT *
FROM tickets
WHERE DATE(criado_em) = (
    SELECT DATE(MAX(iniciado_em)) FROM incidentes
);
```

---

### Subquery no FROM (Tabela Derivada)

```sql
-- Departamentos com mais tickets que a média
SELECT
    departamento,
    total_tickets
FROM (
    SELECT
        u.departamento,
        COUNT(t.id) AS total_tickets
    FROM usuarios u
    LEFT JOIN tickets t ON u.id = t.usuario_id
    GROUP BY u.departamento
) AS resumo_depto
WHERE total_tickets > (
    SELECT AVG(total_tickets)
    FROM (
        SELECT COUNT(t.id) AS total_tickets
        FROM usuarios u
        LEFT JOIN tickets t ON u.id = t.usuario_id
        GROUP BY u.departamento
    ) AS sub
)
ORDER BY total_tickets DESC;
```

---

### Subquery no SELECT (Scalar Subquery)

```sql
-- Para cada ticket, mostra quantos outros tickets o usuário tem
SELECT
    t.id,
    t.titulo,
    u.nome,
    (
        SELECT COUNT(*)
        FROM tickets t2
        WHERE t2.usuario_id = t.usuario_id
          AND t2.id != t.id
    ) AS outros_tickets_do_usuario
FROM tickets t
JOIN usuarios u ON t.usuario_id = u.id
WHERE t.status = 'aberto';
```

---

### EXISTS — Verificar Existência

```sql
-- Usuários que têm pelo menos um ticket crítico aberto
SELECT u.nome, u.email
FROM usuarios u
WHERE EXISTS (
    SELECT 1
    FROM tickets t
    WHERE t.usuario_id = u.id
      AND t.prioridade = 'critica'
      AND t.status = 'aberto'
);

-- NOT EXISTS — usuários sem nenhum ticket
SELECT u.nome
FROM usuarios u
WHERE NOT EXISTS (
    SELECT 1 FROM tickets t
    WHERE t.usuario_id = u.id
);
```

---

## Módulo 8 — Manipulando Dados (DML)

### INSERT — Inserindo Dados

```sql
-- Inserir uma linha
INSERT INTO tickets (titulo, descricao, status, prioridade, usuario_id)
VALUES ('Servidor fora do ar', 'Servidor web principal não responde', 'aberto', 'critica', 42);

-- Inserir múltiplas linhas de uma vez
INSERT INTO servidores (nome, ip, ambiente, cpu_uso, memoria_livre)
VALUES
    ('web-01', '10.0.1.10', 'producao', 45.2, 8192),
    ('web-02', '10.0.1.11', 'producao', 62.1, 4096),
    ('db-01',  '10.0.2.10', 'producao', 78.5, 2048);

-- Inserir a partir de outra query
INSERT INTO tickets_arquivo
SELECT * FROM tickets
WHERE status = 'fechado'
  AND resolvido_em < CURRENT_DATE - INTERVAL '1 year';
```

---

### UPDATE — Atualizando Dados

```sql
-- Atualizar um registro específico
UPDATE tickets
SET status = 'fechado',
    resolvido_em = NOW(),
    responsavel_id = 15
WHERE id = 1042;

-- Atualizar múltiplos registros
UPDATE servidores
SET status = 'manutencao'
WHERE ambiente = 'staging'
  AND ultimo_deploy < CURRENT_DATE - INTERVAL '30 days';

-- Update com base em outra tabela (JOIN no UPDATE)
UPDATE tickets t
SET responsavel_id = u.id
FROM usuarios u
WHERE u.departamento = 'Suporte'
  AND u.disponivel = TRUE
  AND t.responsavel_id IS NULL
  AND t.status = 'aberto';

-- ⚠️ SEMPRE use WHERE no UPDATE — sem WHERE, atualiza TUDO!
```

---

### DELETE — Removendo Dados

```sql
-- Deletar registro específico
DELETE FROM logs_acesso
WHERE id = 9999;

-- Deletar com condição
DELETE FROM logs_acesso
WHERE timestamp < CURRENT_DATE - INTERVAL '90 days';

-- Deletar com subquery
DELETE FROM tickets
WHERE usuario_id IN (
    SELECT id FROM usuarios WHERE ativo = FALSE
);

-- ⚠️ SEMPRE use WHERE no DELETE — sem WHERE, apaga TUDO!

-- ✅ Boa prática: rode o SELECT antes de fazer o DELETE
-- Primeiro, confirme o que vai apagar:
SELECT * FROM logs_acesso WHERE timestamp < CURRENT_DATE - INTERVAL '90 days';
-- Só então, apague:
DELETE FROM logs_acesso WHERE timestamp < CURRENT_DATE - INTERVAL '90 days';
```

---

### TRUNCATE — Limpar Tabela Inteira

```sql
-- Apaga TODOS os dados da tabela (muito mais rápido que DELETE sem WHERE)
TRUNCATE TABLE logs_temp;

-- ⚠️ Não pode ser revertido facilmente. Use com extremo cuidado!
-- ⚠️ Reseta os auto-incrementos (em alguns bancos)
```

---

### Transações — Segurança em Operações Críticas

```sql
-- Transação garante que ou tudo acontece, ou nada acontece

BEGIN;

    -- Transferir responsabilidade dos tickets
    UPDATE tickets
    SET responsavel_id = 20
    WHERE responsavel_id = 15
      AND status = 'aberto';

    -- Marcar funcionário como inativo
    UPDATE usuarios
    SET ativo = FALSE
    WHERE id = 15;

COMMIT;    -- Confirma tudo
-- ROLLBACK;  -- Ou desfaz tudo se algo der errado
```

---

## Módulo 9 — Criando Estruturas (DDL)

### CREATE TABLE

```sql
-- Criando a tabela de tickets
CREATE TABLE tickets (
    id              SERIAL PRIMARY KEY,          -- auto-incremento
    titulo          VARCHAR(200)   NOT NULL,
    descricao       TEXT,
    status          VARCHAR(20)    NOT NULL DEFAULT 'aberto',
    prioridade      VARCHAR(20)    NOT NULL DEFAULT 'media',
    usuario_id      INTEGER        NOT NULL REFERENCES usuarios(id),
    responsavel_id  INTEGER        REFERENCES usuarios(id),
    servidor_id     INTEGER        REFERENCES servidores(id),
    criado_em       TIMESTAMP      NOT NULL DEFAULT NOW(),
    atualizado_em   TIMESTAMP,
    resolvido_em    TIMESTAMP,

    -- Restrições
    CONSTRAINT chk_status     CHECK (status IN ('aberto', 'em_andamento', 'pausado', 'fechado')),
    CONSTRAINT chk_prioridade CHECK (prioridade IN ('baixa', 'media', 'alta', 'critica'))
);
```

---

### ALTER TABLE — Modificando Estrutura

```sql
-- Adicionar coluna
ALTER TABLE tickets ADD COLUMN categoria VARCHAR(50);

-- Remover coluna
ALTER TABLE tickets DROP COLUMN categoria;

-- Renomear coluna
ALTER TABLE tickets RENAME COLUMN descricao TO descricao_problema;

-- Mudar tipo de dado
ALTER TABLE tickets ALTER COLUMN titulo TYPE VARCHAR(300);

-- Adicionar constraint
ALTER TABLE tickets
ADD CONSTRAINT chk_resolucao
CHECK (resolvido_em IS NULL OR resolvido_em >= criado_em);
```

---

### DROP — Removendo Estruturas

```sql
-- Remover tabela
DROP TABLE logs_temp;

-- Remover apenas se existir (seguro)
DROP TABLE IF EXISTS logs_temp;

-- Remover banco inteiro (EXTREMO CUIDADO!)
DROP DATABASE nome_banco;
```

---

### Índices — Melhorando Performance

```sql
-- Índice simples (melhora buscas por essa coluna)
CREATE INDEX idx_tickets_status ON tickets(status);
CREATE INDEX idx_tickets_usuario ON tickets(usuario_id);

-- Índice composto (para queries que filtram por ambas)
CREATE INDEX idx_tickets_status_prioridade
ON tickets(status, prioridade);

-- Índice único (garante que os valores são únicos)
CREATE UNIQUE INDEX idx_usuarios_email
ON usuarios(email);

-- Remover índice
DROP INDEX idx_tickets_status;
```

---

## Módulo 10 — Funções Essenciais

### Funções de Texto

```sql
-- Tamanho
SELECT LENGTH('PostgreSQL');               -- 10

-- Maiúsculas / Minúsculas
SELECT UPPER('ana silva');                 -- ANA SILVA
SELECT LOWER('ANA SILVA');                 -- ana silva

-- Remover espaços
SELECT TRIM('  texto  ');                  -- 'texto'
SELECT LTRIM('  texto  ');                 -- 'texto  '
SELECT RTRIM('  texto  ');                 -- '  texto'

-- Substituir
SELECT REPLACE('a,b,c', ',', ' - ');       -- 'a - b - c'

-- Extrair parte do texto
SELECT SUBSTRING('PostgreSQL' FROM 1 FOR 4);    -- 'Post'
SELECT LEFT('PostgreSQL', 4);                   -- 'Post'
SELECT RIGHT('PostgreSQL', 3);                  -- 'SQL'

-- Posição de um texto dentro de outro
SELECT POSITION('SQL' IN 'PostgreSQL');    -- 8

-- Concatenar
SELECT CONCAT('Olá', ', ', 'mundo', '!'); -- 'Olá, mundo!'
SELECT 'Olá' || ', ' || 'mundo!';         -- PostgreSQL

-- Aplicação real: normalizar emails antes de busca
SELECT * FROM usuarios
WHERE LOWER(TRIM(email)) = LOWER(TRIM('Ana@EMPRESA.com'));
```

---

### Funções de Data

```sql
-- Data e hora atual
SELECT NOW();                              -- 2024-11-15 14:30:00.123
SELECT CURRENT_DATE;                       -- 2024-11-15
SELECT CURRENT_TIME;                       -- 14:30:00.123

-- Extrair parte da data
SELECT EXTRACT(YEAR  FROM NOW());          -- 2024
SELECT EXTRACT(MONTH FROM NOW());          -- 11
SELECT EXTRACT(DAY   FROM NOW());          -- 15
SELECT EXTRACT(HOUR  FROM NOW());          -- 14
SELECT EXTRACT(DOW   FROM NOW());          -- 5 (0=Dom, 1=Seg... 6=Sab)

-- Diferença entre datas
SELECT AGE(NOW(), '2024-01-01');           -- 10 months 14 days...
SELECT NOW() - '2024-01-01'::DATE;         -- 319 days (PostgreSQL)

-- Adicionar/subtrair intervalo
SELECT NOW() + INTERVAL '7 days';
SELECT NOW() - INTERVAL '3 months';
SELECT CURRENT_DATE - 30;                  -- 30 dias atrás

-- Formatar data
SELECT TO_CHAR(NOW(), 'DD/MM/YYYY HH24:MI');  -- '15/11/2024 14:30' (PostgreSQL)
SELECT DATE_FORMAT(NOW(), '%d/%m/%Y %H:%i');  -- MySQL

-- Truncar para início do período
SELECT DATE_TRUNC('month', NOW());         -- 2024-11-01 00:00:00
SELECT DATE_TRUNC('week', NOW());          -- início da semana atual
SELECT DATE_TRUNC('day', NOW());           -- hoje à meia-noite
```

---

### Funções Numéricas

```sql
SELECT ROUND(3.14159, 2);    -- 3.14
SELECT CEIL(4.1);            -- 5   (arredonda para cima)
SELECT FLOOR(4.9);           -- 4   (arredonda para baixo)
SELECT ABS(-15);             -- 15  (valor absoluto)
SELECT MOD(10, 3);           -- 1   (resto da divisão)
SELECT POWER(2, 8);          -- 256 (potência)
SELECT SQRT(144);            -- 12  (raiz quadrada)
```

---

### COALESCE e NULLIF — Tratando NULLs

```sql
-- COALESCE: retorna o primeiro valor não-nulo
SELECT
    nome,
    COALESCE(telefone, celular, 'Sem contato') AS contato
FROM usuarios;

-- Substituir null por 0 em somas
SELECT
    usuario_id,
    COALESCE(SUM(valor), 0) AS total_gasto
FROM compras
GROUP BY usuario_id;

-- NULLIF: retorna NULL se os dois valores forem iguais
-- Útil para evitar divisão por zero!
SELECT
    total_resolvidos,
    total_abertos,
    total_resolvidos / NULLIF(total_abertos, 0) AS taxa
FROM metricas;

-- Sem NULLIF: divisão por zero → erro
-- Com NULLIF: divisão por zero → NULL (sem erro)
```

---

### CASE WHEN — Lógica Condicional

```sql
-- CASE simples
SELECT
    nome,
    CASE prioridade
        WHEN 'critica' THEN '🔴 Crítica'
        WHEN 'alta'    THEN '🟠 Alta'
        WHEN 'media'   THEN '🟡 Média'
        WHEN 'baixa'   THEN '🟢 Baixa'
        ELSE '⚪ Indefinida'
    END AS prioridade_formatada
FROM tickets;

-- CASE pesquisado (condições complexas)
SELECT
    nome,
    cpu_uso,
    CASE
        WHEN cpu_uso >= 90 THEN 'CRÍTICO — ação imediata!'
        WHEN cpu_uso >= 75 THEN 'Alerta — monitorar'
        WHEN cpu_uso >= 50 THEN 'Normal — atenção'
        ELSE 'Saudável'
    END AS status_cpu
FROM servidores
ORDER BY cpu_uso DESC;

-- CASE em agregação (pivô manual)
SELECT
    DATE_TRUNC('month', criado_em) AS mes,
    COUNT(CASE WHEN prioridade = 'critica' THEN 1 END) AS criticos,
    COUNT(CASE WHEN prioridade = 'alta'    THEN 1 END) AS altos,
    COUNT(CASE WHEN prioridade = 'media'   THEN 1 END) AS medios,
    COUNT(CASE WHEN prioridade = 'baixa'   THEN 1 END) AS baixos,
    COUNT(*) AS total
FROM tickets
GROUP BY DATE_TRUNC('month', criado_em)
ORDER BY mes;
```

---

## Módulo 11 — Window Functions

Window Functions realizam cálculos sobre um conjunto de linhas relacionadas à linha atual, **sem agrupar as linhas** como o GROUP BY faz.

```sql
-- Sintaxe:
FUNÇÃO() OVER (
    PARTITION BY coluna   -- divide em grupos (opcional)
    ORDER BY coluna       -- ordena dentro do grupo (opcional)
)
```

---

### ROW_NUMBER, RANK, DENSE_RANK

```sql
-- Numerar tickets por usuário (do mais recente ao mais antigo)
SELECT
    id,
    titulo,
    usuario_id,
    criado_em,
    ROW_NUMBER() OVER (
        PARTITION BY usuario_id
        ORDER BY criado_em DESC
    ) AS numero_ticket_usuario
FROM tickets;

-- Ranking de usuários por quantidade de tickets
SELECT
    u.nome,
    COUNT(t.id) AS total,
    RANK()       OVER (ORDER BY COUNT(t.id) DESC) AS ranking,
    DENSE_RANK() OVER (ORDER BY COUNT(t.id) DESC) AS ranking_denso
FROM usuarios u
LEFT JOIN tickets t ON u.id = t.usuario_id
GROUP BY u.id, u.nome;

-- RANK vs DENSE_RANK:
-- RANK:       1, 2, 2, 4, 5  (pula o 3 depois de empate)
-- DENSE_RANK: 1, 2, 2, 3, 4  (não pula números)
```

---

### LAG e LEAD — Comparando com Linhas Vizinhas

```sql
-- Comparar CPU atual com a medição anterior (série temporal)
SELECT
    servidor_id,
    medido_em,
    cpu_uso,
    LAG(cpu_uso) OVER (
        PARTITION BY servidor_id
        ORDER BY medido_em
    ) AS cpu_anterior,
    cpu_uso - LAG(cpu_uso) OVER (
        PARTITION BY servidor_id
        ORDER BY medido_em
    ) AS variacao_cpu
FROM metricas_servidor
ORDER BY servidor_id, medido_em;

-- Ticket anterior e próximo do mesmo usuário
SELECT
    id,
    titulo,
    criado_em,
    LAG(criado_em)  OVER (PARTITION BY usuario_id ORDER BY criado_em) AS ticket_anterior_em,
    LEAD(criado_em) OVER (PARTITION BY usuario_id ORDER BY criado_em) AS proximo_ticket_em
FROM tickets;
```

---

### Somas e Médias Acumuladas

```sql
-- Total acumulado de tickets abertos por mês
SELECT
    mes,
    novos_tickets,
    SUM(novos_tickets) OVER (
        ORDER BY mes
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS total_acumulado
FROM (
    SELECT
        DATE_TRUNC('month', criado_em) AS mes,
        COUNT(*) AS novos_tickets
    FROM tickets
    GROUP BY DATE_TRUNC('month', criado_em)
) sub
ORDER BY mes;
```

---

## Módulo 12 — CTEs e Queries Complexas

### CTE — Common Table Expression

CTEs (WITH) deixam queries complexas muito mais legíveis, como se fossem "variáveis de query".

```sql
-- Sintaxe básica
WITH nome_cte AS (
    SELECT ...
)
SELECT * FROM nome_cte;
```

---

### CTEs na Prática

```sql
-- Análise completa de SLA de tickets

WITH
-- 1. Calcular tempo de resolução de cada ticket
tempo_resolucao AS (
    SELECT
        id,
        usuario_id,
        prioridade,
        criado_em,
        resolvido_em,
        EXTRACT(EPOCH FROM (resolvido_em - criado_em)) / 3600 AS horas_resolucao
    FROM tickets
    WHERE status = 'fechado'
      AND resolvido_em IS NOT NULL
),

-- 2. SLA máximo por prioridade (regra de negócio)
sla_regras AS (
    SELECT * FROM (
        VALUES
            ('critica', 4),
            ('alta',    8),
            ('media',   24),
            ('baixa',   72)
    ) AS t(prioridade, sla_horas)
),

-- 3. Verificar se cada ticket respeitou o SLA
analise_sla AS (
    SELECT
        tr.*,
        sr.sla_horas,
        CASE
            WHEN tr.horas_resolucao <= sr.sla_horas THEN 'Dentro do SLA'
            ELSE 'Fora do SLA'
        END AS resultado_sla
    FROM tempo_resolucao tr
    JOIN sla_regras sr ON tr.prioridade = sr.prioridade
)

-- Query final: resumo de SLA por prioridade
SELECT
    prioridade,
    COUNT(*) AS total,
    COUNT(CASE WHEN resultado_sla = 'Dentro do SLA' THEN 1 END) AS dentro_sla,
    COUNT(CASE WHEN resultado_sla = 'Fora do SLA'   THEN 1 END) AS fora_sla,
    ROUND(
        100.0 * COUNT(CASE WHEN resultado_sla = 'Dentro do SLA' THEN 1 END)
        / COUNT(*), 1
    ) AS percentual_sla
FROM analise_sla
GROUP BY prioridade
ORDER BY
    CASE prioridade
        WHEN 'critica' THEN 1
        WHEN 'alta'    THEN 2
        WHEN 'media'   THEN 3
        WHEN 'baixa'   THEN 4
    END;
```

---

### CTE Recursiva — Hierarquias

```sql
-- Organograma: mostrar todos os subordinados de um gerente
WITH RECURSIVE hierarquia AS (
    -- Caso base: o gerente raiz
    SELECT id, nome, gerente_id, 0 AS nivel
    FROM funcionarios
    WHERE id = 1  -- ID do diretor de TI

    UNION ALL

    -- Caso recursivo: buscar subordinados
    SELECT f.id, f.nome, f.gerente_id, h.nivel + 1
    FROM funcionarios f
    JOIN hierarquia h ON f.gerente_id = h.id
)
SELECT
    REPEAT('  ', nivel) || nome AS nome_indentado,
    nivel
FROM hierarquia
ORDER BY nivel, nome;

-- Resultado:
-- Diretor TI
--   Gerente Infra
--     Analista Infra 1
--     Analista Infra 2
--   Gerente Dev
--     Dev Sênior
--     Dev Pleno
```

---

## Módulo 13 — Performance e Índices

### EXPLAIN — Entendendo como o banco executa sua query

```sql
-- Ver o plano de execução
EXPLAIN
SELECT * FROM tickets
WHERE status = 'aberto'
  AND prioridade = 'critica';

-- Ver o plano COM tempo real de execução (PostgreSQL)
EXPLAIN ANALYZE
SELECT t.*, u.nome
FROM tickets t
JOIN usuarios u ON t.usuario_id = u.id
WHERE t.status = 'aberto';
```

**O que prestar atenção no EXPLAIN:**

| Sinal | O que significa | O que fazer |
|---|---|---|
| `Seq Scan` | Lendo a tabela inteira | Criar índice na coluna do WHERE |
| `Index Scan` | Usando índice ✅ | Ótimo! |
| `Hash Join` | Join eficiente ✅ | Normal para grandes tabelas |
| `Nested Loop` | Join com loop | Ok para pequenas tabelas |
| `rows=99999` | Estimativa de muitas linhas | Verificar se precisa índice |

---

### Estratégias de Performance

```sql
-- ✅ 1. Selecione só o que precisa
-- ❌ SELECT * FROM tickets WHERE ...
-- ✅ SELECT id, titulo, status FROM tickets WHERE ...

-- ✅ 2. Filtre cedo, filtre bem
SELECT t.id, t.titulo, u.nome
FROM tickets t
JOIN usuarios u ON t.usuario_id = u.id
WHERE t.status = 'aberto'         -- filtra antes do JOIN quando possível
  AND t.criado_em > '2024-01-01';

-- ✅ 3. Índices nas colunas usadas em WHERE e JOIN
CREATE INDEX idx_tickets_status    ON tickets(status);
CREATE INDEX idx_tickets_usuario   ON tickets(usuario_id);
CREATE INDEX idx_tickets_criado_em ON tickets(criado_em);

-- Índice composto (útil para filtros combinados frequentes)
CREATE INDEX idx_tickets_status_prioridade
ON tickets(status, prioridade)
WHERE status != 'fechado';    -- índice parcial: só indexa abertos

-- ✅ 4. Evite funções em colunas indexadas no WHERE
-- ❌ Índice não é usado:
WHERE YEAR(criado_em) = 2024
-- ✅ Índice é usado:
WHERE criado_em BETWEEN '2024-01-01' AND '2024-12-31'

-- ✅ 5. Use EXISTS em vez de IN para subqueries grandes
-- IN: executa a subquery completa primeiro
-- EXISTS: para assim que encontra o primeiro resultado
```

---

## Módulo 14 — Casos Reais de TI

### 📊 Dashboard de Tickets — Visão Geral

```sql
-- Relatório executivo: status atual do suporte
SELECT
    COUNT(*)                                      AS total_tickets,
    COUNT(CASE WHEN status = 'aberto'       THEN 1 END) AS abertos,
    COUNT(CASE WHEN status = 'em_andamento' THEN 1 END) AS em_andamento,
    COUNT(CASE WHEN status = 'fechado'
               AND DATE(resolvido_em) = CURRENT_DATE THEN 1 END) AS resolvidos_hoje,

    COUNT(CASE WHEN prioridade = 'critica'
               AND status IN ('aberto','em_andamento') THEN 1 END) AS criticos_pendentes,

    ROUND(AVG(
        CASE WHEN status = 'fechado'
        THEN EXTRACT(EPOCH FROM (resolvido_em - criado_em)) / 3600
        END
    ), 1) AS media_horas_resolucao

FROM tickets
WHERE criado_em >= CURRENT_DATE - INTERVAL '30 days';
```

---

### 🚨 Alertas de Infraestrutura

```sql
-- Servidores em estado crítico neste momento
SELECT
    s.nome                           AS servidor,
    s.ip,
    s.ambiente,
    s.cpu_uso                        AS "CPU %",
    s.memoria_livre                  AS "RAM livre (MB)",
    s.disco_livre                    AS "Disco livre (GB)",
    s.ultima_verificacao,
    CASE
        WHEN s.cpu_uso >= 95            THEN '🔴 CPU CRÍTICA'
        WHEN s.memoria_livre < 512      THEN '🔴 RAM CRÍTICA'
        WHEN s.disco_livre < 10         THEN '🔴 DISCO CRÍTICO'
        WHEN s.cpu_uso >= 80            THEN '🟠 CPU alta'
        WHEN s.memoria_livre < 1024     THEN '🟠 RAM baixa'
        WHEN s.disco_livre < 20         THEN '🟠 Disco baixo'
        ELSE '🟢 Normal'
    END AS status_alerta
FROM servidores s
WHERE s.ativo = TRUE
  AND s.ambiente = 'producao'
ORDER BY
    CASE
        WHEN s.cpu_uso >= 95 OR s.memoria_livre < 512 OR s.disco_livre < 10 THEN 1
        WHEN s.cpu_uso >= 80 OR s.memoria_livre < 1024 OR s.disco_livre < 20 THEN 2
        ELSE 3
    END,
    s.cpu_uso DESC;
```

---

### 🔍 Auditoria de Acessos Suspeitos

```sql
-- Detectar logins fora do horário comercial
SELECT
    usuario_id,
    u.nome,
    u.departamento,
    COUNT(*)                AS total_acessos_suspeitos,
    MIN(la.timestamp)       AS primeiro_acesso,
    MAX(la.timestamp)       AS ultimo_acesso,
    STRING_AGG(DISTINCT la.ip_origem, ', ') AS ips_usados
FROM logs_acesso la
JOIN usuarios u ON la.usuario_id = u.id
WHERE
    -- Fora do horário comercial (antes das 7h ou depois das 20h)
    (EXTRACT(HOUR FROM la.timestamp) < 7
     OR EXTRACT(HOUR FROM la.timestamp) >= 20)
    -- Ou final de semana
    OR EXTRACT(DOW FROM la.timestamp) IN (0, 6)
GROUP BY la.usuario_id, u.nome, u.departamento
HAVING COUNT(*) >= 3
ORDER BY total_acessos_suspeitos DESC;

-- Múltiplas tentativas de login falhas
SELECT
    ip_origem,
    COUNT(*)            AS tentativas_falhas,
    COUNT(DISTINCT usuario_tentado) AS usuarios_diferentes,
    MIN(timestamp)      AS primeiro_tentativa,
    MAX(timestamp)      AS ultima_tentativa
FROM logs_acesso
WHERE sucesso = FALSE
  AND timestamp >= NOW() - INTERVAL '1 hour'
GROUP BY ip_origem
HAVING COUNT(*) >= 5
ORDER BY tentativas_falhas DESC;
```

---

### 📈 Análise de SLA e Performance da Equipe

```sql
-- Performance individual de resolução de tickets por analista
WITH metricas_analista AS (
    SELECT
        resp.nome                       AS analista,
        COUNT(t.id)                     AS tickets_resolvidos,
        ROUND(AVG(
            EXTRACT(EPOCH FROM (t.resolvido_em - t.criado_em)) / 3600
        ), 1)                           AS media_horas,
        COUNT(CASE WHEN t.prioridade = 'critica' THEN 1 END) AS criticos_resolvidos,
        COUNT(CASE WHEN
            EXTRACT(EPOCH FROM (t.resolvido_em - t.criado_em)) / 3600
            <= CASE t.prioridade
                WHEN 'critica' THEN 4
                WHEN 'alta'    THEN 8
                WHEN 'media'   THEN 24
                ELSE 72
               END
        THEN 1 END) AS dentro_sla
    FROM tickets t
    JOIN usuarios resp ON t.responsavel_id = resp.id
    WHERE t.status = 'fechado'
      AND t.resolvido_em IS NOT NULL
      AND t.resolvido_em >= CURRENT_DATE - INTERVAL '30 days'
    GROUP BY resp.id, resp.nome
)
SELECT
    analista,
    tickets_resolvidos,
    media_horas         AS "Média (horas)",
    criticos_resolvidos AS "Críticos",
    dentro_sla,
    ROUND(100.0 * dentro_sla / NULLIF(tickets_resolvidos, 0), 1) AS "% SLA",
    RANK() OVER (ORDER BY tickets_resolvidos DESC) AS ranking_volume,
    RANK() OVER (ORDER BY media_horas ASC)         AS ranking_velocidade
FROM metricas_analista
ORDER BY tickets_resolvidos DESC;
```

---

### 🛠️ Relatório de Deploys e Incidentes

```sql
-- Correlação entre deploys e incidentes (detectar deploys problemáticos)
SELECT
    d.versao,
    d.projeto,
    d.realizado_em,
    d.responsavel,
    COUNT(i.id)          AS incidentes_apos_deploy,
    MIN(i.iniciado_em)   AS primeiro_incidente,
    SUM(i.duracao_minutos) AS total_minutos_impacto
FROM deploys d
LEFT JOIN incidentes i
    ON i.iniciado_em BETWEEN d.realizado_em
                         AND d.realizado_em + INTERVAL '24 hours'
    AND i.relacionado_ao_deploy = d.id
WHERE d.realizado_em >= CURRENT_DATE - INTERVAL '90 days'
GROUP BY d.id, d.versao, d.projeto, d.realizado_em, d.responsavel
ORDER BY incidentes_apos_deploy DESC, d.realizado_em DESC;
```

---

### 👥 Relatório de Acessos por Sistema

```sql
-- Quem acessou o sistema e com que frequência no último mês
SELECT
    u.nome,
    u.departamento,
    u.cargo,
    COUNT(la.id)                 AS total_acessos,
    COUNT(DISTINCT DATE(la.timestamp)) AS dias_com_acesso,
    MIN(la.timestamp)            AS primeiro_acesso,
    MAX(la.timestamp)            AS ultimo_acesso,
    ROUND(COUNT(la.id)::numeric /
        NULLIF(COUNT(DISTINCT DATE(la.timestamp)), 0), 1) AS media_acessos_por_dia
FROM usuarios u
LEFT JOIN logs_acesso la
    ON u.id = la.usuario_id
    AND la.timestamp >= CURRENT_DATE - INTERVAL '30 days'
    AND la.sucesso = TRUE
WHERE u.ativo = TRUE
GROUP BY u.id, u.nome, u.departamento, u.cargo
ORDER BY total_acessos DESC;
```

---

### 🧹 Queries de Manutenção / DBA

```sql
-- Tamanho das tabelas (PostgreSQL)
SELECT
    schemaname,
    tablename,
    pg_size_pretty(pg_total_relation_size(schemaname||'.'||tablename)) AS tamanho_total,
    pg_size_pretty(pg_relation_size(schemaname||'.'||tablename))       AS tamanho_dados,
    pg_size_pretty(pg_indexes_size(schemaname||'.'||tablename))        AS tamanho_indices
FROM pg_tables
WHERE schemaname = 'public'
ORDER BY pg_total_relation_size(schemaname||'.'||tablename) DESC;

-- Queries mais lentas (PostgreSQL com pg_stat_statements)
SELECT
    LEFT(query, 80)                      AS query_resumida,
    calls                                AS execucoes,
    ROUND(total_exec_time::numeric, 2)   AS tempo_total_ms,
    ROUND(mean_exec_time::numeric, 2)    AS tempo_medio_ms,
    ROUND(stddev_exec_time::numeric, 2)  AS desvio_padrao_ms
FROM pg_stat_statements
ORDER BY mean_exec_time DESC
LIMIT 10;

-- Conexões ativas (PostgreSQL)
SELECT
    pid,
    usename    AS usuario,
    application_name AS aplicacao,
    client_addr AS ip_cliente,
    state,
    LEFT(query, 60) AS query_atual,
    query_start
FROM pg_stat_activity
WHERE state != 'idle'
ORDER BY query_start;

-- Duplicatas para limpeza
SELECT
    email,
    COUNT(*) AS total
FROM usuarios
GROUP BY email
HAVING COUNT(*) > 1
ORDER BY total DESC;
```

---

## 🚀 Cheatsheet SQL

```sql
-- ============================================
-- CONSULTA BÁSICA
-- ============================================
SELECT coluna1, coluna2
FROM tabela
WHERE condição
ORDER BY coluna ASC|DESC
LIMIT n OFFSET m;

-- ============================================
-- FILTROS
-- ============================================
WHERE coluna = 'valor'
WHERE coluna != 'valor'
WHERE coluna > 10
WHERE coluna BETWEEN 1 AND 100
WHERE coluna IN ('a', 'b', 'c')
WHERE coluna LIKE '%texto%'
WHERE coluna IS NULL
WHERE coluna IS NOT NULL
WHERE cond1 AND cond2
WHERE cond1 OR cond2
WHERE NOT condição

-- ============================================
-- AGREGAÇÃO
-- ============================================
COUNT(*)             -- total de linhas
COUNT(coluna)        -- não conta NULLs
COUNT(DISTINCT col)  -- valores únicos
SUM(coluna)
AVG(coluna)
MIN(coluna)
MAX(coluna)

-- ============================================
-- AGRUPAMENTO
-- ============================================
GROUP BY coluna
HAVING COUNT(*) > 10        -- filtra grupos

-- ============================================
-- JOINS
-- ============================================
INNER JOIN tabela2 ON t1.id = t2.fk
LEFT  JOIN tabela2 ON t1.id = t2.fk
RIGHT JOIN tabela2 ON t1.id = t2.fk
FULL  JOIN tabela2 ON t1.id = t2.fk

-- ============================================
-- CASE WHEN
-- ============================================
CASE coluna
    WHEN 'a' THEN 'resultado a'
    WHEN 'b' THEN 'resultado b'
    ELSE 'outros'
END

CASE
    WHEN coluna > 100 THEN 'alto'
    WHEN coluna > 50  THEN 'medio'
    ELSE 'baixo'
END

-- ============================================
-- FUNÇÕES ÚTEIS
-- ============================================
COALESCE(col, 0)           -- substitui NULL
NULLIF(col, 0)             -- retorna NULL se igual
ROUND(valor, casas)
UPPER(texto) / LOWER(texto)
TRIM(texto)
LENGTH(texto)
SUBSTRING(texto FROM 1 FOR 5)
REPLACE(texto, 'de', 'por')
NOW() / CURRENT_DATE
EXTRACT(YEAR FROM data)
DATE_TRUNC('month', data)
INTERVAL '7 days'

-- ============================================
-- WINDOW FUNCTIONS
-- ============================================
ROW_NUMBER() OVER (PARTITION BY col ORDER BY col)
RANK()        OVER (ORDER BY col DESC)
DENSE_RANK()  OVER (ORDER BY col DESC)
LAG(col, 1)   OVER (PARTITION BY col ORDER BY col)
LEAD(col, 1)  OVER (PARTITION BY col ORDER BY col)
SUM(col)      OVER (ORDER BY col ROWS UNBOUNDED PRECEDING)

-- ============================================
-- CTE
-- ============================================
WITH nome AS (
    SELECT ...
),
outro_nome AS (
    SELECT ... FROM nome
)
SELECT * FROM outro_nome;

-- ============================================
-- DML
-- ============================================
INSERT INTO tabela (col1, col2) VALUES (v1, v2);
UPDATE tabela SET col = valor WHERE condição;
DELETE FROM tabela WHERE condição;

-- ============================================
-- BOAS PRÁTICAS
-- ============================================
-- ✅ Use aliases descritivos: FROM tickets t
-- ✅ Selecione colunas específicas, não *
-- ✅ Sempre use WHERE em UPDATE e DELETE
-- ✅ Teste SELECT antes de DELETE/UPDATE
-- ✅ Use transações em operações críticas
-- ✅ Indice colunas usadas em WHERE e JOIN
-- ✅ Use EXPLAIN para analisar performance
```

---

### 🏁 Desafios para praticar

- [ ] Crie um banco de dados de helpdesk do zero e popule com dados fictícios
- [ ] Escreva uma query que calcule o SLA de cada ticket automaticamente
- [ ] Crie um relatório de produtividade com ranking de analistas
- [ ] Detecte usuários com comportamento de acesso anômalo usando JOINs e GROUP BY
- [ ] Use Window Functions para calcular média móvel de incidentes por semana
- [ ] Escreva uma CTE recursiva para mostrar a hierarquia de um time
- [ ] Analise a performance de uma query com EXPLAIN e crie os índices corretos

---

### 📚 Recursos Recomendados

| Recurso | Tipo | Link |
|---|---|---|
| **SQLite Online** | Praticar no navegador | [sqliteonline.com](https://sqliteonline.com) |
| **PostgreSQL Docs** | Documentação completa | [postgresql.org/docs](https://www.postgresql.org/docs/) |
| **SQL Zoo** | Exercícios interativos | [sqlzoo.net](https://sqlzoo.net) |
| **Mode SQL Tutorial** | Tutoriais com dados reais | [mode.com/sql-tutorial](https://mode.com/sql-tutorial) |
| **pgAdmin** | Interface gráfica PostgreSQL | [pgadmin.org](https://www.pgadmin.org) |
| **DBeaver** | Cliente universal de banco | [dbeaver.io](https://dbeaver.io) |

---

<div align="center">

**Feito com ❤️ e muitos `SELECT * FROM erros WHERE resolvido = false`**

*"SQL é a linguagem que transforma dados em decisões."*

⭐ Se este curso te ajudou, dê uma estrela no repositório!

</div>
