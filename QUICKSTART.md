# PLANE1 Quick Start & Troubleshooting

## ✅ Latest Fixes Applied:
1. Cockpit expanded by default
2. `takeOff`, `land`, `changeDestination` made globally accessible
3. Debug logging throughout

## 🚀 How to Use:

### After Dismissing Welcome Screen:

You should see:
- **Flight Controls panel** (expanded, visible)
- **Take Off button** (green, clickable)
- **Land button** (disabled/grayed out)
- **Destination buttons** (8 buttons in a grid)
- **Flight gauges** (Time, Altitude, Tempo)

### To Take Off:
1. Click the green **"Take Off"** button
2. OR press **Spacebar**

### What You Should See in Console:
```
[DEBUG] [INPUT] Take Off button clicked
[INFO] [FLIGHT] TAKEOFF SEQUENCE INITIATED
```

### If You See This Instead:
```
[WARN] [FLIGHT] Landing requested but not flying
```
**You're clicking destination buttons, not the Take Off button!**

## 🐛 Current Issues in Your Logs:

### Problem: Clicking Wrong Buttons
You're clicking destination buttons (World Tour, Asia, etc.) which try to land.
**These are for AFTER you land**, not for taking off.

### Solution:
1. Hard refresh: `Cmd+Shift+R` (Mac) or `Ctrl+F5` (Windows)
2. Dismiss welcome screen
3. Look for the **GREEN "Take Off" button** in the Flight Deck section
4. Click THAT button (or press Spacebar)

## 📸 What to Look For:

The Flight Deck panel should show:
```
┌─────────────────────────────┐
│ Flight Deck                  │
├─────────────────────────────┤
│ [Take Off]  [Land (disabled)]│
│ [Test Audio] [Full Screen]   │
│ [Randomize All]              │
│ [Hide UI] [Clear Trail]      │
│ [Flight Log]                 │
└─────────────────────────────┘
```

## 🔍 Debugging:

Open Console (F12) and run:
```javascript
// Check if functions exist
console.log('takeOff:', typeof window.takeOff);
console.log('land:', typeof window.land); 
console.log('changeDestination:', typeof window.changeDestination);

// Check button
console.log('Take Off button:', document.getElementById('takeoff'));

// Try manual takeoff
window.takeOff();
```

All should show "function" and the last command should start your flight!
