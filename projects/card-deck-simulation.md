---
layout: project
type: project
image: img/cards.jpg
title: "Card Deck Simulation"
date: 2024
published: true
labels:
  - C
  - Cards
  - Simulator
summary: "A card deck simulation program I wrote in C for ICS 212 during my Spring 2024 semester."
---

In ICS 212: Program Structure, a course I took in Spring 2024, we were tasked with designing a card deck simulator that mimics the functionality of a real deck of cards. The program starts by creating a full 52-card deck, assigning each card a `rank` (like Ace or King), a `suit` (like Hearts or Spades), and a `color` (red or black). The deck is stored using an array of structs and can be shuffled randomly using the `rand()` function seeded by the system clock.

## Structure and Initialization

Cards are stored using the following structure:

```c
struct card {
    char *rank;
    char suit[MAX];
    char color[MAX];
};
typedef struct card Card;
```

The deck is initialized using three predefined arrays: `ranks`, `suits`, and `colors`. Cards are created in a loop:

```c
deck[i].rank = ranks[i % MAX_RANKS];
strncpy(deck[i].suit, suits[i / MAX_RANKS], MAX);
strncpy(deck[i].color, colors[i / MAX_RANKS], MAX);
```

This approach uses modulo and division to assign appropriate ranks and suits to all 52 cards while also associating the right color with each suit.

## Shuffling the Deck

To simulate a real-world shuffle, the program uses a pseudo-random number generator seeded with `time(NULL)`:

```c
srand(time(NULL));
for (i = 0; i < MAX_CARDS; i++) {
    swapper = rand() % MAX_CARDS;
    temp = deck[i];
    deck[i] = deck[swapper];
    deck[swapper] = temp;
}
```

This Fisher-Yates-like algorithm ensures that the cards are randomly reordered. The user is then prompted whether they want to shuffle again.

## Displaying the Cards

Cards are printed in groups of three using the following format:

```c
printf("%5s of %-12s (%s)\n", deck[i].rank, deck[i].suit, deck[i].color);
```

This output includes the card’s rank, suit, and color, and every three cards are followed by a newline for better readability.

## Program Flow Summary

The main program structure:

```c
Card deck[MAX_CARDS];
initialize(deck);
display(deck);

while ('\n' == newline) {
    shuffle(deck);
    display(deck);
    newline = getchar();
}
```

This loop allows the user to shuffle the deck repeatedly, reinforcing understanding of loops, conditionals, input handling, and function calls.

## Reflection

This project strengthened my ability to use C structures, pointers, arrays, and standard libraries like `stdlib.h` and `time.h`. I learned how to organize related data into a meaningful structure, work with arrays of structures, and incorporate randomness for realistic simulations. With occasional guidance from Professor Wright’s course materials, I was able to design, test, and debug the code independently. The process boosted my confidence in C/C++ programming and helped me think more clearly about program state and logic.

<hr>

Source: <a href="https://github.com/acenasa/card_deck_simulation/blob/main/card_deck_simulation.c.c"><i class="large github icon "></i>acenasa/ics-212-card-deck-simulation</a>
