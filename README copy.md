# Flexible Data Type System

A comprehensive C++ data management system that can dynamically adapt to
different CSV structures and provide statistical analysis capabilities.

## Features

### 🔧 Core Capabilities

- **Dynamic Structure Adaptation**: Automatically detects and adapts to any CSV
  structure
- **Multiple Data Types Support**:
  - Integers (`int`)
  - Floating-point numbers (`float`)
  - Strings (`std::string`)
  - Dates (`std::chrono::year_month_day`)
  - Categories/Enums (`Category`)
- **Automatic Type Inference**: Intelligently determines data types from CSV
  content
- **Dynamic Column Management**: Add or modify columns at runtime
- **Type-Safe Operations**: Ensures data integrity with proper type checking

### 📊 Statistical Analysis

- **Descriptive Statistics**: Mean, median, standard deviation, min/max,
  quartiles
- **Frequency Analysis**: Count and percentage distribution for categorical data
- **Data Filtering**: Filter data based on various criteria
- **Search Functionality**: Find specific values across columns
- **Data Preview**: Display first N rows for quick inspection

## Project Structure

```
Situacion Problema Solucion/
├── Dato.h          # Core data type implementation
├── Analisis.h      # CSV analyzer and statistical functions
├── main.cpp        # Comprehensive demonstration
├── test.cpp        # Simple functionality test
└── README.md       # This documentation
```

## Quick Start

### 1. Automatic CSV Loading

```cpp
#include "Analisis.h"

// Create analyzer and load CSV
CSVAnalyzer analyzer;
analyzer.loadCSV("your_data.csv");

// Get basic information
analyzer.printBasicStatistics();
analyzer.printHead(5);  // Show first 5 rows

// Statistical analysis
analyzer.printNumericStatistics();
analyzer.printCategoricalStatistics();
```

### 2. Manual Data Creation

```cpp
#include "Dato.h"

// Define structure
std::vector<std::string> columns = {"ID", "Name", "Score", "Grade"};
std::vector<DataType> types = {
    DataType::INTEGER,
    DataType::STRING,
    DataType::FLOAT,
    DataType::CATEGORY
};

// Create data object
Dato student(columns, types);

// Set values
student.setValue("ID", 12345);
student.setValue("Name", std::string("John Doe"));
student.setValue("Score", 95.5f);
student.setValue("Grade", Category::GRADE_A);

// Display data
student.display();
```

### 3. Dynamic Column Addition

```cpp
// Add new column at runtime
student.addColumn("Email", DataType::STRING);
student.setValue("Email", std::string("john.doe@email.com"));

// Set values from strings (automatic conversion)
student.setValueFromString("Score", "87.3");
student.setValueFromString("ID", "54321");
```

### 4. Data Analysis Operations

```cpp
// Search for specific values
auto results = analyzer.searchValue("Department", "Engineering");
std::cout << "Found " << results.size() << " matches" << std::endl;

// Filter data
auto filtered = analyzer.filterData("Age", ">", "30");
auto highScores = analyzer.filterData("Score", ">=", "90");

// Access specific values
for (const auto& row : filtered) {
    std::string name = row.getValueAsString(1);  // By index
    double score = row.getNumericValue(2);       // Numeric conversion
}
```

## Supported Data Types

| Type     | C++ Type                      | Example Values       | Auto-Detection |
| -------- | ----------------------------- | -------------------- | -------------- |
| INTEGER  | `int`                         | 42, -17, 0           | ✅             |
| FLOAT    | `float`                       | 3.14, -2.5, 1.0      | ✅             |
| STRING   | `std::string`                 | "Hello", "Text data" | ✅             |
| DATE     | `std::chrono::year_month_day` | "2023-12-01"         | ✅             |
| CATEGORY | `Category`                    | "A", "B", "C"        | ✅             |

## Auto-Detection Rules

The system automatically infers data types using these rules:

1. **INTEGER**: Contains only digits (with optional +/- sign)
2. **FLOAT**: Contains decimal point and valid floating-point format
3. **DATE**: Matches YYYY-MM-DD pattern
4. **CATEGORY**: Limited unique values (≤10 or ≤10% of total rows)
5. **STRING**: Default fallback for all other data

## Statistical Features

### Numeric Columns

- Count of non-null values
- Mean (average)
- Median (50th percentile)
- Standard deviation
- Minimum and maximum values
- First quartile (Q1) and third quartile (Q3)

### Categorical Columns

- Frequency count for each unique value
- Percentage distribution
- Sorted by frequency (most common first)

## Compilation & Execution

### Requirements

- C++20 compatible compiler
- Standard libraries: `<variant>`, `<chrono>`, `<regex>`

### Compilation

```bash
# Compile main demonstration
g++ -std=c++20 -o main.exe main.cpp

# Compile simple test
g++ -std=c++20 -o test.exe test.cpp

# With optimization
g++ -std=c++20 -O2 -o main.exe main.cpp
```

### Execution

```bash
# Run main demo (creates sample CSV and demonstrates features)
./main.exe

# Run simple test
./test.exe
```

## Example CSV Formats

The system can handle various CSV formats:

### Employee Data

```csv
ID,Name,Age,Salary,Department,JoinDate
1,John Doe,30,50000.50,Engineering,2023-01-15
2,Jane Smith,25,45000.00,Marketing,2022-06-10
```

### Student Grades

```csv
StudentID,Name,Math,Science,English,Grade
101,Alice,95.5,88.0,92.3,A
102,Bob,78.2,85.5,79.8,B
```

### Sales Data

```csv
Date,Product,Price,Quantity,Category
2023-01-01,Laptop,999.99,5,Electronics
2023-01-02,Book,15.50,20,Education
```

## Advanced Features

### Custom Categories

Extend the `Category` enum for domain-specific categories:

```cpp
enum class Category {
    // Existing grades
    GRADE_A, GRADE_B, GRADE_C, GRADE_D, GRADE_F,

    // Custom categories
    HIGH_PRIORITY, MEDIUM_PRIORITY, LOW_PRIORITY,
    APPROVED, PENDING, REJECTED,

    CUSTOM  // For unmatched values
};
```

### Error Handling

The system provides comprehensive error handling:

- Invalid file paths
- Malformed CSV data
- Type conversion errors
- Column index out of range
- Missing column names

### Performance Considerations

- Efficient memory usage with `std::variant`
- Lazy evaluation for type inference
- Optimized string operations
- Minimal overhead for type checking

## Use Cases

1. **Data Analysis**: Process CSV files from various sources
2. **Educational Software**: Manage student grades and information
3. **Business Intelligence**: Analyze sales, employee, or financial data
4. **Research**: Handle experimental data with mixed types
5. **Data Migration**: Convert between different data formats
6. **Reporting**: Generate statistics from structured data

## Extensibility

The system is designed for easy extension:

1. **New Data Types**: Add types to the `DataValue` variant
2. **Custom Statistics**: Extend the `CSVAnalyzer` class
3. **Export Formats**: Add methods to export data in different formats
4. **Validation Rules**: Implement custom data validation
5. **Performance Optimizations**: Add caching or indexing mechanisms

## License

This project is part of a university assignment for TC1033 - Programming Course
at Tecnológico de Monterrey.

---

_Created as part of the Situación Problema Solución assignment, demonstrating
advanced C++ programming concepts including templates, variants, and statistical
analysis._
