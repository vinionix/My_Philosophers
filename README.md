# My_Philosophers

Implementação do problema clássico dos filósofos jantando em C, desenvolvida como parte da formação da 42 Rio.

O projeto trabalha concorrência, threads, mutexes, sincronização e controle de tempo. A proposta é simular filósofos que alternam entre comer, dormir e pensar, evitando condições de corrida e monitorando corretamente o estado de cada participante.

## Objetivo

Resolver o problema dos filósofos jantando usando `pthread`, garantindo que os recursos compartilhados sejam protegidos e que a simulação respeite os tempos informados por argumento.

## Tecnologias e conceitos utilizados

- C
- Makefile
- `pthread`
- Mutexes
- Concorrência
- Sincronização entre threads
- Controle de tempo com `gettimeofday`
- Estruturas encadeadas
- Gerenciamento manual de memória

## Funcionamento geral

O programa recebe os parâmetros da simulação pela linha de comando:

```text
./philo number_of_philosophers time_to_die time_to_eat time_to_sleep [number_of_times_each_philosopher_must_eat]
```

Cada filósofo é executado em uma thread. Os garfos são protegidos por mutexes, e uma rotina de monitoramento acompanha se algum filósofo morreu ou se todos atingiram a quantidade mínima de refeições, quando esse argumento opcional é informado.

O código também trata o caso específico de apenas um filósofo.

## Como compilar e executar

```sh
git clone https://github.com/vinionix/My_Philosophers.git
cd My_Philosophers
make
./philo 5 800 200 200
```

Exemplo com limite de refeições:

```sh
./philo 5 800 200 200 7
```

Alvos disponíveis:

```sh
make
make clean
make fclean
make re
```

## Status atual

Projeto em C com estrutura principal implementada, incluindo criação de threads, rotina dos filósofos, monitoramento e tratamento para um único filósofo.

O repositório não informa testes automatizados ou resultado de avaliação. A documentação foi escrita com base nos arquivos disponíveis no projeto.

## Evolução do projeto

- Estruturação dos argumentos e da tabela de filósofos/garfos.
- Implementação da criação de threads para os filósofos.
- Proteção de recursos compartilhados com mutexes.
- Implementação do monitoramento da simulação.
- Tratamento do caso de apenas um filósofo.
- Fase atual: projeto documentado para consulta e portfólio.

## Aprendizados principais

- Criação e sincronização de threads em C.
- Uso de mutexes para proteger recursos compartilhados.
- Prevenção de condições de corrida.
- Controle de tempo em simulações concorrentes.
- Organização de uma solução para um problema clássico de sistemas operacionais.

## Autor

Desenvolvido por [vinionix](https://github.com/vinionix) durante a formação na 42 Rio.
