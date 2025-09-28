## Driver App Project – Detailed Summary & Report  
**SIH-2025**

<img src="https://cdn-icons-png.flaticon.com/512/741/741407.png" alt="Bus App" width="200"/>

---

## 1. Project Overview

**Name:** Driver App (SIH-2025)

**Tech Stack:**  
- Frontend: React Native (Expo) <!-- .element: class="fragment fade-in" -->
- Backend: MQTT <!-- .element: class="fragment fade-in" -->
- Location: expo-location (High-accuracy GPS) <!-- .element: class="fragment fade-in" -->
- Navigation: React Navigation <!-- .element: class="fragment fade-in" -->
- Cloud Services: EAS Build (APK & AAB) <!-- .element: class="fragment fade-in" -->

**Purpose:**  
1. Scan QR codes for passenger verification <!-- .element: class="fragment fade-in" -->
2. Confirm route changes <!-- .element: class="fragment fade-in" -->
3. Share real-time location data <!-- .element: class="fragment fade-in" -->
4. Monitor tracking status, GPS accuracy, speed <!-- .element: class="fragment fade-in" -->

<img src="https://cdn-icons-png.flaticon.com/512/854/854878.png" width="150"/>

---

## 2. Key Features

**Live Tracking**  
Tracks bus location in real-time; publishes to MQTT every second or per meter <!-- .element: class="fragment grow" -->

**MQTT Integration**  
Lightweight, low-latency backend <!-- .element: class="fragment grow" -->

**Route Management**  
Change routes dynamically; restarts tracking <!-- .element: class="fragment grow" -->

**UI & Status**  
Bus number, route ID, MQTT status, publish count <!-- .element: class="fragment grow" -->

**Permissions & Accuracy**  
Uses BestForNavigation mode, requests foreground GPS permission <!-- .element: class="fragment grow" -->

---

## 3. Architecture

### Frontend
- `HomeScreen.tsx` → Entry point <!-- .element: class="fragment fade-left" -->
- `QRScanner.tsx` → QR code scanning <!-- .element: class="fragment fade-left" -->
- `RouteConfirmation.tsx` → Confirms route changes <!-- .element: class="fragment fade-left" -->
- `LiveTrackingHighAccuracy.tsx` → GPS tracking & MQTT publish <!-- .element: class="fragment fade-left" -->

### Backend
- `mqttService.ts` → Connect/disconnect/publish <!-- .element: class="fragment fade-right" -->
- `mqttConfig.ts` → Route settings <!-- .element: class="fragment fade-right" -->
- GPSData = `{ latitude, longitude, timestamp, accuracy, speed, heading }` <!-- .element: class="fragment fade-right" -->

---

## Navigation

Uses `createNativeStackNavigator` with screens:  
- Home <!-- .element: class="fragment fade-in" -->  
- QRScanner <!-- .element: class="fragment fade-in" -->  
- RouteConfirmation <!-- .element: class="fragment fade-in" -->  
- LiveTracking <!-- .element: class="fragment fade-in" -->  
- NotFound <!-- .element: class="fragment fade-in" -->

<img src="https://cdn-icons-png.flaticon.com/512/684/684908.png" width="200"/>

---

## 4. EAS Build Config (APK & AAB)

```json
{
  "cli": { "version": ">= 3.0.0" },
  "build": {
    "preview": { 
        "distribution": "internal", 
        "android": { "buildType": "apk" 
        } 
    },
    "release": { 
        "distribution": "store", 
        "android": { 
            "buildType": "app-bundle" 
        } 
    }
  }
}
````

<!-- .element: class="fragment highlight-current-blue" -->

* Preview → APK (internal testing)
* Release → AAB (Play Store)
* Build command → `eas build -p android --profile preview`

---

## 5. Common Issues & Fixes

* **useEffect missing dependency** → cleanup function or `// eslint-disable-next-line` <!-- .element: class="fragment fade-in" -->
* **EAS buildType error** → use only `apk` or `app-bundle` <!-- .element: class="fragment fade-in" -->
* **Node version incompatibility** → Node v16–17 for expo-cli <!-- .element: class="fragment fade-in" -->

---

## 7. Build & Release

* Release command: `eas build -p android --profile release` <!-- .element: class="fragment fade-in" -->
* Build time: APK 5–15 min, AAB 10–30 min <!-- .element: class="fragment fade-in" -->

<img src="https://cdn-icons-png.flaticon.com/512/906/906343.png" width="150"/>

---

## 8. Summary

* ✅ Real-time GPS via MQTT <!-- .element: class="fragment fade-in" -->
* ✅ Dynamic route management <!-- .element: class="fragment fade-in" -->
* ✅ EAS builds (APK & AAB) <!-- .element: class="fragment fade-in" -->
* ✅ Scalable, transport-ready solution <!-- .element: class="fragment fade-in" -->


---

## Thank you ❤ 
for spending your valuable time with us...