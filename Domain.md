```mermaid
classDiagram

ticketmachine "1" -- "1" customer : serves
ticket "*" -- "0-1" international fee : adds to price
ticketmachine "1" -- "*" ticket : prints
Bank  "1" -- "1" ticketmachine : authenticates debit cards
Credit_co "1" -- "1"  ticketmachine : authenticates credit cards
ticket "*" -- "0-1" date : valid on
NS-servers -- "*" ticketmachine : calculates price for
ticketmachine "1" -- "*" receipt : prints
ticket "*" -- "*" receipt : is described on
ticketmachine "1" -- "1" Coin machine : accepts cash in
ticketmachine "1" -- "1" CardReader : scans credit/debit cards with
customer "*"  -- "1" CardReader : scans credit/debit card on

class ticketmachine

class ticket{
    +starting point
    +destination
    +class
    +discount
}

class Coinmachine{
    +CurrentTotal
}

class receipt{
    +Total
    +tax
}





```