# Skill: API Design

Use this skill when the user wants to design, plan, or review an API (REST, GraphQL, or other).

## When to Use

- User asks to "design an API" or "plan endpoints"
- User discusses API structure, routes, or data models
- User wants to review existing API design for improvements

## Instructions

1. Clarify the API purpose and target users
2. Define resources and endpoints following REST conventions:
   - Use nouns for resource paths (e.g., `/users`, `/orders`)
   - Use standard HTTP methods (GET, POST, PUT, DELETE)
   - Follow consistent naming conventions
3. Design request/response schemas with clear field types
4. Consider:
   - Authentication and authorization requirements
   - Pagination for list endpoints
   - Error response format consistency
   - Versioning strategy
5. Document each endpoint with:
   - Path, method, description
   - Request body schema
   - Response schema (success and error)
   - Required permissions
6. Provide OpenAPI/Swagger spec skeleton if applicable
