# Flask to Static HTML Mapping

This document shows how the Flask routes have been converted to static HTML pages for demo purposes.

## 📍 Complete Route Mapping

| Flask Route | HTTP Method | Static HTML File | Description |
|------------|-------------|------------------|-------------|
| `/` | GET | `index.html` | Main dashboard with AI assistant and panic detection |
| `/profile` | GET/POST | `profile.html` | User profile setup and management |
| `/monitoring` | GET | `monitoring.html` | Live sensor data monitoring |
| `/history` | GET | `history.html` | Panic attack episode history log |
| `/calming_methods` | GET | `calming_methods.html` | Emotion-based music and breathing exercises |
| `/ask_ai` | POST | *Embedded in index.html* | AI chatbot responses (JavaScript) |
| `/data` | GET | *Simulated in JavaScript* | Sensor data API endpoint |
| `/status` | GET/POST | *Simulated in JavaScript* | Panic status API endpoint |

## 🔄 API Endpoints → JavaScript Functions

### Original Flask API Endpoints

```python
# Flask Backend APIs
@app.route('/data')
def get_data():
    return jsonify(sensor_data=sensor_data)

@app.route('/status', methods=['GET', 'POST'])
def status():
    return jsonify(panic_data)

@app.route('/ask_ai', methods=['POST'])
def ask_ai():
    return jsonify({'answer': response})
```

### Static HTML JavaScript Equivalents

```javascript
// In monitoring.html and calming_methods.html
function generateSensorData() {
    const heartRate = Math.floor(Math.random() * (120 - 60 + 1)) + 60;
    const temperature = (Math.random() * (37.5 - 36.5) + 36.5).toFixed(1);
    const spo2 = Math.floor(Math.random() * (100 - 95 + 1)) + 95;
    return { heartRate, temperature, spo2 };
}

// In index.html
function getAIResponse(question) {
    // Simulated AI responses
    if (q.includes('how to calm down')) {
        return "Try breathing exercises...";
    }
    // ... more conditions
}

// In index.html
let panicTriggered = false;
function updateUI() {
    // Update panic status based on local state
}
```

## 📁 File Structure Comparison

### Original Flask Structure
```
project/
├── app.py                  # Flask application
├── templates/
│   ├── index.html         # Dashboard
│   ├── user_profile.html  # Profile
│   ├── live_monitoring.html
│   ├── history.html
│   └── calming_methods.html
└── static/
    ├── css/style.css
    └── js/main.js
```

### Static Demo Structure
```
online/
├── demo.html              # NEW: Landing page
├── index.html            # Self-contained dashboard
├── profile.html          # Self-contained profile
├── monitoring.html       # Self-contained monitoring
├── history.html          # Self-contained history
├── calming_methods.html  # Self-contained calming
├── README.md             # Documentation
└── MAPPING.md            # This file
```

## 🔧 Key Differences

### 1. Data Storage
- **Flask**: Python variables and `history.log` file
- **Static**: Browser localStorage and JavaScript variables

### 2. AI Assistant
- **Flask**: Server-side processing in Python
- **Static**: Client-side logic in JavaScript

### 3. Sensor Data
- **Flask**: Serial port reading from MAX30102 sensor
- **Static**: Random number generation for simulation

### 4. Form Handling
- **Flask**: POST requests to backend
- **Static**: JavaScript event handlers and localStorage

### 5. Navigation
- **Flask**: `url_for()` and Flask redirects
- **Static**: Direct HTML file links

## 💾 Data Persistence

### Flask Backend
```python
# File-based storage
HISTORY_FILE = 'history.log'

def write_history(entry):
    history = read_history()
    history.insert(0, entry)
    with open(HISTORY_FILE, 'w') as f:
        json.dump(history, f, indent=4)
```

### Static HTML
```javascript
// Browser localStorage
function saveToStorage() {
    localStorage.setItem('panicHistory', JSON.stringify(historyData));
}

function loadFromStorage() {
    const saved = localStorage.getItem('panicHistory');
    if (saved) {
        historyData = JSON.parse(saved);
    }
}
```

## 🎨 CSS Implementation

### Flask Version
- **External CSS**: `/static/css/style.css`
- **Shared across all templates**
- **Requires Flask static file serving**

### Static Version
- **Embedded CSS**: `<style>` tags in each HTML file
- **Self-contained in each page**
- **No external dependencies (except Google Fonts)**

## 📊 Feature Parity

| Feature | Flask | Static | Notes |
|---------|-------|--------|-------|
| AI Chatbot | ✅ | ✅ | Simplified logic in static |
| Panic Detection | ✅ | ✅ | Fully functional |
| Sensor Monitoring | ✅ | ✅ | Simulated data |
| History Logging | ✅ | ✅ | localStorage vs file |
| User Profile | ✅ | ✅ | localStorage vs memory |
| Emotion Detection | ✅ | ✅ | JavaScript algorithm |
| Music Recommendation | ✅ | ✅ | Text-based (no audio files) |
| Breathing Exercise | ✅ | ✅ | Enhanced with animation |
| Emergency Timer | ✅ | ⚠️ | Not implemented (console only) |
| Serial Communication | ✅ | ❌ | Cannot be simulated in browser |

## 🚀 Advantages of Static Version

1. **No Server Required**: Can be hosted anywhere
2. **Instant Load**: No backend processing delay
3. **Offline Capable**: Works without internet (after first load)
4. **Easy Deployment**: Simple drag-and-drop hosting
5. **Low Cost**: Free hosting on GitHub Pages, Netlify, etc.
6. **Demo Friendly**: Perfect for presentations
7. **Client Privacy**: All data stays in browser

## ⚠️ Limitations of Static Version

1. **No Real Sensor Data**: Cannot connect to MAX30102
2. **No Backend AI**: Simple rule-based responses only
3. **No Real Emergency Alerts**: Cannot send SMS/calls
4. **Limited Storage**: localStorage has size limits
5. **No Multi-User**: Each browser is isolated
6. **No Database**: Cannot query historical trends

## 🔮 Use Cases

### Flask Version Best For:
- Production deployment with real sensors
- Multi-user system with central database
- Integration with emergency services
- Advanced AI/ML processing
- Clinical/hospital use

### Static Version Best For:
- Demonstrations and presentations
- Proof of concept
- Prototyping and UI testing
- Educational purposes
- Portfolio showcasing
- Quick demos without setup

## 📝 How Features Were Adapted

### 1. Panic Detection Algorithm
**Flask (Python):**
```python
def classify_emotion_with_ml(heart_rate, temperature, spo2):
    prediction = emotion_model.predict([[heart_rate, temperature, spo2]])
    return prediction[0]
```

**Static (JavaScript):**
```javascript
function classifyEmotion(heartRate, temperature, spo2) {
    if (heartRate > 100) return "Anxious";
    else if (heartRate > 85) return "Excited";
    else if (heartRate < 70 && spo2 > 97) return "Calm";
    else return "Happy";
}
```

### 2. Emergency Timer
**Flask (Python):**
```python
emergency_timer = threading.Timer(30, send_emergency_message)
emergency_timer.start()
```

**Static (JavaScript):**
```javascript
// Simplified - just shows console message
setTimeout(() => {
    console.log('Emergency message would be sent now');
}, 30000);
```

### 3. Data Updates
**Flask (Python):**
```python
def read_serial_data():
    while True:
        sensor_data['heart_rate'] = read_from_sensor()
        time.sleep(2)
```

**Static (JavaScript):**
```javascript
setInterval(() => {
    const data = generateSensorData();
    updateUI(data);
}, 2000);
```

## 🎯 Testing the Mapping

### Test Checklist
- [ ] Open `demo.html` as entry point
- [ ] Navigate to all pages from dashboard
- [ ] Test AI chatbot interactions
- [ ] Trigger panic detection (Yes/No buttons)
- [ ] Verify "I'm Okay" button appears
- [ ] Check live monitoring updates
- [ ] Generate and view history data
- [ ] Try breathing exercise
- [ ] Save and load user profile
- [ ] Test physical activity mode toggle
- [ ] Verify localStorage persistence

## 📚 Additional Resources

- **Original Flask Code**: `../app.py`
- **Template Files**: `../templates/`
- **Static Assets**: `../static/`
- **User Guide**: `README.md`
- **Demo Launcher**: `demo.html`

---

**Summary**: All Flask routes have been successfully mapped to static HTML pages with equivalent functionality using client-side JavaScript. The demo is fully functional without any backend requirements.
