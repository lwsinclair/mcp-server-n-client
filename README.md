[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/tqmvt-mcp-server-n-client-badge.png)](https://mseep.ai/app/tqmvt-mcp-server-n-client)

# Test MCP Server

A Model Context Protocol (MCP) server for managing user data with support for resources, tools, and prompts.

## Features

### Resources

The server provides two resource endpoints for accessing user data:

- **All Users** (`users://all`) - Retrieves all users from the database
- **User Profile** (`users://{userId}/profile`) - Retrieves a specific user's profile by ID

### Tools

Three tools are available for user management:

1. **create-user** - Create a new user with specified details
   - Parameters: name, email, address, phone
2. **create-random-user** - Automatically generate and create a user with fake data
   - Uses AI sampling to generate realistic user information
3. **generate-fake-user** (Prompt) - Generate fake user data based on a given name
   - Parameter: name

## Installation

```bash
npm install
```

## Requirements

- Node.js (with ES modules support)
- Dependencies:
  - `@modelcontextprotocol/sdk`
  - `zod`

## Usage

### Starting the Server

```bash
npm start
```

The server uses stdio transport for communication.

### Resource Access

**Get all users:**

```
users://all
```

**Get specific user profile:**

```
users://123/profile
```

### Tool Usage

**Create a user:**

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "address": "123 Main St",
  "phone": "555-0123"
}
```

**Create a random user:**
No parameters required - automatically generates fake user data using AI sampling.

## Data Storage

User data is stored in `./src/data/users.json` as a JSON array. Each user object contains:

- `id` (number) - Auto-incremented user ID
- `name` (string) - User's full name
- `email` (string) - Email address
- `address` (string) - Physical address
- `phone` (string) - Phone number

## Server Capabilities

- **Resources**: Query user data via URI schemes
- **Tools**: Perform user management operations
- **Prompts**: Generate templated prompts for user creation

## Development

The server is built using the Model Context Protocol SDK and implements:

- Resource templates with dynamic URI parameters
- Tool definitions with Zod schema validation
- AI sampling for generating fake data
- File-based persistence

## License

MIT

## Notes

- User IDs are auto-incremented starting from the current user count + 1
- All operations return JSON responses
- Error handling is implemented for user not found scenarios
- The server uses the sampling API to generate realistic fake user data
