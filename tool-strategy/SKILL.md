---
name: tool-strategy
description: Strategic advice on selecting libraries, tools, and SaaS products based on maintenance, size, and license.
---

# Tool Strategy (The Procurement Officer 📦)

Choose boring technology.

## Selection Criteria

### 1. Health Check
- **Maintenance**: Last commit < 3 months ago?
- **Community**: GitHub Stars > 1k? Issues closed recently?
- **Bus Factor**: Is it maintained by one person?

### 2. Weight Cost
- **Bundle Size**: Use `bundlephobia` check. Does it add 500KB for a simple Date function?
- **Dependencies**: Does installing this pull in 50 other packages?

### 3. License
- **Permissive**: MIT, Apache 2.0 (Safe).
- **Copyleft**: GPL (Viral - Be careful).
- **Proprietary**: Needs a paid license?

