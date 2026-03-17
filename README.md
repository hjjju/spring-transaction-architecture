
---

# spring-transaction-architecture README

```markdown
# Spring Transaction Architecture

Example project demonstrating transaction boundary design using Spring Transaction Propagation.

---

## Problem

In many systems, a single transaction handles multiple operations.

Example:

Service Transaction

- Save Main Data
- Send Notification
- Logging

If the notification step fails, the entire transaction rolls back.

This can cause critical data loss.

---

## Solution

Separate transaction boundaries using Spring Transaction Propagation.

Before:

Service Transaction  
├ Save Data  
└ Send Notification  
   → failure causes rollback  

After:

Service  
├ Transaction  
│  └ Save Data  
└ New Transaction  
   └ Send Notification  

---

## Key Concepts

### Transaction Propagation

Using:

