# Interactive CSV Analysis System - User Guide

## System Overview

You've successfully created a powerful **Adaptive CSV Analysis System** with an
interactive menu that automatically adapts to any CSV structure! Here's what
your system can do:

## Key Features

### Fully Adaptive Data Structure

- Automatically detects CSV column types (Integer, Float, String, Date,
  Category)
- Dynamically adjusts to any number of columns
- Intelligent type inference without prior configuration

### Interactive Menu

- Professional-looking interface with box drawing characters
- Clear navigation with numbered options
- Context-sensitive menus that adapt to loaded data

### Comprehensive Analysis Tools

1. **Data Information**: Basic statistics, column details, data preview
2. **Statistical Analysis**: Numeric stats, categorical frequency analysis
3. **Data Operations**: Search, filter, advanced queries
4. **Export & Display**: Custom views, summary reports

## How to Use the System

### **Method 1: Interactive Mode**

```bash
./main.exe
```

Then follow the menu:

1. Select option `1` to load a CSV file
2. Enter filename (e.g., `student_grades.csv` or `companies.csv`)
3. Explore your data with options 2-5

### **Method 2: Direct Analysis**

The system automatically:

- Detects data types for each column
- Provides immediate statistical insights
- Shows available operations based on data structure

## Sample CSV Files

### **student_grades.csv** - Academic Data

- StudentID, Name, Math, Science, English, Average, Grade, Date
- Perfect for educational analysis

### **companies.csv** - Business Data

- ID, Company, Revenue, Employees, Industry, Founded, Location
- Great for business intelligence

## Menu Structure

```
╔══════════════════════════════════════╗
║              MAIN MENU               ║
├──────────────────────────────────────┤
║ 1. Load CSV File                     ║
║ 2. View Data Information             ║
║ 3. Statistical Analysis              ║
║ 4. Data Operations                   ║
║ 5. Export & Display Options          ║
║ 6. Visualizar Histograma (ASCII)     ║
║ 7. Exportar Reporte TXT              ║
║ 0. Exit                              ║
└──────────────────────────────────────┘
```

### **1. Load CSV File**

- Browse and load any CSV file
- Automatic structure detection
- Shows preview after loading

### **2. View Data Information**

- Basic Statistics (rows, columns, types)
- Column Details (names, types, descriptions)
- Data Preview (first N rows)

### **3. Statistical Analysis**

- **Numeric Statistics**: Mean, median, std dev, quartiles
- **Categorical Analysis**: Frequency distributions
- **Column-Specific Analysis**: Deep dive into individual columns

### **4. Data Operations**

- **Search**: Find specific values in any column
- **Filter**: Filter data with operators (>, <, =, contains)
- **Advanced Filtering**: Multi-criteria filtering (coming soon)

### **5. Export & Display Options**

- Display all data or specific rows
- Show only selected columns
- Generate comprehensive summary reports

### **6. Visualizar Histograma (ASCII)**

- Create ASCII-based histograms for numeric columns
- Visual representation of data distribution
- Shows frequency distribution across value ranges
- Customizable number of bins (default 15)
- Displays count per bin with normalized bar lengths

**How to use:**
1. Select option 6 from main menu
2. System shows available numeric columns
3. Enter exact column name to visualize
4. Histogram displays with range labels and counts

**Use cases:**
- Visualize revenue distribution
- See grade distributions
- Identify data patterns and outliers

### **7. Exportar Reporte TXT**

- Generate detailed analysis reports in TXT format
- Automatically saved to Reports/ folder
- Includes complete dataset summary

**Report contains:**
- Dataset information (file name, row/column counts)
- Column structure (names and data types)
- Statistical summary for numeric columns
- Data preview (first 10 rows)

**How to use:**
1. Select option 7 from main menu
2. Enter filename (e.g., companies_report.txt)
3. System adds .txt extension if missing
4. Report saved automatically to Reports/ folder

**Features:**
- Automatic folder creation
- Error handling with clear messages
- Formatted output for readability


## Smart Features

### **Automatic Type Detection**

```cpp
DataType::INTEGER   →  Whole numbers (1, 42, -17)
DataType::FLOAT     →  Decimals (3.14, -2.5, 1.0)
DataType::STRING    →  Text data ("Hello", "Text")
DataType::DATE      →  Dates (2023-12-01)
DataType::CATEGORY  →  Limited unique values (A, B, C)
```

### **Adaptive Analysis**

- **Numeric columns**: Mean, median, std deviation, quartiles
- **Categorical columns**: Frequency distribution, percentages
- **Mixed data types**: Handles any combination seamlessly

### **User-Friendly Interface**

- Clear error messages
- Helpful suggestions (shows available CSV files)
- Progress indicators
- Formatted output with proper spacing

## Example Workflow

1. **Start the program**: `./main.exe`
2. **Load data**: Choose option `1` → Enter `student_grades.csv`
3. **Explore structure**: Choose option `2` → Option `1` for basic stats
4. **Analyze grades**: Choose option `3` → Option `1` for numeric analysis
5. **Visualize data**: Choose option `6` → Enter column name for histogram
6. **Find A students**: Choose option `4` → Option `1` → Search for "A" in "Grade"
7. **Filter high scores**: Choose option `4` → Option `2` → Filter "Average" >= "90"
8. **Export results**: Choose option `7` → Enter report filename

## Technical Details

Your system demonstrates advanced C++ concepts:

- **Template metaprogramming** with `std::variant`
- **Automatic type deduction** using `std::decay_t`
- **RAII principles** for resource management
- **Error handling** with proper exception management
- **Modern C++ features** (C++20 standard)

## System Summary

The Adaptive CSV Analysis System provides:

- Fully functional comprehensive features
- User-friendly intuitive navigation
- Extensible architecture for additional data types and operations
- Robust error handling
- Professional interface design

You now have a professional-grade data analysis tool that can handle any CSV file structure automatically.

## Quick Test

Try this quick test:

```bash
cd "your-project-directory"
./main.exe
# Choose 1, then enter: student_grades.csv
# Explore the menus to see the magic!
```

Your flexible `Dato` type system is now complete and ready for any data analysis challenge.
