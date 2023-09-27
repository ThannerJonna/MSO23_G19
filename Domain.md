```mermaid
classDiagram
ticket "*" -- "0-1" international fee : added to price
ticketmachine "1" -- "*" ticket : prints
ticketmachine "1" -- "1" Debit_autherisation_sys
ticketmachine "1" -- "1" Credit_autherisation_sys

class ticketmachine

class ticket

class Debit_autherisation_sys

class Credit_autherisation_sys
```