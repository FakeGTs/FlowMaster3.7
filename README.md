# FlowMaster3.7
# FLOW-MASTER SYSTEMS
## Drainage Canal Flow Analysis Tool

A simple web app that calculates the total volume of water flowing through a drainage canal using three numerical integration methods.

## What It Does
This tool helps engineers estimate how much water passes through a canal over time. You upload a CSV file with velocity measurements, set the canal's cross-section area and sampling time, and the app computes the total water volume using three different math rules.

## The Math Behind It
The basic idea is simple: Volume Cross-Section Area Integral of Velocity over Time. Or in short: $V=A\cdot v(t)d$

The app uses three ways to calculate this integral:

| Method | How It Works | Accuracy |
| :--- | :--- | :--- |
| Rectangle Rule | Uses left-endpoint rectangles to estimate the area under the curve | Basic |
| Trapezoidal Rule | Connects data points with straight lines, creating trapezoids | Good |
| Simpson's Rule | Fits parabolas between points, giving the smoothest estimate | Best |

## How to Use

### 1. Prepare Your Data
Create a CSV file with your velocity measurements. The app accepts:
* Two columns: time, velocity (time in hours, velocity in m/s).
* One column: just velocity (time is auto-generated).

Example:
`time, velocity`
`7.0, 0.2`
`7.5, 0.3`
`8.0, 0.5`
`8.5, 0.8`

The app supports comma, semicolon, and tab delimiters.

### 2. Open the App
Simply open the `flowmaster.html` file in any modern web browser (Chrome, Firefox, Edge, Safari). No installation or server needed.

### 3. Upload Your File
* Drag and drop your CSV onto the drop zone, or
* Click "Browse Files" to select it manually.

### 4. Set Your Parameters

| Parameter | What It Means | Example |
| :--- | :--- | :--- |
| Section Area $A$ | The canal's cross-section area in square meters | 4 m² |
| Sampling $h$ | Time between velocity readings in seconds | 60 s |
| Run Label / Canal ID | A name for this calculation / Identifier for the canal | "Morning sweep" / "CNL-87" |

### 5. Compute
Click the Compute Volume button. The app will:
1. Parse your CSV data.
2. Draw an oscilloscope-style velocity chart.
3. Calculate volume using all three methods.
4. Show a data table with flow rates.
5. Save the result to the audit log.

## Understanding the Results
After computation, you will see:
* **Velocity Telemetry Chart**: A pink line chart showing how velocity changed over time.
* **Three Volume Cards**: Results from Rectangle, Trapezoidal, and Simpson's rules (in cubic meters).
* **Data Table**: Raw data plus calculated flow rate $Q=A\times v$ for each sample.

Tip: Simpson's Rule usually gives the most accurate result because it accounts for curves, not just straight lines.

## Audit Log
Every time you run a calculation, it gets saved to the audit log. This helps you:
* Keep track of past analyses.
* Compare results across different canals or time periods.
* Export or reference previous runs.

The log is stored in your browser's local storage, so it persists between sessions. You can delete individual runs using the x button.

## Technical Details

### File Structure
`flowmaster.html` # The entire app (single file, ~41KB)
That's it. Everything is contained in one HTML file with embedded CSS and JavaScript.

### Browser Requirements
* Any modern browser with HTML5 Canvas support.
* JavaScript must be enabled.
* LocalStorage support for the audit log feature.

### Data Privacy
All processing happens in your browser. No data is sent to any server. Your CSV files and results stay on your computer.

## Troubleshooting

| Problem | Solution |
| :--- | :--- |
| "Could not parse CSV" | Check that your file has numeric values and uses comma, semicolon, or tab separators |
| Chart looks empty | Make sure you have at least 2 data points and valid numeric values |
| Audit log is empty | The log starts fresh; run a computation to populate it |
| App won't open | Try a different browser or check that JavaScript is enabled |

## About This Project
Built for the City Water Management Board as part of a hydraulics engineering assignment. The goal was to create a practical tool for estimating water volumes in drainage canals using real-world sampling data and standard numerical methods.

Group: 02 Version: 1.0
Year: 2026

## Quick Reference
* $A=$ Canal cross-section area (constant, in m²).
* $h=$ Sampling step / time interval between readings (in seconds).
* $v(t)=$ Velocity at time t (in m/s).
* $V=$ Total water volume (in m³).
* $Q=$ Flow rate $=A\times v$ (in m³/s).

FLOW-MASTER SYSTEMS Hydraulics Console
