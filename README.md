# My_Philosophers

Implementação do problema clássico dos **Filósofos Jantando** em C, desenvolvida durante a formação da 42 Rio.

O projeto usa threads e mutexes para simular filósofos que alternam entre comer, dormir e pensar enquanto disputam recursos compartilhados. O desafio real é manter o estado consistente sob concorrência e respeitar os limites de tempo da simulação.

## Objetivo

Resolver o problema usando `pthread`, garantindo que:

- os garfos sejam protegidos contra acesso concorrente incorreto;
- a saída da simulação permaneça consistente;
- o estado de morte/finalização seja observado corretamente;
- a simulação respeite `time_to_die`, `time_to_eat` e `time_to_sleep`;
- o argumento opcional de quantidade de refeições seja tratado;
- recursos sejam liberados ao final.

## Execução

```text
./philo number_of_philosophers time_to_die time_to_eat time_to_sleep [number_of_times_each_philosopher_must_eat]
```

Exemplo:

```bash
./philo 5 800 200 200
```

Com meta de refeições:

```bash
./philo 5 800 200 200 7
```

## Modelo de concorrência

```text
Philosopher thread 1 ─┐
Philosopher thread 2 ─┼──> shared forks protected by mutexes
Philosopher thread N ─┘
          │
          └────────────> monitor / stop condition
```

Cada filósofo executa uma rotina própria. Os garfos são recursos compartilhados, e uma rotina de monitoramento acompanha as condições de término.

## Tecnologias e conceitos

- C
- Makefile
- `pthread`
- mutexes
- concorrência
- sincronização
- `gettimeofday`
- shared state
- estruturas encadeadas
- gerenciamento manual de memória

## Onde estão os bugs mais perigosos

Projetos concorrentes podem parecer corretos durante dezenas de execuções e falhar apenas em uma condição de timing específica. Os pontos mais sensíveis são:

- duas threads acessando estado sem sincronização;
- ordem de aquisição de garfos;
- saída concorrente no terminal;
- thread de monitor lendo estado enquanto outra thread o modifica;
- diferença entre tempo real e o momento em que a thread volta a executar;
- cleanup de mutex/thread durante finalização.

## Casos de teste úteis

- um único filósofo;
- dois filósofos;
- muitos filósofos;
- tempos extremamente apertados;
- cenário em que uma morte é esperada;
- cenário em que todos devem completar a meta de refeições;
- várias execuções consecutivas com os mesmos argumentos;
- análise com ferramentas de detecção de data race quando disponíveis.

## Como compilar

```bash
git clone https://github.com/vinionix/My_Philosophers.git
cd My_Philosophers
make
```

Alvos:

```bash
make
make clean
make fclean
make re
```

## Status

A estrutura principal está implementada, incluindo criação de threads, rotina dos filósofos, monitoramento e tratamento do caso de um único filósofo. O repositório não afirma resultado oficial de avaliação nem suíte automatizada completa.

## O que este projeto demonstra

- criação e sincronização de threads;
- mutexes e proteção de recursos compartilhados;
- raciocínio sobre race conditions;
- controle de tempo em sistemas concorrentes;
- lifecycle e cleanup de recursos de sincronização;
- debugging de comportamento não determinístico.

## Documentação

- [Technical Overview](docs/TECHNICAL_OVERVIEW.md) — modelo de concorrência, pontos críticos e estratégia de stress test.

## Autor

Desenvolvido por [Vinícius Fidelis](https://github.com/vinionix) durante a formação na 42 Rio.
