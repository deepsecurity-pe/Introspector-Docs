---
title: FAQ
nav_order: 8
---

## Is this a replacement for Burp Collaborator / interactsh?

Not exactly. Those are excellent OOB utilities. Introspector focuses on being a **workflow hub**: listeners + payload hosting + redirect intel + modules + a log UI you can treat as an execution trace.

## Why do I see DNS but no HTTP?

Common causes:
- the target resolves names but has egress restrictions for HTTP/HTTPS
- the component uses DNS for validation or discovery but never fetches
- the request was blocked after resolution

## Do I need port 53?

Only if you want DNS callbacks. You can run HTTP-only for many use cases.
