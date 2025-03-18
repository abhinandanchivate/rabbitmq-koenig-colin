Below is a **complete Python code** demonstrating all **25 operations** on a **Quorum Queue** in RabbitMQ using the `pika` library.

---

## ✅ **Install Dependencies**
```bash
pip install pika
```

---

## ✅ **Setup RabbitMQ URL**
Set up the connection to RabbitMQ using a complete URL:

```python
URL = "amqp://guest:guest@localhost:5672/%2F"
```

---

## ✅ **Complete Code for All 25 Quorum Queue Operations**

### 📌 **1. Declare a Quorum Queue**
```python
import pika

params = pika.URLParameters(URL)
connection = pika.BlockingConnection(params)
channel = connection.channel()

# Declare quorum queue
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-queue-type': 'quorum'}
)

print("✅ Quorum queue declared")
connection.close()
```

---

### 📌 **2. Publish Messages to a Quorum Queue**
```python
connection = pika.BlockingConnection(params)
channel = connection.channel()

message = "Hello from Quorum Queue!"
channel.basic_publish(
    exchange='',
    routing_key='my_quorum_queue',
    body=message,
    properties=pika.BasicProperties(delivery_mode=2)
)

print(f"✅ Sent: '{message}'")
connection.close()
```

---

### 📌 **3. Consume Messages from a Quorum Queue**
```python
connection = pika.BlockingConnection(params)
channel = connection.channel()

def callback(ch, method, properties, body):
    print(f"✅ Received: {body.decode()}")
    ch.basic_ack(delivery_tag=method.delivery_tag)

channel.basic_consume(queue='my_quorum_queue', on_message_callback=callback)
print("🚀 Waiting for messages. CTRL+C to exit.")
channel.start_consuming()
```

---

### 📌 **4. Delete a Quorum Queue**
```python
connection = pika.BlockingConnection(params)
channel = connection.channel()

channel.queue_delete(queue='my_quorum_queue')
print("✅ Quorum queue deleted.")
connection.close()
```

---

### 📌 **5. Purge a Quorum Queue**
```python
connection = pika.BlockingConnection(params)
channel = connection.channel()

channel.queue_purge(queue='my_quorum_queue')
print("✅ Quorum queue purged.")
connection.close()
```

---

### 📌 **6. Set Message TTL for Quorum Queue**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-message-ttl': 60000}
)
```

---

### 📌 **7. Set Maximum Length of Quorum Queue**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-max-length': 10}
)
```

---

### 📌 **8. Set Maximum Size of Quorum Queue**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-max-length-bytes': 102400}
)
```

---

### 📌 **9. Set Dead Letter Exchange**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-dead-letter-exchange': 'my_dlx'}
)
```

---

### 📌 **10. Set Dead Letter Routing Key**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={
        'x-dead-letter-exchange': 'my_dlx',
        'x-dead-letter-routing-key': 'dead_key'
    }
)
```

---

### 📌 **11. Set Per-Message TTL**
```python
channel.basic_publish(
    exchange='',
    routing_key='my_quorum_queue',
    body='Message with TTL',
    properties=pika.BasicProperties(expiration='5000')
)
```

---

### 📌 **12. Inspect Quorum Queue State**
```bash
curl -u guest:guest http://localhost:15672/api/queues/%2F/my_quorum_queue
```

---

### 📌 **13. Set Quorum Queue Replication Factor**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-quorum-initial-group-size': 5}
)
```

---

### 📌 **14. Bind Quorum Queue to Exchange**
```python
channel.queue_bind(queue='my_quorum_queue', exchange='my_exchange', routing_key='my_key')
```

---

### 📌 **15. Unbind Quorum Queue from Exchange**
```python
channel.queue_unbind(queue='my_quorum_queue', exchange='my_exchange', routing_key='my_key')
```

---

### 📌 **16. Configure High Availability**  
👉 Already built into quorum queues

---

### 📌 **17. Priority Support**  
👉 NOT SUPPORTED for Quorum Queues

---

### 📌 **18. Acknowledge Messages**
```python
def callback(ch, method, properties, body):
    ch.basic_ack(delivery_tag=method.delivery_tag)
```

---

### 📌 **19. Reject a Message Without Requeue**
```python
channel.basic_reject(delivery_tag=method.delivery_tag, requeue=False)
```

---

### 📌 **20. Reject and Requeue a Message**
```python
channel.basic_reject(delivery_tag=method.delivery_tag, requeue=True)
```

---

### 📌 **21. Negative Acknowledgement (Nack)**
```python
channel.basic_nack(delivery_tag=method.delivery_tag, requeue=False)
```

---

### 📌 **22. Check if Queue Exists**
```python
try:
    channel.queue_declare(queue='my_quorum_queue', passive=True)
    print("✅ Queue exists.")
except pika.exceptions.ChannelClosedByBroker:
    print("❌ Queue does not exist.")
```

---

### 📌 **23. Close Connection**
```python
connection.close()
```

---

### 📌 **24. Set Auto-Delete**  
👉 Quorum queues are durable — not recommended.

```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    auto_delete=True
)
```

---

### 📌 **25. Set Overflow Policy**
```python
channel.queue_declare(
    queue='my_quorum_queue',
    durable=True,
    arguments={'x-overflow': 'reject-publish'}
)
```

---

## ✅ **Complete URL Example**
```python
URL = "amqp://guest:guest@localhost:5672/%2F"
params = pika.URLParameters(URL)
connection = pika.BlockingConnection(params)
channel = connection.channel()
```

---

## ✅ **Summary of Operations**
| Operation | Description |
|-----------|-------------|
| Declare Queue | `queue_declare` |
| Publish | `basic_publish` |
| Consume | `basic_consume` |
| Acknowledge | `basic_ack` |
| Reject | `basic_reject` |
| Delete | `queue_delete` |
| Purge | `queue_purge` |
| Set TTL | `x-message-ttl` |
| Set Size | `x-max-length-bytes` |
| Dead Letter Exchange | `x-dead-letter-exchange` |
| Overflow Policy | `x-overflow` |
| Close Connection | `connection.close()` |
| Inspect State | `curl` command |
| Negative Acknowledgement | `basic_nack` |
| Replication Factor | `x-quorum-initial-group-size` |
| Priority | ❌ Not Supported |

---
