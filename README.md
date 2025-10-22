# Project Gutenberg Book Search Engine - Web UI

A modern, responsive web interface for searching books from Project Gutenberg. Built with React and styled to resemble Google's search interface.

## 🎯 Features

- **Full-text search** across Project Gutenberg's entire collection
- **Advanced filtering** by:
  - Author name (supports partial matching)
  - Language (185+ languages supported via ISO 639-1 codes)
  - Publication year
- **Multi-word search support** - finds books containing all search terms
- **Direct links to Project Gutenberg** - click any result to read the book
- **Responsive design** - works seamlessly on desktop and mobile devices
- **Real-time search results** with result count and filtering information
- **Persistent filters** - filters are preserved when navigating back to search

## 🛠️ Tech Stack

- **Frontend**: React 19 with React Router v6
- **Styling**: CSS with responsive design and CSS variables
- **State Management**: React Hooks (useState, useEffect)
- **Dependencies**:
  - `react-router-dom` - Client-side routing
  - `countries-list` - Language data with ISO 639-1 codes
- **Backend**: Java with Javalin (separate microservice)

## 📦 Installation

### Prerequisites
- Node.js (v18 or higher)
- npm or yarn
- Backend service running on `http://localhost:7003`

### Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd <project-directory>
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## 🚀 Usage

### Basic Search
1. Navigate to the home page
2. Enter your search query in the search box (e.g., "Alice in Wonderland")
3. Press Enter or click the Search button
4. Results will appear with links to Project Gutenberg

### Advanced Search with Filters

#### On the Home Page
1. Enter your search term
2. (Optional) Add filters before searching:
   - **Author**: Enter an author name (supports partial matching)
   - **Language**: Select from 185+ languages
   - **Year**: Select a publication year
3. Click Search

#### On the Search Results Page
1. Modify the filter fields
2. Click "Apply Filters" to update results
3. Click "Clear Filters" to remove all filters

### URL Parameters
You can also use URL parameters for direct searches:
```
/search?q=the&author=lincoln&language=en&year=2025
```

**Query Parameters:**
- `q` (required): Search term(s)
- `author` (optional): Author name to filter by
- `language` (optional): ISO 639-1 language code
- `year` (optional): Publication year (YYYY format)

## 📝 Component Documentation

### HomePage.jsx
The landing page where users can enter search terms and apply filters before searching.

**Key Features:**
- Search input with clear button
- Author text input
- Language dropdown (185+ languages)
- Year dropdown (150 years back from current year)
- Clear filters button
- Search button

### SearchPage.jsx
Displays search results with filtering capabilities.

**Key Features:**
- Persistent URL parameters
- Filter bar with real-time modifications
- Result count and active filters display
- Direct links to Project Gutenberg
- No results page with suggestions
- Loading state with spinner

## 🔗 Backend API

This frontend connects to a Java-based search API running on port 7003.

### API Endpoint
```
GET http://localhost:7003/search
```

### Request Parameters
```
q=search_term&author=author_name&language=lang_code&year=YYYY
```

### Response Format
```json
{
  "query": "the",
  "count": 94,
  "filters": {
    "author": "lincoln"
  },
  "results": [
    {
      "book_id": 4,
      "title": "Lincoln's Gettysburg Address",
      "author": "Abraham Lincoln",
      "language": "English",
      "year": "September 6, 2025"
    }
  ]
}
```

For backend setup and documentation, see the [backend repository](https://github.com/lennart-group/stage-2).

### Responsive Breakpoints
- Mobile: < 768px (single column layout)
- Desktop: >= 768px (multi-column layout)

## 🔍 Search Behavior

### Multi-Word Searches
When you search for multiple words (e.g., "alice wonderland"):
- The search finds books containing **all** terms (AND logic)
- Results are ranked by relevance
- Spaces are automatically URL-encoded as `%20`

### Author Filter
- Supports partial matching (case-insensitive)
- Example: "lincoln" matches "Abraham Lincoln"
- Can combine with other filters

### Language Filter
- Uses ISO 639-1 language codes
- Over 185 languages supported
- Case-insensitive matching

### Year Filter
- Matches exact year from publication date
- Filters from 1875 to current year
- Optional filter (leave blank for any year)

## 🤝 Contributing

This is an academic project for ULPGC's Big Data class. For contributions or issues, please contact the project maintainers.

### Project Guidelines
- Follow React best practices
- Keep components small and reusable
- Use descriptive commit messages
- Test on multiple devices

## 📚 Related Resources

- [React Documentation](https://react.dev)
- [React Router Documentation](https://reactrouter.com)
- [Project Gutenberg](https://www.gutenberg.org)
- [ISO 639-1 Language Codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)

## 👨‍💻 Authors

**Project Contributors:**
- @nosekdan - Frontend development

## 📋 License

This project is part of the ULPGC Big Data class curriculum.

## 🎓 Academic Information

**Course**: Big Data - ULPGC
**Project**: Search Engine for Project Gutenberg
**Date**: October 2025

### Project Components
1. **Frontend** (this repository) - React web UI
2. **Backend** - Java search service with MongoDB
3. **Data Pipeline** - Text indexing and ingestion

