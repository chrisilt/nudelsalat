# Nudelsalat

A cross-platform React Native application that runs on web, iOS, and Android with a PostgreSQL database backend.

## Tech Stack

- **Frontend**: React Native with Expo
- **Web Support**: React Native Web
- **Backend**: Express.js with TypeScript
- **Database**: PostgreSQL with Prisma ORM

## Prerequisites

- Node.js 18+ and npm
- PostgreSQL database
- Expo CLI (installed automatically via npx)

## Getting Started

### 1. Install Dependencies

```bash
npm install
```

### 2. Set Up Environment

Copy the example environment file and configure your database:

```bash
cp .env.example .env
```

Edit `.env` and update the `DATABASE_URL` with your PostgreSQL connection string:

```
DATABASE_URL="postgresql://USER:PASSWORD@HOST:PORT/DATABASE?schema=public"
```

### 3. Set Up Database

Generate the Prisma client and push the schema to your database:

```bash
npm run db:generate
npm run db:push
```

### 4. Run the Application

#### Start the Expo App (Web, iOS, Android)

```bash
# Start the development server
npm start

# Run on specific platform
npm run web      # Web browser
npm run ios      # iOS simulator (macOS only)
npm run android  # Android emulator
```

#### Start the Backend Server

```bash
# Development mode with hot reload
npm run server:dev

# Production mode
npm run server
```

## Project Structure

```
nudelsalat/
├── App.tsx              # Main React Native app component
├── index.ts             # App entry point
├── app.json             # Expo configuration
├── package.json         # Dependencies and scripts
├── tsconfig.json        # TypeScript config for React Native
├── tsconfig.server.json # TypeScript config for server
├── prisma/
│   └── schema.prisma    # Database schema
├── server/
│   └── index.ts         # Express API server
└── assets/              # Images and fonts
```

## Available Scripts

### Frontend (Expo)
- `npm start` - Start Expo development server
- `npm run web` - Start web development server
- `npm run ios` - Start iOS simulator
- `npm run android` - Start Android emulator

### Backend
- `npm run server` - Start API server
- `npm run server:dev` - Start API server with hot reload

### Database
- `npm run db:generate` - Generate Prisma client
- `npm run db:push` - Push schema changes to database
- `npm run db:migrate` - Create and apply migrations
- `npm run db:studio` - Open Prisma Studio (database GUI)

## API Endpoints

The backend server runs on port 3001 by default.

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health` | Health check |
| GET | `/api/users` | Get all users |
| POST | `/api/users` | Create a user |
| GET | `/api/posts` | Get all posts |
| POST | `/api/posts` | Create a post |

## Development

### Adding New Database Models

1. Edit `prisma/schema.prisma` to add your models
2. Run `npm run db:generate` to update the Prisma client
3. Run `npm run db:push` or `npm run db:migrate` to update the database

### Building for Production

For web deployment:
```bash
npx expo export --platform web
```

For native apps, refer to the [Expo documentation](https://docs.expo.dev/build/introduction/).

## License

MIT