# KasirFIFO-FirtsInFirstOut-CPro2
Project Intro to Computer Programming - Team 3

## 👥 Tim Kami
| Prima Aditama  | Inventaris (`inventory.py`) |
| Bachtiar Arief N | Engine HPP FIFO (`cogs.py`) |
| Andra Putra P | Kasir POS (`pos.py`) |
| Wisam Ikbar D | Laporan, CLI, Unit Test (`main.py`, `report.py`) |

## 📐 Class Diagram
```mermaid
classDiagram
    direction TB

    class Product {
        +str id
        +str name
        +float selling_price
        +list~Batch~ batches
        +add_batch(purchase_price, qty, date)
        +total_stock() int
    }

    class Batch {
        +float purchase_price
        +int qty
        +str arrival_date
    }

    class Inventory {
        +dict~str,Product~ products
        +add_product(id, name, selling_price)
        +find_product(id) Product
        +list_products() list
        +restock(id, qty, purchase_price)
    }

    class HPPEngine {
        +compute_fifo(product, qty) tuple
        +compute_margin(profit, sales) float
        +compute_markup(profit, cogs) float
    }

    class TransactionItem {
        +Product product
        +int qty
        +subtotal() float
        +item_cogs() float
    }

    class Transaction {
        +list~TransactionItem~ items
        +float discount
        +float paid_amount
        +total_sales() float
        +total_cogs() float
        +gross_profit() float
        +change_due() float
    }

    class Receipt {
        +Transaction transaction
        +format_receipt() str
        +print_receipt() void
    }

    class Report {
        +list~Transaction~ history
        +daily_summary() dict
        +total_revenue() float
        +total_profit() float
        +print_report() void
    }

    class KasirApp {
        +Inventory inventory
        +Report report
        +main_menu() void
        +cashier_module() void
        +restock_module() void
        +view_stock_module() void
        +report_module() void
        +validate_choice(input) bool
    }

    %% Relasi
    Inventory "1" *-- "*" Product : has-a
    Product "1" *-- "*" Batch : has-a
    Transaction "1" *-- "*" TransactionItem : has-a
    KasirApp "1" *-- "1" Inventory : has-a
    KasirApp "1" *-- "1" Report : has-a
    TransactionItem "*" --> "1" Product : refers-to
    Receipt "1" --> "1" Transaction : formats
    KasirApp ..> HPPEngine : uses
    KasirApp ..> Receipt : uses
    HPPEngine ..> Product : reads

    %% Styling Warna
    classDef prima fill:#dbeafe,stroke:#3b82f6,stroke-width:2px,color:#000;
    classDef bachtiar fill:#dcfce7,stroke:#22c55e,stroke-width:2px,color:#000;
    classDef andra fill:#fef08a,stroke:#eab308,stroke-width:2px,color:#000;
    classDef wisam fill:#f3e8ff,stroke:#a855f7,stroke-width:2px,color:#000;
    classDef core fill:#f3f4f6,stroke:#9ca3af,stroke-width:2px,color:#000;

    class Inventory:::prima
    class Product:::prima
    class Batch:::prima
    class HPPEngine:::bachtiar
    class Transaction:::andra
    class TransactionItem:::andra
    class Report:::wisam
    class Receipt:::wisam
    class KasirApp:::core
```
