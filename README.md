# Crime Pattern Detection System

A comprehensive web-based crime analysis platform built as part of a 2nd-year Computer Science Engineering internship project. This system uses fundamental Data Structures and Algorithms (DSA) concepts to analyze crime patterns from CSV datasets.

## 🚀 Live Demo

**Deployed Application:** [https://serene-faun-924075.netlify.app](https://serene-faun-924075.netlify.app)

## 📋 Table of Contents

- [Features](#features)
- [Technology Stack](#technology-stack)
- [DSA Concepts Used](#dsa-concepts-used)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### 🔍 Core Analysis Features
- **Crime Type Analysis**: Frequency counting using hash maps
- **Hotspot Detection**: Geographic crime distribution analysis
- **Time Pattern Recognition**: Temporal crime clustering
- **Advanced Search**: Multi-criteria crime record filtering
- **Report Generation**: Comprehensive crime analysis reports

### 📊 Visualization Dashboard
- Interactive bar charts for crime type distribution
- Pie charts for location-based analysis
- Line charts for time pattern visualization
- Real-time data filtering and sorting

### 🔧 Data Management
- CSV file upload and processing
- Data validation and quality assessment
- Export functionality for reports
- Real-time data statistics

## 🛠 Technology Stack

### Frontend
- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **Lucide React** for icons
- **React Router** for navigation
- **Vite** for build tooling

### Backend Logic
- **Python** for data processing
- **Pandas** for CSV handling
- **Matplotlib/Seaborn** for chart generation

### Deployment
- **Netlify** for hosting
- **GitHub** for version control

## 🧮 DSA Concepts Used

### 1. Hash Maps (O(1) Operations)
```typescript
// Crime type frequency counting
const crimeTypeHash = new Map<string, number>();
data.forEach(record => {
  crimeTypeHash.set(record.type, (crimeTypeHash.get(record.type) || 0) + 1);
});
```

### 2. Linear Search (O(n) Complexity)
```typescript
// Multi-criteria search implementation
search(filters: SearchFilters): CrimeRecord[] {
  return this.data.filter(record => {
    // Apply multiple search criteria
    return this.matchesAllFilters(record, filters);
  });
}
```

### 3. Sorting Algorithms (O(n log n))
```typescript
// Sort crime types by frequency
const sortedCrimes = Array.from(crimeTypeHash.entries())
  .sort((a, b) => b[1] - a[1]);
```

### 4. Sliding Window Algorithm
```python
# Detect crime clusters using sliding window
def detect_clusters_sliding_window(self, window_size: int = 7):
    for i in range(len(sorted_dates) - window_size + 1):
        window_dates = sorted_dates[i:i + window_size]
        total_crimes = sum(date_counts[date] for date in window_dates)
        # Analyze cluster patterns
```

## 🚀 Installation

### Prerequisites
- Node.js (v16 or higher)
- Python 3.8+
- Git

### Clone Repository
```bash
git clone https://github.com/yourusername/crime-pattern-detection.git
cd crime-pattern-detection
```

### Frontend Setup
```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

### Python Backend Setup
```bash
# Install Python dependencies
pip install pandas matplotlib seaborn

# Run analysis script
python main.py
```

## 📖 Usage

### 1. Data Upload
- Navigate to **Data Management** page
- Upload CSV file with required columns: `id`, `date`, `time`, `type`, `location`
- System validates data quality automatically

### 2. Analysis Dashboard
- View comprehensive crime statistics on the **Dashboard**
- Explore different visualization types
- Filter data by time periods and crime types

### 3. Search Functionality
- Use **Search** page for detailed record filtering
- Apply multiple search criteria simultaneously
- Export search results

### 4. Report Generation
- Generate various report types from **Reports** page
- Download reports in text format
- Schedule automated report generation

## 📁 Project Structure

```
crime-pattern-detection/
├── src/
│   ├── components/          # Reusable UI components
│   │   ├── charts/         # Chart components
│   │   ├── Layout.tsx      # Main layout wrapper
│   │   └── StatCard.tsx    # Statistics display card
│   ├── pages/              # Application pages
│   │   ├── Dashboard.tsx   # Main dashboard
│   │   ├── CrimeTypes.tsx  # Crime type analysis
│   │   ├── Hotspots.tsx    # Location analysis
│   │   ├── TimePatterns.tsx # Temporal analysis
│   │   ├── Clusters.tsx    # Cluster detection
│   │   ├── Search.tsx      # Search functionality
│   │   ├── Reports.tsx     # Report generation
│   │   └── DataManagement.tsx # Data handling
│   ├── data/               # Data management
│   │   └── crimeData.ts    # Sample crime dataset
│   ├── utils/              # Utility functions
│   │   ├── searchUtils.ts  # Search algorithms
│   │   └── reportGenerator.ts # Report generation
│   └── App.tsx             # Main application component
├── public/                 # Static assets
├── python/                 # Python analysis scripts
│   ├── main.py            # Main analysis script
│   ├── data_loader.py     # CSV data loading
│   ├── pattern_analyzer.py # DSA implementations
│   └── chart_generator.py  # Visualization generation
└── crime_data.csv         # Sample dataset
```

## 🔧 API Documentation

### Search Engine
```typescript
interface SearchFilters {
  query: string;        // Text search across multiple fields
  crimeType: string;    // Filter by specific crime type
  location: string;     // Location-based filtering
  dateFrom: string;     // Start date filter
  dateTo: string;       // End date filter
}

class CrimeSearchEngine {
  search(filters: SearchFilters): CrimeRecord[]
  getSuggestions(query: string, field: 'type' | 'location'): string[]
  getUniqueValues(field: keyof CrimeRecord): string[]
}
```

### Report Generator
```typescript
interface ReportData {
  title: string;
  generatedAt: string;
  period: string;
  summary: ReportSummary;
  analysis: any;
}

class ReportGenerator {
  generateSummaryReport(period: string): ReportData
  generateTrendReport(period: string): ReportData
  generateHotspotReport(period: string): ReportData
  downloadReport(reportData: ReportData): void
}
```

## 🎯 Key Algorithms

### 1. Crime Frequency Analysis
- **Time Complexity**: O(n) for counting, O(n log n) for sorting
- **Space Complexity**: O(k) where k is unique crime types
- **Implementation**: Hash map for frequency counting

### 2. Hotspot Detection
- **Time Complexity**: O(n) for location counting
- **Space Complexity**: O(m) where m is unique locations
- **Implementation**: Geographic frequency analysis

### 3. Time Pattern Recognition
- **Time Complexity**: O(n) for hour extraction and counting
- **Space Complexity**: O(24) for hourly buckets
- **Implementation**: Time-based clustering

### 4. Cluster Detection
- **Time Complexity**: O(n * w) where w is window size
- **Space Complexity**: O(n) for date storage
- **Implementation**: Sliding window algorithm

## 📊 Sample Data Format

```csv
id,date,time,type,location
1,2024-01-15,14:30,Theft,Downtown
2,2024-01-15,22:15,Burglary,Residential Area
3,2024-01-16,08:45,Vandalism,Park District
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow TypeScript best practices
- Maintain consistent code formatting
- Add comments for complex algorithms
- Update documentation for new features

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🎓 Academic Context

This project was developed as part of a 2nd-year Computer Science Engineering internship, focusing on:

- **Data Structures**: Hash maps, arrays, sets
- **Algorithms**: Searching, sorting, sliding window
- **Software Engineering**: Modular design, clean code principles
- **Web Development**: Modern React patterns, responsive design
- **Data Analysis**: Statistical analysis, pattern recognition

## 📞 Contact

**Project Maintainer**: [Your Name]
- Email: your.email@example.com
- LinkedIn: [Your LinkedIn Profile]
- GitHub: [@yourusername](https://github.com/yourusername)

## 🙏 Acknowledgments

- Thanks to the Computer Science Engineering department for project guidance
- Inspiration from real-world crime analysis systems
- Open source community for tools and libraries used

---

**⭐ Star this repository if you found it helpful!**