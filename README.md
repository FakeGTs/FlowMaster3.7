# FlowMaster3.7
# [cite_start]FLOW-MASTER SYSTEMS [cite: 1]
## [cite_start]Drainage Canal Flow Analysis Tool [cite: 2]

[cite_start]A simple web app that calculates the total volume of water flowing through a drainage canal using three numerical integration methods. [cite: 3]

## [cite_start]What It Does [cite: 4]
[cite_start]This tool helps engineers estimate how much water passes through a canal over time. [cite: 5] [cite_start]You upload a CSV file with velocity measurements, set the canal's cross-section area and sampling time, and the app computes the total water volume using three different math rules. [cite: 6]

## [cite_start]The Math Behind It [cite: 7]
[cite_start]The basic idea is simple: [cite: 8] [cite_start]Volume Cross-Section Area Integral of Velocity over Time. [cite: 9] [cite_start]Or in short: $V=A\cdot v(t)d$ [cite: 10]

[cite_start]The app uses three ways to calculate this integral: [cite: 11]

| Method | How It Works | Accuracy |
| :--- | :--- | :--- |
| [cite_start]Rectangle Rule [cite: 12] | [cite_start]Uses left-endpoint rectangles to estimate the area under the curve [cite: 12] | [cite_start]Basic [cite: 12] |
| [cite_start]Trapezoidal Rule [cite: 12] | [cite_start]Connects data points with straight lines, creating trapezoids [cite: 12] | [cite_start]Good [cite: 12] |
| [cite_start]Simpson's Rule [cite: 12] | [cite_start]Fits parabolas between points, giving the smoothest estimate [cite: 12] | [cite_start]Best [cite: 12] |

## [cite_start]How to Use [cite: 13]

### [cite_start]1. Prepare Your Data [cite: 14]
Create a CSV file with your velocity measurements. [cite_start]The app accepts: [cite: 15]
* [cite_start]Two columns: time, velocity (time in hours, velocity in m/s). [cite: 16]
* [cite_start]One column: just velocity (time is auto-generated). [cite: 16]

[cite_start]Example: [cite: 17]
[cite_start]`time, velocity` [cite: 18]
[cite_start]`7.0, 0.2` [cite: 19]
[cite_start]`7.5, 0.3` [cite: 20]
[cite_start]`8.0, 0.5` [cite: 21]
[cite_start]`8.5, 0.8` [cite: 22]

[cite_start]The app supports comma, semicolon, and tab delimiters. [cite: 24]

### [cite_start]2. Open the App [cite: 25]
Simply open the `flowmaster.html` file in any modern web browser (Chrome, Firefox, Edge, Safari). [cite_start]No installation or server needed. [cite: 26]

### [cite_start]3. Upload Your File [cite: 27]
* [cite_start]Drag and drop your CSV onto the drop zone, or [cite: 28]
* [cite_start]Click "Browse Files" to select it manually. [cite: 29]

### [cite_start]4. Set Your Parameters [cite: 30]

| Parameter | What It Means | Example |
| :--- | :--- | :--- |
| [cite_start]Section Area $A$ [cite: 31] | [cite_start]The canal's cross-section area in square meters [cite: 31] | [cite_start]4 m² [cite: 31] |
| [cite_start]Sampling $h$ [cite: 31] | [cite_start]Time between velocity readings in seconds [cite: 31] | [cite_start]60 s [cite: 31] |
| [cite_start]Run Label / Canal ID [cite: 31] | [cite_start]A name for this calculation / Identifier for the canal [cite: 31] | [cite_start]"Morning sweep" / "CNL-87" [cite: 31] |

### [cite_start]5. Compute [cite: 32]
Click the Compute Volume button. [cite_start]The app will: [cite: 33]
1. [cite_start]Parse your CSV data. [cite: 34]
2. [cite_start]Draw an oscilloscope-style velocity chart. [cite: 35]
3. [cite_start]Calculate volume using all three methods. [cite: 36]
4. [cite_start]Show a data table with flow rates. [cite: 37]
5. [cite_start]Save the result to the audit log. [cite: 38]

## [cite_start]Understanding the Results [cite: 39]
[cite_start]After computation, you will see: [cite: 40]
* [cite_start]**Velocity Telemetry Chart**: A pink line chart showing how velocity changed over time. [cite: 41, 42]
* [cite_start]**Three Volume Cards**: Results from Rectangle, Trapezoidal, and Simpson's rules (in cubic meters). [cite: 41, 42]
* [cite_start]**Data Table**: Raw data plus calculated flow rate $Q=A\times v$ for each sample. [cite: 43]

[cite_start]Tip: Simpson's Rule usually gives the most accurate result because it accounts for curves, not just straight lines. [cite: 44]

## [cite_start]Audit Log [cite: 45]
Every time you run a calculation, it gets saved to the audit log. [cite_start]This helps you: [cite: 46]
* [cite_start]Keep track of past analyses. [cite: 47]
* [cite_start]Compare results across different canals or time periods. [cite: 48]
* [cite_start]Export or reference previous runs. [cite: 50]

[cite_start]The log is stored in your browser's local storage, so it persists between sessions. [cite: 51] [cite_start]You can delete individual runs using the x button. [cite: 52]

## [cite_start]Technical Details [cite: 53]

### [cite_start]File Structure [cite: 54]
[cite_start]`flowmaster.html` # The entire app (single file, ~41KB) [cite: 55]
That's it. [cite_start]Everything is contained in one HTML file with embedded CSS and JavaScript. [cite: 56]

### [cite_start]Browser Requirements [cite: 57]
* [cite_start]Any modern browser with HTML5 Canvas support. [cite: 58]
* [cite_start]JavaScript must be enabled. [cite: 59]
* [cite_start]LocalStorage support for the audit log feature. [cite: 60]

### [cite_start]Data Privacy [cite: 61]
All processing happens in your browser. [cite_start]No data is sent to any server. [cite: 62] [cite_start]Your CSV files and results stay on your computer. [cite: 63]

## [cite_start]Troubleshooting [cite: 64]

| Problem | Solution |
| :--- | :--- |
| [cite_start]"Could not parse CSV" [cite: 65] | [cite_start]Check that your file has numeric values and uses comma, semicolon, or tab separators [cite: 65] |
| [cite_start]Chart looks empty [cite: 65] | [cite_start]Make sure you have at least 2 data points and valid numeric values [cite: 65] |
| [cite_start]Audit log is empty [cite: 65] | [cite_start]The log starts fresh; run a computation to populate it [cite: 65] |
| [cite_start]App won't open [cite: 65] | [cite_start]Try a different browser or check that JavaScript is enabled [cite: 65] |

## [cite_start]About This Project [cite: 66]
[cite_start]Built for the City Water Management Board as part of a hydraulics engineering assignment. [cite: 67] [cite_start]The goal was to create a practical tool for estimating water volumes in drainage canals using real-world sampling data and standard numerical methods. [cite: 68]

[cite_start]Group: 02 Version: 1.0 [cite: 69]
[cite_start]Year: 2026 [cite: 70]

## [cite_start]Quick Reference [cite: 72]
* [cite_start]$A=$ Canal cross-section area (constant, in m²). [cite: 73]
* [cite_start]$h=$ Sampling step / time interval between readings (in seconds). [cite: 74]
* [cite_start]$v(t)=$ Velocity at time t (in m/s). [cite: 75]
* [cite_start]$V=$ Total water volume (in m³). [cite: 76]
* [cite_start]$Q=$ Flow rate $=A\times v$ (in m³/s). [cite: 77]

[cite_start]FLOW-MASTER SYSTEMS Hydraulics Console [cite: 78]
