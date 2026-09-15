Introdução 

1.
O alfabeto é o conjunto finito de símbolos utilizados para construir as cadeias (palavras).
Para o formato de código do alfabeto inclui:
  
Letras maiúsculas:
$\{A, B, C, \dots, Z\}$


Dígitos numéricos:
$\{0, 1, 2, 3, 4, 5, 6, 7, 8, 9\}$

Símbolo especial: o hífen "-"
  
 $\Sigma$ {A, B, ... Z} $\cup$ {0, 1,...9} $\cup$ {-}

2. 
- Prefixo fixo: Começa com exatas 3 letras maiúsculas 

- Separador: Seguido por um hífen (-).

- Bloco de ano: Seguido por exatamente 4 dígitos numéricos

- Separador: Seguido por outro hífen (-).

- Bloco sequencial: Termina com exatamente 3 dígitos numéricos 

- Tamanho fixo: A palavra precisa ter exatamente 12 caracteres no total

3.

Aceitas (exemplos):

- LFA-2026-001 

- ABC-2024-042

- XYZ-1999-000

Rejeitadas (exemplos):

- LFA26-1 (falta hífens e possui quantidade incorreta de dígitos)

- LFA-2026-1 (o último bloco deve ter 3 dígitos, não 1)

- lfa-2026-001 (letras minúsculas não são permitidas)

- LFA-2026-0001 (o último bloco tem 4 dígitos em vez de 3)

4. Sim


5.

-  $\Sigma$ {A, B, ... Z} $\cup$ {0, 1,...9} $\cup$ {-}
-  A palavra é dividida sequencialmente em 5 blocos:

Bloco 1: 3 letras maiúsculas (ex: LFA)

Bloco 2: 1 hífen (-)

Bloco 3: 4 dígitos para o ano (ex: 2026)

Bloco 4: 1 hífen (-)

Bloco 5: 3 dígitos para o sequencial (ex: 001)

6.
Ordem: Estritamente sequencial (Bloco 1 $\rightarrow$ 2 $\rightarrow$ 3 $\rightarrow$ 4 $\rightarrow$ 5).

Escolhas:

No Bloco 1: qualquer letra de A a Z.

Nos Blocos 3 e 5: qualquer dígito de 0 a 9.

Repetições (Tamanho fixo):

Bloco 1: exatamente 3 repetições de letras.

Bloco 3: exatamente 4 repetições de dígitos.

Bloco 5: exatamente 3 repetições de dígitos.

7.

Válidos: LFA-2026-001, ENG-2024-042, ABC-1999-000

Inválidos: LFA26-1 (sem hífens e tamanho incorreto), lfa-2026-001 (minúsculas), LFA-2026-01 (último bloco com 2 dígitos em vez de 3)

8.

Expressão Regular (Regex Posix): [A-Z]{3}-[0-9]{4}-[0-9]{3}

Linguagem Formal (Notação Teórica): $(A\vert{}B\vert{}\dots\vert{}Z)^3 \cdot - \cdot (0\vert{}1\vert{}\dots\vert{}9)^4 \cdot - \cdot (0\vert{}1\vert{}\dots\vert{}9)^3$


Sufixo 00

- 0|1)*00

Exatamente dois a

- b*ab*ab*

Identificador acadêmico

- ^[A-Z]{2}[0-9]{3}[a-z]?$

  

Código de matrícula acadêmica

^(CCO|ESW|SIS)-202[4-9]-[0-9]{4}-[MTN]$



DFA equivalente 

EstadoOrigem,               Entrada,          Estado Destino,       Descrição


q0​ (Inicial),               [A-Z],                 q1​,              Lê a 1ª letra do curso



q1​,                         [A-Z],                 q2​,              Lê a 2ª letra do curso


 
q2​,                         [0-9],                 q3​,              Lê o 1º dígito do código



q3​,                         [0-9],                 q4​,              Lê o 2º dígito do código



q4​,                         [0-9],                 q5​,              Lê o 3º dígito do código



q5​ (Aceitação),             [a-z],                 q6​,              Lê o sufixo opcional (turno)



q6​ (Aceitação),           Qualquer símbolo,       qerro​,            Caractere extra inviabiliza a palavra


Qualquer estado,          Entrada fora do padrão, qerro​,            Transição implícita para o sumidouro


qerro​ (Sumidouro),        Qualquer símbolo,       qerro​,            Permanece no sumidouro
