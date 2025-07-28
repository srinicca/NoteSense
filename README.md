# NoteSense
# Real-Time Music Transcriber with Hindustani Support

A sophisticated real-time music transcription application that supports both Western and Hindustani (North Indian Classical) music systems. This tool can listen to live audio input and identify musical notes in real-time, displaying them using either Western notation (C, D, E...) or Hindustani sargam (सा, रे, ग...).

## Features

- **Dual Note System Support**: Switch between Western and Hindustani musical note systems
- **Real-Time Audio Processing**: Live microphone input with continuous pitch detection
- **Visual Feedback**: Real-time graphs showing frequency detection and note identification
- **Devanagari Script Support**: Authentic display of Hindustani notes in सरगम notation
- **Just Intonation**: Proper microtonal support for Hindustani music
- **Session Export**: Save transcription sessions for later analysis
- **Confidence-Based Detection**: Only displays notes with sufficient confidence levels

## Musical Systems Supported

### Western System
- 12-tone equal temperament
- Notes: C, C#, D, D#, E, F, F#, G, G#, A, A#, B
- Covers octaves 3-6 (130 Hz - 1046 Hz)

### Hindustani System
- Just intonation ratios
- Swaras: सा (Sa), रे (Re), ग (Ga), म (Ma), प (Pa), ध (Dha), नि (Ni)
- Includes komal (♭) and tivra (♯) variants
- Authentic microtonal intervals for classical Indian music

## Installation

### Prerequisites

```bash
pip install numpy scipy matplotlib pyaudio tkinter
```

### System Requirements

- **Python**: 3.7 or higher
- **Operating System**: Windows, macOS, or Linux
- **Audio**: Microphone or audio input device
- **Memory**: Minimum 512 MB RAM
- **Storage**: 50 MB free space

### Platform-Specific Setup

#### Windows
```bash
# Install PyAudio (may require Visual C++ Build Tools)
pip install pyaudio

# Alternative if above fails:
conda install pyaudio
```

#### macOS
```bash
# Install PortAudio first
brew install portaudio

# Then install PyAudio
pip install pyaudio
```

#### Linux (Ubuntu/Debian)
```bash
# Install system dependencies
sudo apt-get install python3-pyaudio portaudio19-dev

# Install Python packages
pip install pyaudio
```

## Usage

### Basic Operation

1. **Start the Application**:
   ```bash
   python music_transcriber.py
   ```

2. **Select Note System**:
   - Choose "Western (Do-Re-Mi)" for standard Western notation
   - Choose "Hindustani (सा-रे-ग)" for Indian classical music

3. **Begin Recording**:
   - Click "Start Recording" to begin real-time transcription
   - Sing or play notes near your microphone
   - Watch the real-time visualization

4. **Stop and Export**:
   - Click "Stop Recording" to end the session
   - Export your session data for analysis

### Interface Guide

#### Control Panel
- **Start/Stop Buttons**: Control recording state
- **Note System Selection**: Toggle between Western and Hindustani
- **Current Note Display**: Shows the currently detected note
- **Status Indicator**: Shows recording status

#### Visualization
- **Frequency Graph**: Real-time frequency detection (100-1000 Hz)
- **Notes Timeline**: Detected notes plotted over time
- **Confidence Visualization**: Only confident detections are displayed

### Note System Details

#### Western Notes
```
C3, C#3, D3, D#3, E3, F3, F#3, G3, G#3, A3, A#3, B3
C4, C#4, D4, D#4, E4, F4, F#4, G4, G#4, A4, A#4, B4
C5, C#5, D5, D#5, E5, F5, F#5, G5, G#5, A5, A#5, B5
C6
```

#### Hindustani Swaras
```
Shuddh (Natural): सा रे ग म प ध नि
Komal (Flat): रे♭ ग♭ ध♭ नि♭
Tivra (Sharp): म♯
```

## Configuration

### Audio Settings
```python
CHUNK = 4096          # Audio buffer size
RATE = 22050          # Sample rate (Hz)
CHANNELS = 1          # Mono audio
BUFFER_DURATION = 2.0 # Seconds of audio buffer
```

### Detection Settings
```python
ANALYSIS_INTERVAL = 0.1  # Analysis frequency (seconds)
MIN_CONFIDENCE = 0.5     # Minimum confidence threshold
tolerance = 30           # Frequency tolerance (Hz)
```

### Frequency Ranges
- **Detection Range**: 80 Hz - 2000 Hz (vocal range)
- **Display Range**: 100 Hz - 1000 Hz
- **Note Range**: 130 Hz - 1046 Hz (C3 - C6)

## File Structure

```
music_transcriber/
├── music_transcriber.py    # Main application
├── README.md              # This file
├── requirements.txt       # Python dependencies
└── sessions/             # Exported session data
    ├── session_western_*.txt
    └── session_hindustani_*.txt
```

## Session Export Format

Exported sessions contain:
```
Time(s)  Note    Display    Frequency(Hz)  Confidence
0.100    C4      C4         261.6          0.850
0.200    D4      D4         293.7          0.920
0.300    Sa4     सा4        261.6          0.875
```

## Technical Details

### Pitch Detection Algorithm
- **Windowing**: Hanning window for spectral analysis
- **FFT**: Fast Fourier Transform for frequency domain analysis
- **Peak Detection**: Scipy peak finding with confidence thresholds
- **Filtering**: Vocal range filtering (80-2000 Hz)

### Note Mapping
- **Western**: 12-tone equal temperament
- **Hindustani**: Just intonation with traditional ratios
- **Tolerance**: Adaptive frequency tolerance for each system

### Real-Time Processing
- **Multi-threading**: Separate threads for audio capture and analysis
- **Circular Buffer**: Efficient audio data management
- **Queue System**: Thread-safe audio data transfer

## Troubleshooting

### Common Issues

#### No Audio Input Detected
```bash
# Check microphone permissions
# Windows: Settings → Privacy → Microphone
# macOS: System Preferences → Security & Privacy → Microphone
# Linux: Check ALSA/PulseAudio configuration
```

#### PyAudio Installation Errors
```bash
# Try alternative installation methods:
conda install pyaudio
# or
pip install pipwin
pipwin install pyaudio
```

#### Poor Note Detection
- Ensure quiet environment
- Sing/play clearly and steadily
- Adjust microphone sensitivity
- Check if notes are in supported range (C3-C6)

#### GUI Display Issues
```bash
# Install tkinter if missing:
# Ubuntu/Debian:
sudo apt-get install python3-tk

# macOS (if using Homebrew Python):
brew install tcl-tk
```

### Performance Optimization

#### Reduce Latency
```python
CHUNK = 2048          # Smaller buffer
ANALYSIS_INTERVAL = 0.05  # More frequent analysis
```

#### Improve Accuracy
```python
MIN_CONFIDENCE = 0.7  # Higher confidence threshold
tolerance = 20        # Stricter frequency matching
```

## Contributing

### Development Setup
1. Clone the repository
2. Install development dependencies
3. Run tests
4. Submit pull requests

## Acknowledgments

- **Hindustani Music Theory**: Based on traditional just intonation ratios
- **Audio Processing**: Built with NumPy and SciPy
- **GUI Framework**: Tkinter and Matplotlib
- **Cultural Accuracy**: Authentic Devanagari script representation



*"संगीत सर्वभूतानाम्" - Music is the universal language* 🎵
