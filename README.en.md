# Variable Speed Audio/Video Player with Custom Functions

A TypeScript-based web application that controls audio/video playback speed through custom mathematical functions or graphical drawing, enabling dynamic variable-speed playback effects.

## Purpose

This project allows users to define playback rate functions through three methods:

1. **Formula Input**: Define rate functions using mathematical expressions, supporting common math functions (sin, cos, log, exp, etc.)
2. **Graphical Drawing**: Draw function curves directly on a canvas, supporting closed curves and direction selection
3. **Preset Functions**: Select preset rate modes (constant, linear acceleration, sine wave, pulse wave, etc.)

The system adjusts audio/video playback speed in real-time based on the defined function and visualizes it on two canvases:
- **Source Function Graph**: Displays the original function curve and current playback position
- **Playback Rate Time Curve**: Shows the rate trajectory over time

## Implementation

### Tech Stack

- **TypeScript**: Type-safe JavaScript superset
- **HTML5 Canvas**: For function graph drawing and visualization
- **Web Audio/Video API**: Controls media playback speed
- **Vanilla JavaScript**: No framework dependencies, lightweight implementation

### Core Features

#### 1. Mathematical Formula Parsing

- Supports simplified math syntax (e.g., `sin`, `cos`, `pi`, `^`, etc.)
- Automatically converts to JavaScript Math functions
- Variables `t` represents current time, `d` represents total duration

#### 2. Graphical Drawing Processing

- **Non-closed Curves**: Maps X-axis coordinates to time, Y-axis to playback rate
- **Closed Curves**: Uses arc length parameterization, supports clockwise/counterclockwise traversal
- **Auto-scaling**: Maps the drawn minimum value to 1x, maximum to the maximum rate limit

#### 3. Rate Control

- Uses `media.playbackRate` API to adjust playback speed in real-time
- Implements smooth rate updates through `requestAnimationFrame`
- Rate range is limited between 1x and the maximum rate limit

#### 4. Visualization

- **Source Function Canvas**: Displays the original function curve, marks current playback position
- **Preview Canvas**: Shows rate change curve over time, includes axes and grid

## Running the Project

### Requirements

- Node.js (for TypeScript compilation)
- Modern browser (supports ES2017+ and Canvas API)

### Install Dependencies

```bash
npm install
```

### Compile TypeScript

```bash
# One-time compilation
npm run build

# Or use watch mode (auto recompile)
npm run watch
```

### Start Local Server

Due to browser security restrictions, you need to access via HTTP server, not by directly opening the HTML file.

#### Method 1: Using Python

```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

#### Method 2: Using Node.js serve

```bash
npx serve .
```

#### Method 3: Using VS Code Live Server

Install the Live Server extension, right-click `index.html` and select "Open with Live Server"

### Access the Application

Open in browser:
```
http://localhost:8000
```

### Usage Steps

1. **Select Media File**: Click "选择音视频文件" (Select audio/video file), choose an audio or video file
2. **Choose Input Method**:
   - **Formula Input**: Enter mathematical expression, e.g., `sin((t / d) * pi * 4) + 2`
   - **Graphical Drawing**: Click or drag on canvas to draw curves
   - **Preset Functions**: Select preset mode from dropdown menu
3. **Adjust Parameters**: Set maximum rate limit (default 4x)
4. **Start Playback**: Click "应用函数并开始播放" (Apply function and start playback) button
5. **Observe Effects**: Playback speed changes in real-time according to the function, canvas displays current playback position

## Project Structure

```
.
├── src/
│   └── main.ts          # Main program logic
├── dist/
│   ├── main.js          # Compiled JavaScript
│   └── main.js.map      # Source map
├── index.html           # Main page
├── tsconfig.json        # TypeScript configuration
├── package.json         # Project configuration and dependencies
├── LICENSE              # MIT License
├── README.md            # Main README (language selector)
├── README.zh.md         # Chinese documentation
└── README.en.md         # English documentation
```

## Notes

- Playback speed is limited by browsers, typically ranging from 0.25x to 4x
- Some browsers may restrict autoplay, requiring manual user interaction
- In graphical drawing mode, closed curves are automatically detected and support looped playback
- Function values are automatically normalized to ensure minimum value is 1x

## License

This project is licensed under the [MIT License](LICENSE).

The MIT License allows:
- Commercial use
- Modification
- Distribution
- Private use

The only requirement is to retain the original copyright notice.
