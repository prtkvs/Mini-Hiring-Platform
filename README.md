# TALENTFLOW - Mini Hiring Platform

A comprehensive React application for HR teams to manage jobs, candidates, and assessments. Built with modern web technologies and featuring a complete mock API with local persistence.

## Features

### 🎯 Jobs Management
- **Jobs Board**: Paginated list with search, filtering, and sorting
- **Drag & Drop Reordering**: Optimistic updates with rollback on failure
- **Create/Edit Jobs**: Modal-based job creation with validation
- **Deep Linking**: Direct access to jobs via `/jobs/:jobId`
- **Archive/Unarchive**: Toggle job status with one click

### 👥 Candidates Management
- **Virtualized List**: Efficient rendering of 1000+ candidates
- **Advanced Search**: Search by name, email, or stage
- **Candidate Profiles**: Detailed view with timeline and stage management
- **Kanban Board**: Drag-and-drop stage transitions
- **Timeline Tracking**: Complete history of candidate progression

### 📝 Assessments Builder
- **Visual Builder**: Drag-and-drop assessment creation
- **Live Preview**: Real-time preview of assessment forms
- **Multiple Question Types**: 
  - Single choice
  - Multiple choice
  - Short text
  - Long text
  - Numeric (with range validation)
  - File upload
- **Conditional Logic**: Show/hide questions based on previous answers
- **Validation Rules**: Required fields, length limits, numeric ranges

## Technology Stack

- **Frontend**: React 18, React Router, React Hook Form
- **State Management**: Custom hooks with React Query patterns
- **Database**: Dexie (IndexedDB wrapper) for local persistence
- **Mock API**: MSW (Mock Service Worker) with artificial latency
- **UI Components**: Custom components with modern CSS
- **Drag & Drop**: React Beautiful DnD
- **Virtualization**: React Window for performance
- **Data Generation**: Faker.js for realistic seed data

## Getting Started

### Prerequisites
- Node.js 16+ 
- npm or yarn

### Installation

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Start the development server**:
   ```bash
   npm start
   ```

3. **Open your browser**:
   Navigate to `http://localhost:3000`

### First Run
On first launch, the application will:
- Start the MSW mock API service
- Seed the database with 25 jobs, 1000 candidates, and 3 assessments
- Set up IndexedDB for local persistence

## API Endpoints

The application uses MSW to simulate a REST API with the following endpoints:

### Jobs
- `GET /api/jobs` - List jobs with pagination and filtering
- `POST /api/jobs` - Create new job
- `PATCH /api/jobs/:id` - Update job
- `PATCH /api/jobs/:id/reorder` - Reorder jobs

### Candidates
- `GET /api/candidates` - List candidates with search and filtering
- `POST /api/candidates` - Create new candidate
- `PATCH /api/candidates/:id` - Update candidate
- `GET /api/candidates/:id/timeline` - Get candidate timeline

### Assessments
- `GET /api/assessments/:jobId` - Get assessment for job
- `PUT /api/assessments/:jobId` - Save assessment
- `POST /api/assessments/:jobId/submit` - Submit assessment response

## Data Persistence

All data is persisted locally using IndexedDB via Dexie:
- **Jobs**: Title, slug, status, tags, order, timestamps
- **Candidates**: Name, email, stage, job association, timestamps
- **Timeline**: Stage changes, notes, timestamps
- **Assessments**: Questions, sections, validation rules
- **Responses**: Candidate answers to assessments

## Key Features Explained

### Drag & Drop Reordering
Jobs can be reordered via drag-and-drop with:
- Optimistic UI updates
- Automatic rollback on API failure
- Visual feedback during drag operations

### Virtualized Lists
Candidate lists use React Window for performance:
- Renders only visible items
- Handles 1000+ candidates smoothly
- Maintains scroll position during updates

### Assessment Builder
Interactive assessment creation with:
- Live preview pane
- Multiple question types
- Conditional logic support
- Real-time validation

### Mock API Features
- **Artificial Latency**: 200-1200ms response times
- **Error Simulation**: 5-10% error rate on write operations
- **Realistic Data**: Generated using Faker.js
- **Persistence**: All changes saved to IndexedDB

## Project Structure

```
src/
├── components/          # React components
│   ├── JobsBoard.js    # Main jobs listing
│   ├── JobDetail.js    # Individual job view
│   ├── CandidatesPage.js # Candidates listing
│   ├── CandidateProfile.js # Candidate details
│   └── AssessmentBuilder.js # Assessment creation
├── hooks/              # Custom React hooks
│   ├── useJobs.js      # Jobs data management
│   ├── useCandidates.js # Candidates data management
│   └── useAssessment.js # Assessment data management
├── database/           # Database schema
│   └── schema.js       # Dexie configuration
├── mocks/              # Mock API
│   ├── handlers.js     # API route handlers
│   └── browser.js      # MSW browser setup
└── utils/              # Utilities
    └── seedData.js     # Data generation
```

## Development Notes

### Performance Optimizations
- Virtualized lists for large datasets
- Debounced search inputs
- Optimistic UI updates
- Efficient re-rendering with React.memo

### Error Handling
- Graceful API error handling
- User-friendly error messages
- Automatic retry mechanisms
- Rollback on failed operations

### Responsive Design
- Mobile-first approach
- Flexible grid layouts
- Touch-friendly interactions
- Accessible navigation

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## License

This project is for demonstration purposes. All rights reserved.
