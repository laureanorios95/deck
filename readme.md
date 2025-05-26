# Deck

A Go library for creating, shuffling, and managing card decks.

## Overview

Deck is a lightweight, flexible Go package that provides functionality to create and manipulate virtual card decks. Whether you're building a card game, implementing a deck of slides, or need a randomized collection of items, Deck offers simple yet powerful tools to handle these operations.

## Features

- Create standard 52-card decks or custom decks
- Shuffle decks using various algorithms
- Draw cards from the deck
- Organize and sort cards
- Manipulate deck state (add/remove cards)
- Pure Go implementation with no external dependencies

## Installation

```bash
go get github.com/laureanorios95/deck
```

## Usage

```go
package main

import (
    "fmt"
    "github.com/laureanorios95/deck"
)

func main() {
    // Create a standard deck of cards
    cards := deck.New()
    
    // Shuffle the deck
    cards = deck.Shuffle(cards)
    
    // Draw a card
    card := cards[0]
    cards = cards[1:]
    fmt.Println(card)
    
    // Draw multiple cards (a hand)
    hand := cards[:5]
    cards = cards[5:]
    fmt.Println(hand)
}
```

## API Reference

### Creating a Deck

```go
// Standard 52-card deck
cards := deck.New()

// Custom deck with options
cards := deck.New(deck.WithoutJokers(), deck.WithSuit(deck.Spades, deck.Hearts))
```

### Functions

- `New(...options)` - Creates a new deck with specified options
- `Shuffle(cards []deck.Card)` - Randomizes the order of cards in the deck
- `Sort(cards []deck.Card)` - Sorts the cards in a specified order
- `Deal(cards []deck.Card, hands, cardsPerHand int)` - Deals cards to multiple hands
- `String(card deck.Card)` - Returns a string representation of a card

## Examples

### Creating a Game of Blackjack

```go
package main

import (
    "fmt"
    "github.com/laureanorios95/deck"
)

func main() {
    cards := deck.New()
    cards = deck.Shuffle(cards)
    
    var playerHand, dealerHand []deck.Card
    
    // Deal initial cards
    playerHand = append(playerHand, cards[0], cards[2])
    dealerHand = append(dealerHand, cards[1], cards[3])
    cards = cards[4:]
    
    fmt.Println("Player hand:", playerHand)
    fmt.Println("Dealer hand:", dealerHand)
}
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

Jon Calhoun - [gophercises.com](https://gophercises.com/)
