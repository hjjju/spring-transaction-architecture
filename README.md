# Spring Transaction Architecture

Example project demonstrating transaction boundary design in Spring Boot services.

---

## Problem

During production operations, certain service processes contained both
core data operations and secondary processing within a single transaction.

If a secondary process failed, the entire transaction was rolled back,
including critical data operations.

This increased the impact scope of failures in production environments.

---

## Solution

The service structure was redesigned to separate transaction boundaries.

Core data operations remained in the main transaction,
while secondary processes were executed in independent transactions.

This was implemented using Spring Transaction Propagation.

---

## Result

- Reduced the impact scope of failures
- Improved production system stability
- Allowed non-critical processes to fail without affecting core data operations
