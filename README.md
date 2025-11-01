# Static Demo Pages - Panic Attack Detection System

This folder contains static HTML pages for demonstrating the Panic Attack Detection System without needing to run the Flask backend server.

## 📁 Files Overview

### Main Pages
- **`index.html`** - Main dashboard with AI assistant, panic status, and navigation
- **`profile.html`** - User profile setup page
- **`monitoring.html`** - Live sensor data monitoring (simulated)
- **`history.html`** - Panic attack episode history log
- **`calming_methods.html`** - Emotion-based music recommendation and breathing exercises

## 🚀 How to Use for Demo

### Option 1: Open Directly in Browser
1. Simply double-click on `index.html` to open in your default browser
2. Navigate between pages using the links provided
3. All functionality is self-contained with simulated data

### Option 2: Using a Local Server (Recommended)
For better experience, use a local web server:

```bash
# Using Python 3
cd online
python -m http.server 8000

# Using Python 2
python -m SimpleHTTPServer 8000

# Using Node.js (if you have http-server installed)
npx http-server -p 8000
```

Then open: http://localhost:8000

### Option 3: Host on GitHub Pages
1. Create a new repository
2. Upload the contents of the `online` folder
3. Enable GitHub Pages in repository settings
4. Access via: `https://yourusername.github.io/repo-name`

### Option 4: Deploy to Netlify/Vercel
1. Drag and drop the `online` folder to [Netlify Drop](https://app.netlify.com/drop)
2. Get instant live demo URL
3. No configuration needed!

## ✨ Features Demonstrated

### 1. Dashboard (`index.html`)
- **AI Assistant**: Interactive chatbot for panic attack support
  - Ask about breathing exercises
  - Get information about panic symptoms
  - Conversational interface
- **Panic Status Indicator**: Visual alert system
- **Physical Activity Mode**: Toggle for exercise mode
- **Quick Actions**: Yes/No panic buttons
- **I'm Okay Button**: Appears when panic is triggered

### 2. Live Monitoring (`monitoring.html`)
- Real-time sensor data simulation
- Heart Rate (60-120 bpm)
- Temperature (36.5-37.5°C)
- SpO2 levels (95-100%)
- Status indicators with color coding

### 3. History Log (`history.html`)
- Episode tracking with timestamps
- Vital signs recorded during episodes
- Statistics dashboard:
  - Total episodes
  - This week count
  - This month count
- Generate sample data button
- Clear history function
- Data persists in localStorage

### 4. Calming Methods (`calming_methods.html`)
- **Emotion Detection**: Based on simulated vital signs
- **Music Recommendation**: Emotion-based music selection
- **4-7-8 Breathing Exercise**: 
  - Interactive animated guide
  - Inhale (4 seconds)
  - Hold (7 seconds)
  - Exhale (8 seconds)
- Beautiful gradient design

### 5. User Profile (`profile.html`)
- Personal information collection
- Medical condition notes
- Emergency contact setup
- Data stored in localStorage

## 🎨 Design Features

- **Responsive Design**: Works on mobile, tablet, and desktop
- **Modern UI**: Clean, professional interface
- **Smooth Animations**: Engaging user experience
- **Color-Coded Status**: Easy visual understanding
- **Accessibility**: Clear fonts and good contrast

## 🔧 Technical Details

### Data Simulation
All pages use JavaScript to simulate:
- Live sensor readings (random within realistic ranges)
- Emotion classification algorithms
- Real-time updates every 2-3 seconds
- LocalStorage for persistence

### No Dependencies
- Pure HTML, CSS, and JavaScript
- No external libraries (except Google Fonts)
- Works completely offline (after first load)
- No backend server required

### Browser Compatibility
- Chrome ✅
- Firefox ✅
- Safari ✅
- Edge ✅
- Mobile browsers ✅

## 📊 Simulated Data Ranges

| Metric | Normal Range | Warning Range | Alert Range |
|--------|-------------|---------------|-------------|
| Heart Rate | 60-85 bpm | 85-100 bpm | >100 bpm |
| Temperature | 36.5-37.0°C | 37.0-37.2°C | >37.2°C |
| SpO2 | 98-100% | 96-97% | <96% |

## 🎭 Demo Flow

1. **Start**: Open `index.html`
2. **Profile Setup**: Click through to profile page (optional)
3. **Interact with AI**: Ask questions in the chatbot
4. **Trigger Panic**: Click "Yes" on panic question
5. **View Monitoring**: Navigate to live monitoring
6. **Check History**: View logged episodes
7. **Try Calming**: Use breathing exercises and music

## 📱 Mobile Demo Tips

- All pages are fully responsive
- Touch-friendly buttons and controls
- Optimized for smaller screens
- Landscape and portrait modes supported

## 🌐 URL Mapping (Flask to Static)

| Flask Route | Static File | Description |
|------------|-------------|-------------|
| `/` | `index.html` | Main dashboard |
| `/profile` | `profile.html` | User profile |
| `/monitoring` | `monitoring.html` | Live monitoring |
| `/history` | `history.html` | Episode history |
| `/calming_methods` | `calming_methods.html` | Calming tools |

## 💡 Customization Tips

### Change Sensor Ranges
Edit the JavaScript in each file:
```javascript
const heartRate = Math.floor(Math.random() * (120 - 60 + 1)) + 60;
```

### Modify Update Intervals
```javascript
setInterval(updateData, 2000); // Change 2000 to desired ms
```

### Add New Emotions
In `calming_methods.html`:
```javascript
const musicDatabase = {
    Happy: ["..."],
    YourEmotion: ["Song 1", "Song 2"]
};
```

## 🎥 Demo Presentation Tips

1. **Start with Profile**: Show personalization
2. **Dashboard Tour**: Highlight all features
3. **Trigger Panic**: Demonstrate alert system
4. **Show Monitoring**: Live data visualization
5. **Breathing Exercise**: Interactive demo
6. **History Review**: Data tracking capabilities

## 📝 Notes

- All data is stored locally in browser (localStorage)
- Clearing browser data will reset everything
- No actual sensor hardware required
- Perfect for presentations and demonstrations

## 🔮 Future Enhancements

- Add more emotion types
- Include actual audio files
- Advanced data visualization (charts)
- Export history to PDF
- Multi-language support

---

**Created for demonstration purposes**  
Based on the Flask application in the parent directory
"# CalmPoint" 
