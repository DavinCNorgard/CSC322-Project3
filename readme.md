# Dining Philosophers Problem with Rotating Priority (NuSMV)

This repository contains an implementation of the classic Dining Philosophers problem using NuSMV, a symbolic model checker. The solution demonstrates a rotating priority mechanism to ensure a more fair opportunity for each philosopher to pick up the chopsticks and eat.

## Problem Description

The Dining Philosophers problem is a classic synchronization problem that illustrates the challenges of avoiding deadlock and ensuring fairness in concurrent systems. There are five philosophers sitting around a circular table. Each philosopher spends their time either thinking or eating. In the center of the table, there is a bowl of spaghetti. Between each pair of philosophers, there is a single chopstick. In order to eat, a philosopher must have both chopsticks to their left and right. The goal is to ensure that every philosopher gets a chance to eat while avoiding deadlock and starvation.

## Model Description

The model is implemented in the `phil.smv` file. It consists of the following components:

- An array `chopsticks` that represents the five chopsticks and their current holder (either a philosopher or nobody).
- A `priority` variable that ranges from 0 to 4 and is used to determine which philosopher currently has the highest priority.
- Five instances of the `philosopher` MODULE, one for each philosopher.

The `philosopher` MODULE has the following variables:

- `state` that represents the philosopher's current state (thinking, hungry, eating, or done).
- Definitions for `gotleft`, `gotright`, `leftfree`, `rightfree`, and `higher_priority`.

The implementation includes a rotating priority mechanism by updating the `priority` variable in the main module and passing it to the philosopher MODULEs. The philosophers can then check if they have the highest priority based on the value of the passed `current_priority` variable.

## Usage

To run the model checking, execute the following command in your terminal:

NuSMV phil.smv >> info.txt
