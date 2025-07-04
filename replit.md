# AI-Powered PPC Campaign Generator

## Overview

This is a full-stack web application that helps users generate Google Ads campaigns with AI-powered keyword analysis, ad group organization, and ad copy creation. The application analyzes seed keywords for search intent, groups them into logical ad groups, and generates compelling ad copy for each group.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for client-side routing
- **Build Tool**: Vite with hot module replacement
- **UI Components**: Radix UI primitives with custom styling

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ESM modules
- **API**: RESTful endpoints for campaign management
- **AI Integration**: OpenAI GPT-4o for keyword analysis and ad generation
- **Database**: PostgreSQL with Drizzle ORM
- **Session Storage**: PostgreSQL-backed sessions with connect-pg-simple

### Data Storage Solutions
- **Primary Database**: PostgreSQL (Neon serverless)
- **ORM**: Drizzle ORM with Zod schema validation
- **Migration Strategy**: Drizzle Kit for schema migrations
- **Fallback Storage**: In-memory storage for development/testing

## Key Components

### Database Schema
The application uses a normalized relational schema:
- **Campaigns**: Main container for PPC campaigns
- **Ad Groups**: Logical groupings of related keywords
- **Keywords**: Individual search terms with intent analysis
- **Ads**: Generated ad copy for each ad group
- **Negative Keywords**: AI-generated keywords to prevent irrelevant clicks
- **Analysis Results**: Aggregated keyword intent and campaign statistics

### AI Services
- **Keyword Analysis**: Categorizes keywords by search intent (transactional, informational, navigational)
- **Budget-Based Selection**: AI analyzes imported keyword data and selects top performers based on CPC, volume, and budget constraints
- **Ad Group Generation**: Groups similar keywords by theme and intent
- **Ad Copy Generation**: Creates headlines and descriptions optimized for each ad group
- **Negative Keyword Generation**: Automatically generates negative keywords to prevent irrelevant clicks and save budget

### API Endpoints
- `GET /api/campaigns` - List all campaigns
- `GET /api/campaigns/:id` - Get campaign with full details
- `POST /api/campaigns/analyze` - Analyze keywords and generate campaign (manual input)
- `POST /api/campaigns/budget-analyze` - Generate budget-optimized campaign from Google Sheets data

## Data Flow

### Manual Keywords Flow
1. **User Input**: User enters seed keywords and optional campaign details
2. **AI Analysis**: Keywords are analyzed by Gemini for search intent and categorization
3. **Campaign Generation**: System creates campaign structure with ad groups and ads
4. **Data Persistence**: All generated data is saved to in-memory storage
5. **Results Display**: User sees comprehensive campaign structure with analytics

### Google Sheets Import Flow
1. **CSV Upload**: User uploads Google Keyword Planner CSV with CPC and volume data
2. **Data Parsing**: System extracts keyword metrics (CPC, search volume, competition)
3. **Budget Configuration**: User sets daily budget, target CPC, and campaign parameters
4. **AI Selection**: Gemini analyzes all keywords and selects top performers within budget
5. **Campaign Optimization**: System generates ad groups and ads for selected keywords only
6. **Cost Analysis**: Provides estimated daily spend and performance metrics

## External Dependencies

### Production Dependencies
- **AI Service**: OpenAI API for keyword analysis and ad generation
- **Database**: Neon PostgreSQL for data persistence
- **UI Components**: Radix UI for accessible component primitives
- **Styling**: Tailwind CSS for utility-first styling

### Development Dependencies
- **Build Tools**: Vite for fast development and building
- **Type Checking**: TypeScript for static type analysis
- **Linting**: ESLint and Prettier for code quality
- **Database Tools**: Drizzle Kit for schema management

## Deployment Strategy

### Build Process
- **Frontend**: Vite builds React app to `dist/public`
- **Backend**: esbuild bundles server code to `dist/index.js`
- **Database**: Drizzle migrations applied via `db:push` command

### Environment Configuration
- **Development**: Uses tsx for TypeScript execution with hot reload
- **Production**: Compiled JavaScript with Node.js runtime
- **Database**: PostgreSQL connection via DATABASE_URL environment variable
- **AI**: OpenAI API key required for keyword analysis features

### Production Considerations
- Static file serving handled by Express in production
- Vite dev server only used in development mode
- Database migrations must be run before deployment
- OpenAI API key must be configured in production environment

## Changelog

```
Changelog:
- July 02, 2025. Initial setup with OpenAI integration
- July 02, 2025. Switched from OpenAI to Google Gemini AI service  
- July 02, 2025. Added negative keyword generation feature for cost optimization
- July 02, 2025. Added Google Sheets integration for CSV import from Google Keyword Planner
- July 02, 2025. Implemented budget-based keyword selection with AI optimization
- July 02, 2025. Enhanced database schema to support CPC, search volume, and budget constraints
```

## User Preferences

```
Preferred communication style: Simple, everyday language.
```