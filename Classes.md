```mermaid
classDiagram

class Comments{
    Aggregation is black
    Composition is white
}

ticket "*" -- "0-1" international fee
ticketmachine "1" *-- "*" ticket
Debit  "1" --* "1" ticketmachine 
Credit "1" --* "1"  ticketmachine 
Logger <-- "*" ticketmachine
MySQL_DB <-- ticketmachine
Marketing_DB <-- ticketmachine
ticketmachine "1" *-- "*" receipt
ticket "*" -- "*" receipt
ticketmachine "1" o-- "1" Coin machine
TaxCalculator "1" -- "*" ticketmachine 

ICard <|.. Credit
ICard <|.. Debit

class MySQL_DB{
    +returnPrice(string destination, string departure, int discount)
}

class sale{
    +amount
    +currency
    +timestamp
    +List~Tickets~
}

class errorLog{
    +List~Log~
}

class Log{
    +timestamp
    +errorcode
}


class ticketmachine{
    +id : int
    +ticketStock : int
    +receiptStock : int
    +inkStock : int 
    +makeLog() : void
    +makeReceipt() : void
    +makeTicket() : void
    +currentSelection~ticket~
    +nextCustomer()
}


class ticket{
    +starting point : string
    +destination : string
    +class : bool
    +price : int
    +amount : int
}


class Paymethod{
    +identifier : int
    +cancelTransaction()
    +rollBack()
}

class Coinmachine{
    +dispenseChange(int)
    +currentTotal() : int
}

class receipt{
    +transaction : sale
    +returnTax() : int
}


class ICard {
    <<Interface>>
 +ListReaders() : String[]
 +Connect(): void
 +Disconnect(): void
 +Transmit() : APDUResponse
 +BeginTransaction(): TransactionID
 +EndTransaction(): bool
 +CancelTransaction() : void
}

class Credit
```