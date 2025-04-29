---
layout: single
title:  "BookBean Cache Design"
date:   2024-01-08 19:03:13 -0800
categories: E-commerce
author_profile: true
---


### Local Cache vs Redis Cache 

| Feature         | Local Cache  | Redis Cache             |
|-----------------|--------------------------------------------|--------------------------------------|
| Storage         | In-process memory         | External Redis server                |
| Latency         | Nanoseconds                                | Milliseconds   |
| Sharing         | Process-specific                           | Shared across multiple services      |
| Persistence     | No             | Yes           |
| Scalability     | Limited by memory           | Horizontally scalable                |
| Concurrency     | Manual                 | Atomic ops; Redlock  |

Bookbean’s real-time recommendation system originally used in-memory caching to reduce latency. It worked well, but as traffic increased, it led to bottlenecks and inconsistent data across distributed processes.

### Initial Setup: Fast But Fragile

With horizontal scaling:
- Caches weren’t shared across instances
- Stale or missing data persisted in individual processes

### Solution: Redis Distributed Cache

Book metadata caching was moved to a Redis Cluster to provide shared access and more control.

- **Key format**: `book_info:<isbn>` → JSON-encoded value  
- **TTL**: 24 hours  
- **Fallback**: Empty/missing results are cached to prevent redundant API calls  
- **Locking**: Distributed locking to avoid thundering herd issues

| Problem               | Solution                                        |
|-----------------------|-------------------------------------------------|
| Cache inconsistency   | Redis provides a shared cache across all nodes |
| High API latency      | Cached Google Books responses with TTL         |
| Hot key contention    | Redlock to limit concurrent refreshes          |
| Cache penetration     | Cache empty responses for invalid ISBNs        |

### Results

- Average response time dropped: **600ms → 80ms**  
- Google API requests reduced by **95%**  
- System has been **stable in production for over 6 months**

---
