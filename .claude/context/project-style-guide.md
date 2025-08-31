---
created: 2025-08-31T14:10:07Z
last_updated: 2025-08-31T14:10:07Z
version: 1.0
author: Claude Code PM System
---

# Project Style Guide

## Development Philosophy

### Core Principles from CLAUDE.md
- **Conciseness First**: Implement the most concise solution that changes as little code as possible
- **No Partial Implementation**: Complete every feature fully - no placeholders or simplified implementations
- **No Code Duplication**: Check existing codebase to reuse functions and constants
- **No Dead Code**: Either use code or delete it completely from codebase
- **No Over-Engineering**: Choose simple functions over unnecessary abstractions, factory patterns, or middleware

## Code Organization Standards

### File Naming Conventions

#### Frontend (React/TypeScript)
```
components/
├── atoms/               # Basic UI elements
│   ├── Button.tsx
│   └── Input.tsx
├── molecules/           # Simple component groups
│   ├── SearchBox.tsx
│   └── UserCard.tsx
├── organisms/           # Complex UI sections
│   ├── TicketList.tsx
│   └── NavigationBar.tsx
└── templates/           # Page layouts
    ├── DashboardLayout.tsx
    └── AuthLayout.tsx
```

#### Backend (Node.js/TypeScript)
```
src/
├── controllers/         # Route handlers
│   ├── ticketController.ts
│   └── userController.ts
├── services/           # Business logic
│   ├── TicketService.ts
│   └── UserService.ts
├── models/             # Data models
│   ├── Ticket.ts
│   └── User.ts
├── middleware/         # Express middleware
│   ├── auth.ts
│   └── validation.ts
└── utils/              # Utility functions
    ├── database.ts
    └── logger.ts
```

### Directory Structure Principles
- **Feature-based organization**: Group related functionality together
- **Separation of concerns**: Clear boundaries between UI, business logic, and data
- **Shared code isolation**: Common utilities in dedicated directories
- **Test colocation**: Tests alongside source files or in parallel structure

## Naming Conventions

### TypeScript/JavaScript Standards

#### Variables and Functions
```typescript
// camelCase for variables and functions
const userName = 'john_doe';
const ticketId = 12345;
const responseTime = 1.5;

// Descriptive function names
function calculateAverageResponseTime(tickets: Ticket[]): number {}
function validateUserPermissions(user: User, resource: string): boolean {}
function formatTicketForDisplay(ticket: Ticket): DisplayTicket {}
```

#### Classes and Interfaces
```typescript
// PascalCase for classes and interfaces
class TicketService {
  private repository: TicketRepository;
}

interface UserPermissions {
  canCreateTickets: boolean;
  canViewAnalytics: boolean;
}

// Type definitions
type TicketStatus = 'open' | 'in_progress' | 'resolved' | 'closed';
type UserRole = 'fae' | 'sales_manager' | 'product_manager' | 'admin';
```

#### Constants
```typescript
// UPPER_SNAKE_CASE for constants
const MAX_UPLOAD_SIZE = 10485760; // 10MB
const DEFAULT_PAGE_SIZE = 25;
const API_BASE_URL = process.env.API_BASE_URL || 'http://localhost:3000';

// Configuration objects
const DATABASE_CONFIG = {
  HOST: process.env.DB_HOST,
  PORT: parseInt(process.env.DB_PORT || '5432'),
  NAME: process.env.DB_NAME
} as const;
```

### File and Component Naming

#### React Components
```typescript
// PascalCase for component files
// TicketListItem.tsx
export const TicketListItem: React.FC<TicketListItemProps> = ({ ticket }) => {
  return <div className="ticket-list-item">{/* Component content */}</div>;
};

// Custom hooks - camelCase with 'use' prefix
// useTicketFilters.ts
export const useTicketFilters = () => {
  // Hook implementation
};
```

#### API Routes and Endpoints
```typescript
// RESTful URL patterns - kebab-case
// GET /api/tickets
// GET /api/tickets/:id
// POST /api/tickets
// PUT /api/tickets/:id
// DELETE /api/tickets/:id

// Nested resources
// GET /api/users/:userId/tickets
// GET /api/knowledge-base/articles
// POST /api/design-tools/magnetic-circuit
```

## Code Style Standards

### TypeScript Configuration
```json
{
  "compilerOptions": {
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noImplicitAny": true,
    "exactOptionalPropertyTypes": true
  }
}
```

### ESLint Rules (Key Requirements)
```javascript
module.exports = {
  rules: {
    // No unused variables - aligns with "NO DEAD CODE" rule
    "@typescript-eslint/no-unused-vars": "error",
    
    // Consistent naming
    "@typescript-eslint/naming-convention": [
      "error",
      {
        "selector": "variable",
        "format": ["camelCase", "UPPER_CASE"]
      },
      {
        "selector": "function", 
        "format": ["camelCase"]
      },
      {
        "selector": "typeLike",
        "format": ["PascalCase"]
      }
    ],
    
    // Prevent code duplication
    "no-duplicate-imports": "error",
    "prefer-const": "error",
    
    // Consistent code style
    "indent": ["error", 2],
    "quotes": ["error", "single"],
    "semi": ["error", "always"]
  }
};
```

## Function and Method Standards

### Function Design Principles
```typescript
// Single responsibility - one clear purpose
function validateTicketData(ticket: CreateTicketRequest): ValidationResult {
  // Validation logic only
}

function saveTicketToDatabase(ticket: ValidatedTicket): Promise<Ticket> {
  // Database operations only  
}

// Pure functions when possible - no side effects
function calculatePriority(urgency: number, impact: number): Priority {
  return urgency * impact > 6 ? 'high' : 'normal';
}

// Clear parameter and return types
function searchTickets(
  query: string, 
  filters: TicketFilters,
  pagination: PaginationOptions
): Promise<SearchResults<Ticket>> {
  // Search implementation
}
```

### Error Handling Patterns
```typescript
// Use Result types for operations that can fail
type Result<T, E = Error> = { success: true; data: T } | { success: false; error: E };

async function createTicket(request: CreateTicketRequest): Promise<Result<Ticket>> {
  try {
    const validatedData = validateTicketData(request);
    if (!validatedData.isValid) {
      return { success: false, error: new ValidationError(validatedData.errors) };
    }
    
    const ticket = await saveTicketToDatabase(validatedData.data);
    return { success: true, data: ticket };
  } catch (error) {
    return { success: false, error: error as Error };
  }
}
```

## Testing Standards

### Test Organization
```
src/
├── components/
│   ├── TicketList.tsx
│   └── TicketList.test.tsx        # Co-located tests
├── services/
│   ├── TicketService.ts
│   └── TicketService.test.ts
└── __tests__/                     # Integration tests
    ├── api/
    └── components/
```

### Test Naming and Structure
```typescript
// Descriptive test names following "should [expected behavior] when [condition]"
describe('TicketService', () => {
  describe('createTicket', () => {
    it('should create ticket with valid data when user has permission', async () => {
      // Arrange
      const validTicketData = createMockTicketData();
      const authorizedUser = createMockUser({ role: 'fae' });
      
      // Act
      const result = await ticketService.createTicket(validTicketData, authorizedUser);
      
      // Assert
      expect(result.success).toBe(true);
      expect(result.data.id).toBeDefined();
      expect(result.data.status).toBe('open');
    });

    it('should return validation error when ticket data is invalid', async () => {
      // Test implementation following CLAUDE.md "NO CHEATER TESTS" rule
      // Must be accurate and reflect real usage
    });
  });
});
```

### Test Requirements (From CLAUDE.md)
- **NO CHEATER TESTS**: Tests must be accurate, reflect real usage, and be designed to reveal flaws
- **Verbose Tests**: Design tests to be verbose for debugging purposes
- **Test Every Function**: Implement tests for every function
- **No Mock Services**: Do not use mock services for anything

## Database and API Standards

### Database Naming
```sql
-- Table names: snake_case, plural
CREATE TABLE tickets (
  id SERIAL PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Column names: snake_case
-- Foreign keys: singular_table_name_id
CREATE TABLE ticket_comments (
  id SERIAL PRIMARY KEY,
  ticket_id INTEGER REFERENCES tickets(id),
  user_id INTEGER REFERENCES users(id),
  comment_text TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);
```

### API Response Formats
```typescript
// Consistent API response structure
interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: {
    code: string;
    message: string;
    details?: Record<string, any>;
  };
  meta?: {
    pagination?: PaginationMeta;
    timestamp: string;
  };
}

// Example usage
const response: ApiResponse<Ticket[]> = {
  success: true,
  data: tickets,
  meta: {
    pagination: { page: 1, total: 100, hasNext: true },
    timestamp: new Date().toISOString()
  }
};
```

## Documentation Standards

### Code Comments
```typescript
/**
 * Calculates the priority score for a ticket based on urgency and business impact.
 * Priority determines assignment queue and SLA requirements.
 * 
 * @param urgency - Scale 1-5, customer-reported urgency level
 * @param impact - Scale 1-5, business impact assessment  
 * @param customerTier - Enterprise/Standard/Basic affects multiplier
 * @returns Priority object with score and SLA target
 */
function calculateTicketPriority(
  urgency: number, 
  impact: number, 
  customerTier: CustomerTier
): TicketPriority {
  // Implementation
}

// Inline comments for complex logic only
const priorityScore = (urgency * impact) * tierMultiplier; // Weighted by customer tier
```

### README Standards
```markdown
# Component/Service Name

## Purpose
Brief description of what this component does and why it exists.

## Usage
```typescript
// Code example showing typical usage
const result = await ticketService.createTicket(ticketData);
```

## Dependencies  
- List of external dependencies
- Internal dependencies

## Testing
- How to run tests
- Test coverage requirements
- Mock data setup if needed
```

## Version Control Standards

### Git Commit Messages
```
feat: add ticket priority calculation algorithm
fix: resolve validation error in user registration  
refactor: extract database connection logic to utility
docs: update API documentation for ticket endpoints
test: add comprehensive tests for TicketService
chore: update dependencies and security patches
```

### Branch Naming
- `feature/ticket-priority-system`
- `bugfix/user-validation-error`  
- `refactor/database-connection-pooling`
- `hotfix/security-patch-auth`

## Performance Standards

### Code Efficiency
```typescript
// Prefer efficient algorithms and data structures
const ticketMap = new Map<number, Ticket>(); // O(1) lookup vs array O(n)

// Avoid nested loops when possible  
const groupedTickets = tickets.reduce((groups, ticket) => {
  const key = ticket.category;
  groups[key] = groups[key] || [];
  groups[key].push(ticket);
  return groups;
}, {} as Record<string, Ticket[]>);

// Use database-level operations vs multiple queries
const results = await db.query(`
  SELECT t.*, u.name as assignee_name 
  FROM tickets t 
  LEFT JOIN users u ON t.assignee_id = u.id 
  WHERE t.status = $1
`, ['open']);
```

### Resource Management
```typescript
// Always clean up resources (CLAUDE.md: NO RESOURCE LEAKS)
const dbConnection = await database.connect();
try {
  const result = await dbConnection.query(sql, params);
  return result;
} finally {
  await dbConnection.close(); // Always close connections
}

// Clear timeouts and intervals
const timeoutId = setTimeout(() => {}, 1000);
// ... later
clearTimeout(timeoutId);

// Remove event listeners
const handler = () => {};
element.addEventListener('click', handler);
// ... later  
element.removeEventListener('click', handler);
```

## Notes
- Style guide enforces CLAUDE.md absolute rules through tooling and process
- Emphasis on code quality, maintainability, and performance
- Clear separation of concerns and consistent patterns across codebase
- Comprehensive testing requirements ensuring robust, debuggable code