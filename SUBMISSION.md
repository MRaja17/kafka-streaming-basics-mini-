# Kafka Streaming Basics — Assignment Submission

Repo: MRaja17/kafka-streaming-basics-mini  
Project code location: kafka-streaming-basics-mini/ (folder inside repo)

---

## Easy 1 — Key concept in my own words
Kafka Streaming (Kafka Streams) means processing data continuously as events arrive in Kafka topics.
Instead of waiting to collect data and processing later (batch), we build a **streaming topology**
(filter → transform → aggregate/join) that runs all the time and produces output in near real time.

Core concepts:
- **Topic**: stream of records (events)
- **KStream**: unbounded stream of events
- **Topology**: processing pipeline (steps connected together)
- **State**: local storage used for aggregations/windows/joins
- **Consumer group scaling**: more partitions + more app instances = more throughput

---

## Easy 2 — Toy example (Kafka Streaming Basics)
Toy example idea:
- Read messages from `input-topic`
- Remove blanks
- Keep only messages with length >= 5
- Convert to UPPERCASE
- Write to `output-topic`

This uses basic Kafka Streams operators:
- `stream(topic)`
- `filter(...)`
- `mapValues(...)`
- `to(outputTopic)`

---

## Intermediate 1 — Apply on a “real dataset” + explain results
Example real dataset pattern: **NYC taxi trips** or **clickstream logs** arriving as JSON strings.

Sample input event:
```json
{"trip_id":"t1","distance":2.3,"payment":"CARD"}
