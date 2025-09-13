# replit.md

## Overview

InocAgro-2025 is a web-based educational platform for agricultural safety ("Inocuidad Agrícola") designed for the 2025-2026 academic period. The application serves as a lesson planning and activity management system for teachers and students in agricultural education. Teachers can create, edit, and manage lesson plans with detailed timing and evaluation criteria, while students can view plans and submit activities. The platform includes user authentication with role-based access (teachers vs students) and supports PDF generation for lesson plans.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Template Engine**: Jinja2 templates with Flask for server-side rendering
- **UI Framework**: Bootstrap 5.3.7 for responsive design and styling
- **Client-side Features**: JavaScript for dynamic form handling, uppercase text conversion, and real-time date/time display
- **PDF Generation**: html2pdf.js library for client-side PDF creation from lesson plans

### Backend Architecture
- **Web Framework**: Flask with Gevent WSGI server for concurrent request handling
- **Authentication**: Flask-Bcrypt for password hashing with session-based authentication
- **Session Management**: 60-minute timeout with automatic cleanup and activity tracking
- **File Handling**: Secure file uploads with Werkzeug, supporting PDF submissions for student activities
- **PDF Generation**: WeasyPrint for server-side PDF generation of lesson plans

### Data Layer
- **Database**: MySQL with PyMySQL connector
- **ORM**: SQLAlchemy with sessionmaker for database operations
- **SSL Security**: SSL certificate validation for secure database connections
- **Key Tables**: 
  - `mat1` for lesson plan data
  - User tables for authentication (students and teachers)
  - Activity submission tracking

### Security and Session Management
- **Password Security**: Bcrypt hashing for user credentials
- **Session Security**: Secret key-based sessions with configurable timeout
- **Input Validation**: Automatic uppercase conversion for form fields (excluding sensitive fields)
- **File Security**: Secure filename handling for uploads

### Application Features
- **Role-based Access**: Separate interfaces and permissions for teachers (docentes) and students (alumnos)
- **Lesson Planning**: Comprehensive lesson plan creation with timing, evaluation criteria, and content management
- **Activity Management**: Student activity submission system with PDF upload support
- **Time Tracking**: Detailed duration tracking for lesson components (apertura, desarrollo, cierre)
- **Evaluation System**: Percentage-based evaluation weighting for different lesson components

## External Dependencies

### Core Framework Dependencies
- **Flask**: Web application framework
- **SQLAlchemy**: Database ORM and connection management
- **Flask-Bcrypt**: Password hashing and authentication
- **Werkzeug 2.0.3**: HTTP utilities and secure file handling
- **Gunicorn**: WSGI HTTP server for production deployment
- **Gevent**: Asynchronous networking library for concurrent connections

### Database and Storage
- **PyMySQL**: MySQL database connector
- **mysql-connector-python**: Additional MySQL connectivity support
- **Database**: MySQL instance with SSL configuration

### Document and Media Processing
- **WeasyPrint**: Server-side PDF generation from HTML/CSS
- **Cloudinary**: Cloud-based image and media management (configured but commented out)

### Utility Libraries
- **pytz**: Timezone handling for Mexico City timezone
- **tempfile**: Temporary file management for PDF processing

### Frontend Libraries (CDN)
- **Bootstrap 5.3.7**: CSS framework for responsive design
- **html2pdf.js**: Client-side PDF generation
- **Google Fonts**: Lato font family for typography

### Development and Deployment
- **Environment Variables**: Configuration for database connections, Cloudinary credentials, and secret keys
- **SSL Certificates**: CA certificate bundle for secure database connections