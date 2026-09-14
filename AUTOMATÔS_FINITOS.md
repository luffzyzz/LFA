Exercício 1

1. Quantos estados existem?
2, ligado e desligado

2.Qual é o estado inicial, considerando que a lâmpada começa apagada?
desligado (estado inicial)

3.Qual entrada provoca uma transição?
O evento de pressionar o botão

4.Partindo de desligado, qual será o estado após um acionamento?
ligado

5.Partindo de desligado, qual será o estado após dois acionamentos?
desligado

6.Explique o funcionamento do sistema com sua palavras:
O sistema funciona como um alternador de estados simples. Toda vez que o botão recebe a entrada de ser pressionado, ele muda a lâmpada do seu estado 
atual para o oposto, se estiver desligada ela liga e se estiver ligada ela desliga.

Exercício 2

Complete a tabela:

Estado atual,       Entrada,              Próximo estado
Fechado,            pessoa_detectada,     Aberto
Fechado,            nenhuma_pessoa,       Fechado
Aberto,             pessoa_detectada,     Aberto
Aberto,             nenhuma_pessoa,       Fechado

Diagrama de estados:

         ┌─── nenhuma_pessoa ───┐            ┌─── pessoa_detectada ───┐
         │                      │            │                        │
         ▼                      │            ▼                        │
    ──► (Fechado) ────── pessoa_detectada ──────► (Aberto) ───────────┘
             ▲                                       │
             └─────────── nenhuma_pessoa ────────────┘

Exercício 3

1. O alfabeto Σ;
Σ = {0,1}

2. O conjunto de estados Q;
Q = {q0, q1}

3. O estado inicial;
q0

4. O conjunto de estados finais F;

5. Os símbolos que podem ser lidos;
0 e 1

6. O significado do círculo duplo em um diagrama;
Indica um estado final 

7. O significado da seta sem origem apontando para um estado;
Indica qual é o estado inicial do autômato 

Exercício 4

Complete: 

Elemento,                  Significado
Σ,                         Alfabeto: Conjunto finito de símbolos de entrada aceitos pelo autômato.
Q,                         Conjunto de estados: Conjunto finito de todos os estados possíveis da máquina.
δ,                         Função de transição: Mapeamento (δ:Q×Σ→Q) que define o próximo estado a partir do estado atual e do símbolo lido.
q0​,                        Estado inicial: Estado em que o autômato se encontra antes de iniciar a leitura da entrada (q0​∈Q).
F,                         Conjunto de estados finais: Subconjunto de Q (F⊆Q) que indica quais estados resultam na aceitação da cadeia.

Explique por que esses cinco elementos são suficientes para definir o funcionamento de um AFD:

1. Entrada validada: Σ define exatamente quais símbolos são permitidos na leitura
2. Espaço de memória: Q define a quantidade finita de configurações/memória interna que o sistema possui 
3. Comportamento deterministico: δ garante que para cada par (estado atual, símbolo lido), exista exatamente um único estado de destino,
sem escolhas aleatórias ou indecisões 
4. Ponto de partida claro: q0 garante que o sistema sempre inicie do mesmo lugar pré-determinado
5. Critério de decisão: F define formalmente a condição de parada que diz se a cadeia lida pertence ou não à linguagem reconhecida pelo autômato

Exercício 5

1.Qual é o resultado de δ(q0, 0)?
δ (q0, 0) = q0 

2. Qual é o resultado de δ(q0, 1)?
δ(q0, 1) = q1

3. Qual é o resultado de δ(q1, 0)?
δ(q1, 0) = q2

4. Qual é o resultado de δ(q2, 1)?
δ(q2, 1) = q1

5. Qual é o estado de aceitação?
O estado de aceitação é q1

6. Desenhe o diagrama correspondente à tabela:

            ┌─── 0 ───┐
            │         │
            ▼         │
       ──► (q0) ──── 1 ────► ((q1)) ◄── 1 ──┐
                               │            │
                               │ 0          │
                               ▼            │
                              (q2) ─────────┘

8. - Para todo q ∈ Q e todo símbolo de entrada da δ ∈ Σ, existe exatamente uma única transição definida na tabela
- Não existem transições vazias
- Não há ambiguidade no caminho percorrido para qualquer símbolo lido

Exercício 6

Aceita ou Rejeita

a) 1

b) 0011001

c) 010010

d) 1101

e) 000011010


a) Cadeia: 
1


Caminho percorrido:
q0 --1--> q1

Estado final:
q1


Resultado:
ACEITA



b) Cadeia: 
0011001


Caminho percorrido:
q0 --0--> q0
q0 --0--> q0
q0 --1--> q1
q1 --1--> q1
q1 --0--> q2
q2 --0--> q1
q1 --1--> q1


Estado final:
q1


Resultado:
ACEITA



c) Cadeia: 
010010


Caminho percorrido:
q0 --0--> q0
q0 --1--> q1
q1 --0--> q2
q2 --0--> q1
q1 --1--> q1
q1 --0--> q2


Estado final:
q2


Resultado:
REJEITADA



d) Cadeia: 
1101


Caminho percorrido:
q0 --1--> q1
q1 --1--> q1
q1 --0--> q2
q2 --1--> q1


Estado final:
q1


Resultado:
ACEITA



e) Cadeia: 
000011010


Caminho percorrido:
q0 --0--> q0
q0 --0--> q0
q0 --0--> q0
q0 --0--> q0
q0 --1--> q1
q1 --1--> q1
q1 --0--> q2
q2 --1--> q1
q1 --0--> q2


Estado final:
q2


Resultado:
REJEITADA


Exercício 7

- Conjunto de estados (Q): {q0, q1}
- Alfabeto (Σ): {0, 1}
- Estado inicial: (q0): q0
- Conjunto de estados finais (F): {q1}


Tabela de transição δ:
δ,0,1
q0​,q0​,q1​
q1​,q0​,q1​

Diagrama de estados:

         ┌─── 0 ───┐            ┌─── 1 ───┐
         │         │            │         │
         ▼         │            ▼         │
    ──► (q0) ──── 1 ────► ((q1)) ─────────┘
         ▲                 │
         └─────── 0 ───────┘

Teste de Cadeias

Cadeia
1


Caminho percorrido 
q0 --1--> q1


Estado final 
q1


Resultado 
aceita


Cadeia
01


Caminho percorrido 
q0 --0--> q0 --1--> q1


Estado final 
q1


Resultado 
aceita


Cadeia
101  


Caminho percorrido 
q0 --1--> q1 --0--> q0 --1--> q1


Estado final 
q1


Resultado 
aceita 


Cadeia
10


Caminho percorrido 
q0 --1--> q1 --0--> q0


Estado final 
q0


Resultado 
rejeita


Cadeia
1110


Caminho percorrido 
q0 --1--> q1 --1--> q1 --1--> q1 --0--> q0

Estado final 
q0


Resultado 
rejeita



Exercício 8

Definição formal M = (Q, Σ, δ, q0, F)

Q: {q0, q1}
Σ: {0,1}
q0: q0
F: {q,0}

Tabela de transição (δ):

δ,0,1
q0​,q0​,q1​
q1​,q1​,q0​

Diagrama de estados:

         ┌─── 0 ───┐            ┌─── 0 ───┐
         │         │            │         │
         ▼         │            ▼         │
    ──► ((q0)) ─── 1 ────► (q1) ──────────┘
          ▲                 │
          └─────── 1 ───────┘

Cadeia:
ε
Caminho percorrido:
q0​
Estado final:
q0​
Resultado:
ACEITA

Cadeia:
0
Caminho percorrido:
q0 ​──► 0​ ──► q0​
Estado final:
q0​
Resultado:
ACEITA

Cadeia:
1
Caminho percorrido:
q0​ ──► 1 ──► ​q1​
Estado final:
q1​
Resultado:
REJEITADA


Cadeia:
11
Caminho percorrido:
q0​ ──► 1​ ──► q1 ──► ​1 ──► ​q0​
Estado final:
q0​
Resultado:
ACEITA


Cadeia:
10101
Caminho percorrido:
q0​ ──► 1 ──► ​q1 ──► ​0 ──► ​q1 ──► ​1 ──► ​q0 ──► ​0 ──► ​q0 ──► ​1 ──► ​q1​
Estado final:
q1​
Resultado
REJEITADA


Cadeia:
101
Caminho percorrido:
q0​ ──► 1 ──► ​q1 ──► ​0 ──► ​q1  ──► ​1  ──► ​q0​
Estado final:
q0​
Resultado:
ACEITA


Cadeia:
1100
Caminho percorrido:
q0​ ──► 1 ──► ​q1 ──► ​1 ──► ​q0 ──► ​0 ──►​ q0​ ──► 0 ──► ​q0​
Estado final:
q0​
Resultado:
ACEITA

Exercício 9 

1. O que o estado inicial representa? 
Nenhum 
2. O que ocorre quando aparece o primeiro 0? 
A máquina transita para um estado intermediário que memoriza que exatamente um 0 acabou de ser visto.
3. O que ocorre quando outro 0 aparece imediatamente depois? 
A máquina reconhece o padrão 00 e transita para o estado final de aceitação.
4. Depois de encontrar 00, a cadeia pode deixar de ser aceita? 
Não. Uma vez alcançada a sequência 00, a condição "pelo menos dois zeros consecutivos" é satisfeita permanentemente. 
O estado final atua como um estado de retenção.
5. Quantos estados são necessários? 
3 estados (q0, q1 e q2)

Definição formal M = (Q, Σ, δ, q0, F)

Q: {q0, q1, q2}
Σ: {0,1}
q0: q0
F: {q2}

Tabela de transição(δ):
δ,0,1
q0​,q1​,q0​
q1​,q2​,q0​
q2​,q2​,q2​

Diagrama de estados:

          ┌─── 1 ───┐                            ┌─── 0, 1 ───┐
          │         │                            │            │
          ▼         │                            ▼            │
    ──► (q0) ───── 0 ────► (q1) ────── 0 ────► ((q2)) ────────┘
         ▲                  │
         └──────── 1 ───────┘

Cadeia:
ε
Caminho percorrido:
q0​
Estado final:
q0​
Resultado:
REJEITADA

Cadeia:
0
Caminho percorrido:
q0​  ──► 0  ──► ​q1​
Estado final:
q1​
Resultado:
REJEITADA

Cadeia:
1
Caminho percorrido:
q0​  ──► 1 ──►  ​q0​
Estado final:
q0​
Resultado:
REJEITADA

Cadeia:
01
Caminho percorrido:
q0​ ──►  0 ──►  ​q1 ──►  ​1 ──►  ​q0​
Estado final:
q0​
Resultado:
REJEITADA

Cadeia:
10
Caminho percorrido:
q0​ ──►  1 ──►  ​q0 ──►  ​0 ──►  ​q1​
Estado final:
q1​
Resultado:
REJEITADA

Cadeia:
10101
Caminho percorrido:
q0​ ──►  1 ──►  ​q0 ──►  ​0​q ──►  1 ──►  ​1 ──►  ​q0 ──►  ​0​q ──►  1​ ──► 1 ──►  ​q0
Estado final:
q0​
Resultado:
REJEITADA

Cadeia:
00
Caminho percorrido:
q0 ──►  ​0​q ──►  1​ ──►  0​ ──►  q2​
Estado final:
q2​
Resultado:
ACEITA

Cadeia:
001
Caminho percorrido:
q0 ──►  ​0​q ──►  1 ──►  ​0​ ──►  q2​ ──►  1 ──►  ​q2
Estado final:
q2​
Resultado:
ACEITA

Cadeia:
100
Caminho percorrido:
q0​ ──►  1 ──►  ​q0 ──►  ​0​q ──►  1​ ──►  0​ ──►  q2​
Estado final:
q2​
Resultado:
ACEITA

Cadeia:
1001
Caminho percorrido:
q0​ ──►  1 ──►  ​q0 ──►  ​0​q ──►  1​ ──►  0​ ──►  q2​ ──►  1 ──►  ​q2
Estado final:
q2​
Resultado:
ACEITA

Cadeia:
0000
Caminho percorrido:
q0​  ──► 0​q ──►  1​ ──►  0​ ──►  q2 ──►  ​0​ ──► q2 ──►  ​0 ──►  ​q2
Estado final:
q2​
Resultado:
ACEITA

Cadeia:
110011
Caminho percorrido:
q0​ ──►  1 ──►  ​q0 ──►  ​1 ──►  ​q0 ──►  ​0 ──►  ​q1 ──►  ​0 ──►  ​q2 ──►  ​1 ──►  ​q2 ──►  ​1 ──►  ​q2​
Estado final:
q2​
Resultado:
ACEITA

Exercício 10

Definição formal M = (Q, Σ, δ, q0, F)

Q: {Verde, Amarelo, Vermelho}
Σ: {tempo}
q0: Verde
F:∅

Tabela de transição(δ):
δ,tempo
Verde,Amarelo
Amarelo,Vermelho
Vermelho,Verde

Diagrama de estados:

    ──► (Verde) ────── tempo ──────► (Amarelo)
           ▲                             │
           │                           tempo
         tempo                           │
           │                             ▼
           └──────────────────────── (Vermelho)

* O semáforo atua como um sistema de controle reativo e cíclico. 
A cada pulso do evento de entrada tempo (que representa a expiração do timer de cada fase):

Estando em Verde, a transição leva o sistema para o estado Amarelo.

Estando em Amarelo, a próxima transição muda o estado para Vermelho.

Estando em Vermelho, o ciclo se completa e a transição retorna ao estado Verde.

Exercício 11

Definição formal M = (Q, Σ, δ, q0, F)

1. Q: {q0, q1, q2, Autenticado, Bloqueado}
2. Σ: {senha_correta, senha_incorreta}
3. q0: q0
4. F: {Autenticado}
5. Comportamento Pós-Autenticação e Pós-Bloqueio: Ambos atuam como estados de retenção, 
permanecendo em si mesmos independentemente de novas entradas recebidas.
6. - Após a Autenticação (Autenticado)Comportamento: O usuário já teve seu acesso concedido. 
Qualquer entrada adicional de senha_correta ou senha_incorreta mantém o sistema no estado Autenticado.
- Comportamento: O limite de 3 tentativas foi atingido. 
O sistema trava e ignora tentativas futuras: qualquer nova tentativa (seja senha_correta ou senha_incorreta) mantém o sistema no estado Bloqueado, 
impedindo a autenticação até que ocorra uma intervenção externa (como um reset do sistema).

Tabela de transição(δ):

δ,senha_correta,senha_incorreta
q0​,Autenticado,q1​
q1​,Autenticado,q2​
q2​,Autenticado,Bloqueado
((Autenticado)),Autenticado,Autenticado
Bloqueado,Bloqueado,Bloqueado

Diagrama de estados:

                   ┌─────── senha_correta ───────┐
                   │                             │
                   ├─────── senha_correta ───────┼────────┐
                   │                             │        │
                   │       ┌─ senha_correta ─────┼────────┼──────┐
                   │       │                     │        │      │
                   ▼       ▼                     │        │      │
    ──► (q0) ── senha_incorreta ──► (q1) ── senha_incorreta ──► (q2)   │   
                                                          │     │
                                                   senha_incorreta │
                                                          │     │
                                                          ▼     ▼
                                                     (Bloqueado) ((Autenticado))
                                                      └─ ↻ ─┘      └─ ↻ ─┘
                                                      (ambas)      (ambas)
