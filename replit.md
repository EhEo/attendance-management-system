# Replit Development Guide

## Overview

This is a comprehensive workforce management system designed for manufacturing companies with approximately 1,000 employees. The application manages overtime requests, attendance tracking, approvals workflow, payroll calculations, and employee management with role-based access control.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **State Management**: Zustand for local state, TanStack Query for server state
- **UI Framework**: Radix UI components with Tailwind CSS styling
- **Styling**: Tailwind CSS with shadcn/ui component library
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Authentication**: Replit Auth with OpenID Connect
- **Session Management**: Express sessions with PostgreSQL storage
- **API Pattern**: RESTful API with role-based access control

### Database Architecture
- **Database**: PostgreSQL (configured for Neon serverless)
- **ORM**: Drizzle ORM with TypeScript schema definitions
- **Migration Strategy**: Drizzle Kit for schema management
- **Connection**: Neon serverless with WebSocket support

## Key Components

### Authentication System
- **Provider**: Replit Auth integration with OIDC
- **Session Storage**: PostgreSQL-backed sessions using connect-pg-simple
- **Authorization**: Role-based access control with 6 distinct roles:
  - Department Manager
  - Department Leader  
  - Team Manager
  - HR Staff
  - Production Planning
  - Viewer

### Data Models
- **Users**: Replit Auth integration with role assignments
- **Departments**: Hierarchical organization structure
- **Teams**: Sub-units within departments
- **Employees**: Detailed employee records with shift assignments
- **Overtime Requests**: Multi-employee overtime request system
- **Approvals**: Workflow management for requests
- **Attendance**: Time tracking with anomaly detection
- **Notifications**: System-wide messaging

### UI Components
- **Layout**: Responsive sidebar navigation with header breadcrumbs
- **Forms**: React Hook Form with Zod validation
- **Data Display**: Cards, tables, and statistical dashboards
- **Interactive Elements**: Dialogs, dropdowns, and selection interfaces

## Data Flow

### Request Flow
1. User authentication via Replit Auth
2. Role-based route protection and UI rendering
3. TanStack Query manages API requests with caching
4. Express routes handle business logic and database operations
5. Drizzle ORM executes type-safe database queries

### State Management
- **Server State**: TanStack Query with automatic caching and refetching
- **Client State**: Zustand stores for component-level state (e.g., selected employees)
- **Form State**: React Hook Form for form validation and submission
- **UI State**: React state for component interactions

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Serverless PostgreSQL driver
- **@tanstack/react-query**: Server state management
- **drizzle-orm**: Type-safe database ORM
- **express**: Web framework
- **react**: UI framework
- **wouter**: Client-side routing

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives
- **tailwindcss**: Utility-first CSS framework
- **lucide-react**: Icon library
- **class-variance-authority**: Component variant management

### Development Dependencies
- **typescript**: Type checking
- **vite**: Build tool and development server
- **tsx**: TypeScript execution for development

## Deployment Strategy

### Development Environment
- **Platform**: Replit with Node.js 20 runtime
- **Database**: PostgreSQL 16 module
- **Development Server**: Vite dev server with Express backend
- **Hot Reload**: Vite HMR for frontend, tsx watch for backend

### Production Build
- **Frontend**: Vite build to static assets
- **Backend**: ESBuild bundle for Node.js execution
- **Database**: Neon serverless PostgreSQL
- **Deployment**: Replit autoscale deployment target

### Environment Configuration
- **DATABASE_URL**: PostgreSQL connection string
- **SESSION_SECRET**: Session encryption key
- **REPL_ID**: Replit environment identifier
- **ISSUER_URL**: OIDC provider endpoint

## User Preferences

Preferred communication style: Simple, everyday language.

## Recent Changes

✓ 데이터베이스 스키마 생성 완료 (모든 테이블 구조 완성)
✓ Replit Auth 인증 시스템 설정 완료
✓ 역할 기반 접근 제어 구현 
✓ 초기 샘플 데이터 추가 (부서, 팀, 직원, 초과근무 요청, 출근 기록)
✓ 사용자를 생산부 부서장으로 설정하여 신청/승인 권한 부여
✓ 한국어 인터페이스 구현

## Changelog

- June 24, 2025: 초기 시스템 구축 완료, 부서장 권한으로 테스트 가능한 상태