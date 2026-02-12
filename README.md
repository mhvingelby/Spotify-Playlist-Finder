# Project Overview

A full-stack web application that enables users to search for Spotify playlists through a web interface. The application features a Node.js/Express frontend server that proxies requests to a Python/Flask backend, which queries the Spotify API and filters results by follower count and contact information extracted from playlist descriptions.

## Architecture Overview

The application follows a **Client-Server Architecture with API Proxy Pattern** and microservices-style separation between the Node.js frontend and Python backend.

### Application Flow

1. User submits search query via web interface
2. Node.js Express server receives request
3. Server proxies request to Python Flask backend
4. Python backend queries Spotify API
5. Backend filters playlists by follower count
6. Backend extracts contact information from descriptions
7. Filtered results returned to frontend
8. EJS template renders playlist results to user

### Entry Points

- **server.js** - Node.js Express frontend server
- **request_handler.py** - Python Flask backend API

## Project Structure

The codebase consists of 5 files with the following breakdown:

- **Python files (.py)**: 2 files
  - `request_handler.py` - Flask backend API structure
  - `spotify_api_handler.py` - Spotify API integration and filtering logic
- **JavaScript files (.js)**: 1 file
  - `server.js` - Express frontend server and routing logic
- **EJS templates (.ejs)**: 2 files
  - `home.ejs` - Main search interface template
  - `header.ejs` - Header template component

## Key Technologies

### Frontend
- **Node.js** with Express framework
- **EJS** (Embedded JavaScript templates) for server-side rendering

### Backend
- **Python** with Flask framework
- **Spotify API** integration for playlist search and data retrieval

## Getting Started

### Prerequisites

- Node.js and npm
- Python 3.x and pip
- Spotify API credentials

### Installation

1. Clone the repository

2. Install Node.js dependencies:
   ```bash
   npm install
   ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements
   ```

4. TODO: Add Spotify API credential configuration instructions

### Running the Application

1. Start the Python backend server (runs on port 9000):
   ```bash
   python request_handler.py
   ```

2. Start the Node.js frontend server:
   ```bash
   node server.js
   ```

3. Access the web interface through your browser

4. Enter a search query to find Spotify playlists

## Onboarding Guide

For developers new to this codebase:

1. Clone the repository and install dependencies for both Node.js (npm install) and Python (pip install requirements)
2. Review `server.js` to understand the Express frontend server and routing logic
3. Examine `request_handler.py` to see the Flask backend API structure
4. Study `spotify_api_handler.py` to understand Spotify API integration and filtering logic
5. Start the Python backend on port 9000 (python request_handler.py)
6. Start the Node.js frontend server (node server.js)
7. Access the web interface and test the playlist search functionality
8. Begin modifications in the appropriate layer based on your task (frontend in server.js/EJS files, backend in Python files)

## Known Issues and Warnings

### Critical Severity

- **No authentication or authorization mechanisms** for search endpoints, allowing unrestricted access to Spotify API queries
- **No input validation or sanitization** on search terms across all layers, creating potential injection vulnerabilities
- **Hardcoded backend URL** (http://127.0.0.1:9000) in multiple locations prevents deployment flexibility and environment-specific configuration
- **No error handling** for API failures, network timeouts, or missing data across backend and frontend components
- **POST /search endpoint** redirects before waiting for backend response completion, potentially causing data loss

### High Severity

- Complex email extraction regex is difficult to maintain and may fail silently without proper error handling
- Hardcoded values (port 9000, loop iterations, region 'US') reduce flexibility and testability

### Medium Severity

- Frontend lacks loading indicators, error messages, and accessibility attributes (ARIA labels, alt text)
- Inline JavaScript in home.ejs should be separated into external files for better maintainability
- Unused variables and commented-out imports suggest incomplete refactoring

## Code Quality Metrics

- **Overall Score**: 39/100 - The codebase demonstrates basic functional implementation with clear separation of concerns, but suffers from critical security gaps, missing error handling, and insufficient documentation that significantly impact production readiness.
- **Maintainability**: 56/100 - Code structure is generally clear with organized functions and basic separation of concerns, but hardcoded values, missing error handling, lack of input validation, and inline code reduce overall maintainability.
- **Complexity**: 28/100 - Most components implement straightforward logic with basic API calls and DOM manipulation, though email extraction regex and nested loops add minor complexity.
- **Documentation**: 34/100 - Minimal documentation across all files with few comments or docstrings; function names are generally descriptive but lack parameter/return value documentation and explanation of complex logic.
