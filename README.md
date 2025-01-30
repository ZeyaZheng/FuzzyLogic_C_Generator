# PoS Order Synchronization Project

## Overview
This project implements a synchronization system for Point of Sale (PoS) order data between client servers (e.g., supermarkets) and a centralized master server. The system ensures efficient data flow using periodic API calls and ORM queries, as depicted in the architecture diagram.

The project is developed using **Odoo** (versions 15 and 17) and relies on PostgreSQL databases for data storage and retrieval. Key functionalities include:
- Periodic data synchronization via cron jobs.
- Centralized reporting via a custom SQL view.
- Modular code organization for client and master servers.

---

## Software Architecture
Below is the architecture of the project:

![pos_order_sync_architecture](./pos_order_sync_architecture.png)

### Key Components
1. **Client Server (Point of Sale, Supermarkets)**  
   - Generates PoS orders.
   - Synchronizes data with the Message Broker Server every 2 minutes via API.

2. **Message Broker Server**  
   - Collects PoS orders from multiple client servers.
   - Synchronizes with the Master Server every 15 minutes.

3. **Master Server**  
   - Aggregates data from Message Broker Servers.
   - Maintains a data warehouse for consolidated reporting.
   - Generates custom SQL views for reporting dashboards.

4. **Sales Reporting Dashboard**  
   - Queries data from the SQL view for real-time visualization.

---

## Project File Structure
The project is organized into two main directories: **Client End** and **Master End**, each with distinct responsibilities.

### 1. Codes on Client End
**Path:** `Codes on Client End/pos_orders_sync`  
This module handles PoS order generation, synchronization with the Message Broker Server, and local configurations.

- **Controllers** (`controllers`):  
  Contains logic for handling APIs and synchronization tools.
  - `pos_orders_sync_tool.py`: Core sync logic.

- **Models** (`models`):  
  Defines the database models and business logic for PoS orders.
  - Key
