# Technical Overview — My_Philosophers

## Problem

The Dining Philosophers problem is a compact way to study concurrency. Several independent threads compete for shared resources while the program must avoid data races, inconsistent state and timing errors.

## Runtime model

Each philosopher runs in its own thread and cycles through eating, sleeping and thinking. Forks are shared resources protected by mutexes. A monitoring routine checks whether a philosopher exceeded `time_to_die` and, when the optional meal target is provided, whether the simulation can stop after every philosopher reached that target.

## Main concurrency concerns

- mutex ownership for forks;
- synchronized logging/output;
- protected access to shared stop/death state;
- accurate timestamps;
- avoiding circular waits where possible;
- joining and cleaning up threads/mutexes correctly;
- handling the single-philosopher edge case.

## Timing

Concurrency correctness is not only logical: the simulation is time-sensitive. The program needs consistent time measurement and should avoid long uncontrolled sleeps that make death detection inaccurate.

## Useful stress tests

- 1 philosopher;
- 2 philosophers with tight timing;
- many philosophers with generous timing;
- configurations that should cause a death;
- configurations where all philosophers should reach the meal target;
- repeated runs to expose race conditions;
- run under ThreadSanitizer or Helgrind when available.

## Portfolio value

The project demonstrates practical understanding of threads, mutexes, race conditions, shared-state design, timing and cleanup — concepts that transfer directly to servers and concurrent systems.
