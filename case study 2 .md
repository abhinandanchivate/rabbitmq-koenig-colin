## 🏆 ** RabbitMQ Case Study: E-Commerce Order Processing System**  

### ✅ **Objective**  
Build a scalable **E-Commerce Order Processing System** using RabbitMQ with the following features:  
✔️ Real-time order processing  
✔️ Parallel processing for different order types  
✔️ Notifications for customers  
✔️ Analytics and logging  
✔️ Dead-letter queue (DLQ) for failed messages  

---

## 🎯 **Use Case Overview**
An e-commerce company handles **different types of orders**:
1. **Normal Orders** – Standard orders placed by customers.  
2. **Priority Orders** – High-priority orders that need to be processed quickly.  
3. **Failed Orders** – Orders that encounter processing failures should go to a **Dead Letter Queue** (DLQ) for retry or manual investigation.  
4. **Customer Notifications** – Customers should receive real-time updates for their orders.  
5. **Order Analytics** – Orders should be logged and aggregated for reporting and monitoring.  

---

## ✅ **Architecture Overview**
### Components:
1. **Exchange Type:** `topic`
2. **Queues:**
   - `order_queue` → For normal orders  
   - `priority_order_queue` → For priority orders  
   - `notification_queue` → For customer notifications  
   - `analytics_queue` → For order logging and analysis  
   - `failed_order_queue` → For dead-letter queue (DLQ)  

### RabbitMQ Binding Rules:
| Routing Key Pattern                   | Queue                  | Purpose                           |
|----------------------------------------|------------------------|-----------------------------------|
| `order.normal.*`                      | `order_queue`          | Handles normal orders            |
| `order.priority.#`                    | `priority_order_queue` | Handles all priority orders       |
| `order.notification.*`                | `notification_queue`   | Handles customer notifications    |
| `order.analytics.*`                   | `analytics_queue`      | Handles order logging             |
| `order.failed.#`                      | `failed_order_queue`   | Handles failed orders             |

---

## ✅ **Implementation Plan**
### 1. **Exchange**: Create a `topic` exchange  
### 2. **Producers**:
- Order Producer → Sends new orders  
- Notification Producer → Sends customer notifications  
- Analytics Producer → Sends order statistics  

### 3. **Consumers**:
- **Order Consumer** → Normal order processing  
- **Priority Order Consumer** → Fast-track processing  
- **Notification Consumer** → Send customer notifications  
- **Analytics Consumer** → Logs order stats  
- **Failed Order Consumer** → Handles retries  

---

## 📌 **Step 1: Create the Exchange and Queues**
### 🔥 `setup.py`


   

---

## 📌 **Step 2: Create the Order Producer**
### 🔥 `order_producer.py`


---

## 📌 **Step 3: Create the Order Consumer**
### 🔥 `order_consumer.py`

---

## 📌 **Step 4: Create the Notification Consumer**
### 🔥 `notification_consumer.py`


---

## 📌 **Step 5: Create the Analytics Consumer**
### 🔥 `analytics_consumer.py`

---

## 📌 **Step 6: Create the Failed Order Consumer**
### 🔥 `failed_order_consumer.py`


---

## ✅ **How It Works**
1. The `Order Producer` sends messages based on:
   - `order.normal.*`  
   - `order.priority.#`  
2. Orders are processed by the `Order Consumer`.  
3. If an order fails → It is routed to the `failed_order_queue`.  
4. Customer notification and analytics are handled asynchronously.  

---

## ✅ **Example Output**
### **Order Consumer:**
```
[x] Processing Order: {'id': 2, 'product': 'Laptop', 'quantity': 3, 'price': 400, 'priority': False}
[!] Order Failed: {'id': 2, 'product': 'Laptop', 'quantity': 3, 'price': 400, 'priority': False}
```

### **Failed Order Consumer:**
```
[Failed] Order Failed: {'id': 2, 'product': 'Laptop', 'quantity': 3, 'price': 400, 'priority': False}
```

---

Enhancements:
✔️ Retry Logic
Use a Dead Letter Exchange (DLX) to store failed messages.
Define a TTL (Time-to-Live) for messages before they are moved to the DLQ.
Implement a retry mechanism:
If a message fails, it will be sent to the DLQ.
After a delay, the message will be re-queued for retry.
After max_retries, the message will be logged or discarded.
✔️ Monitoring
Implement message count monitoring using RabbitMQ Management API.
Log processing status.
Provide insights into:
Number of processed orders.
Number of failed orders.
Retry counts.
📌 Architecture Update
➡️ Add a retry queue with TTL for retry attempts.
➡️ Add a dead-letter queue to handle permanent failures.
➡️ Use headers to track retry count.
➡️ Implement monitoring using RabbitMQ HTTP API.



