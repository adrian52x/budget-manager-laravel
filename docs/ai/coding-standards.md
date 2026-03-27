# Coding Standards

Controllers:
- must remain thin
- only call services

Business logic:
- must live in Services

Validation:
- use Form Requests

Queries:
- avoid N+1
- use eager loading

Naming:
- singular model names
- plural table names

Laravel rules:
- Always use route model binding
- Use policies for authorization
- Use Form Requests for validation
- Avoid business logic in controllers
- Prefer Eloquent relationships