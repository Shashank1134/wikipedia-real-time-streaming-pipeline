# 📡 Wikipedia Real-Time Streaming Pipeline (Project 9)

## 🔹 Overview

This project demonstrates a **real-time data streaming pipeline** using live Wikipedia edit events.

Unlike batch ETL systems, this pipeline ingests **continuous event streams** using Server-Sent Events (SSE) and processes them in real time using a producer-based architecture.

The project focuses on **streaming fundamentals**, including event ingestion, schema design, partitioning, and system architecture.

---

## 🔹 Architecture

Wikipedia SSE Stream
→ Python Producer
→ Streaming Layer (Kinesis / SQS / Kafka - conceptual)
→ Consumer (future extension)
→ Analytics / Storage

---

## 🔹 Key Features

* Real-time event ingestion (no polling)
* Continuous streaming using SSE
* Schema normalization for structured analytics
* Producer–consumer decoupled architecture
* Partitioning strategy using language as key
* Streaming system design (Kinesis/Kafka model)

---

## 🔹 Technologies Used

* Python
* SSE (Server-Sent Events)
* Requests, SSEClient
* AWS Kinesis (conceptual)
* Amazon SQS (conceptual)
* Apache Kafka (conceptual)

---

## 🔹 Event Schema

Each streaming event contains:

* `page_title` — Title of the Wikipedia page
* `language` — Wikipedia language edition (e.g., enwiki, ruwiki)
* `event_type` — Type of change (edit, log, categorize, etc.)
* `user` — Editor username or IP
* `is_bot` — Indicates if the edit was made by a bot
* `change_size` — Size of the change in bytes
* `event_time_utc` — Original event timestamp
* `ingestion_time_utc` — Time when event was received

---

## ▶️ How to Run

1. Clone the repository:

```
git clone https://github.com/YOUR_USERNAME/wikipedia-real-time-streaming-pipeline.git
cd wikipedia-real-time-streaming-pipeline
```

2. Install dependencies:

```
pip install -r requirements.txt
```

3. Run the producer:

```
python producer/wiki_sse_producer.py
```

The script will stream live Wikipedia events for **10 minutes** and print them in real time.

---

## 🔹 Sample Output

```json
{
  "event_time_utc": 1767354371,
  "ingestion_time_utc": "2026-01-02T11:46:13.757401+00:00",
  "source": "wikipedia",
  "page_title": "Battle of Al-Qarn (1160)",
  "language": "enwiki",
  "event_type": "edit",
  "user": "Afshar131",
  "is_bot": false,
  "change_size": 7117
}
```

---

## 🔹 Learnings

* Difference between batch processing and real-time streaming
* Event-driven architecture using continuous data streams
* Producer vs consumer separation
* Partition keys and shard-based parallelism
* Queue vs log-based streaming systems (SQS vs Kinesis/Kafka)
* Importance of schema design in streaming pipelines

---

## 🔹 Future Improvements

* Integrate AWS Kinesis (when cost constraints allow)
* Implement Lambda-based consumer
* Store streaming data in S3
* Add real-time analytics and windowed aggregations
* Extend pipeline using Kafka for full streaming capability

---

## 🔹 Author

**Shashank Sharma**
Aspiring Data Engineer / Cloud Engineer

---
