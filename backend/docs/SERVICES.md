# Backend Services Documentation

## Service Structure

```
backend/
├── src/
│   ├── index.ts              # Entry point
│   ├── middleware/           # Express middleware
│   ├── routes/               # API routes
│   │   ├── auth.ts
│   │   ├── interviews.ts
│   │   ├── questions.ts
│   │   ├── users.ts
│   │   └── analytics.ts
│   ├── controllers/          # Business logic
│   ├── models/               # Database models
│   ├── utils/                # Helper functions
│   └── config/               # Configuration
└── tests/                    # Test files
```

## Services

### Auth Service
Handles user authentication and authorization.
- Register new users
- Login with email/password
- Generate JWT tokens
- Refresh tokens
- Password reset
- OAuth integration

### Interview Service
Manages interview sessions.
- Start new interview
- Submit responses
- Save recordings
- Calculate scores
- Generate feedback

### Question Service
Manages question bank.
- Fetch questions by category
- Get random questions
- Search questions
- Track difficulty levels
- Update questions

### Analytics Service
Generates performance insights.
- Calculate scores
- Track progress
- Generate reports
- Create comparisons
- Build leaderboards

### User Service
Manages user profiles.
- Get user info
- Update profile
- Track statistics
- Manage preferences

## Database Models

### User
```sql
id, email, password, name, avatar_url, phone, subscription_type, created_at
```

### Interview
```sql
id, user_id, interview_type, question_id, duration, score, feedback, status, created_at
```

### Question
```sql
id, category, difficulty, question_text, sample_answer, keywords, created_at
```

### Analytics
```sql
id, user_id, interview_id, clarity_score, confidence_score, accuracy_score, created_at
```

## Environment Variables

```
PORT=8000
NODE_ENV=development
DATABASE_URL=postgresql://...
REDIS_URL=redis://...
JWT_SECRET=your-secret
OPENAI_API_KEY=your-key
```

## Running Tests

```bash
npm test
npm run test:watch
npm run test:coverage
```

## Error Handling

All endpoints return consistent error format:
```json
{
  "success": false,
  "error": "Error message",
  "code": "ERROR_CODE"
}
```

Error codes:
- `INVALID_REQUEST` - Invalid input
- `UNAUTHORIZED` - Not authenticated
- `FORBIDDEN` - No permission
- `NOT_FOUND` - Resource not found
- `SERVER_ERROR` - Internal server error
