# 🎮 Plastic Punk Retro

[![Flutter SDK](https://img.shields.io/badge/Flutter-SDK%20%3E%3D3.2.3%20%3C4.0.0-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
[![Flame Engine](https://img.shields.io/badge/Flame-v1.17.0-F57C00?style=for-the-badge)](https://flame-engine.org)
[![Riverpod](https://img.shields.io/badge/Riverpod-v2.5.1-02569B?style=for-the-badge)](https://riverpod.dev)
[![Firebase](https://img.shields.io/badge/Firebase-Connected-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com)
[![Platform Support](https://img.shields.io/badge/Platforms-Android%20%7C%20iOS%20%7C%20Web%20%7C%20macOS-474747?style=for-the-badge)](#)

A retro-style eco-strategy and simulation game built with **Flutter** and the **Flame Engine**. Embodying classic 8-bit aesthetics, *Plastic Punk Retro* takes players on a journey into plastic pollution cleanup, ocean recycling, and diplomatic coordination to restore balance and create a happier, greener world.

---

## 🌟 Key Features

*   **Retro Tiled Simulation:** Explore and clean up interactive game maps loaded with contaminated waters, polluted lands, and eco-hazards using retro tilesets.
*   **Infrastructure Building:** Design and manage strategic environmental sites including:
    *   **Recycling Factories** to convert plastics into resources.
    *   **Water Treatment Units** to purge toxic waste from water reservoirs.
    *   **Research & Education Centres** to educate citizens and discover green upgrades.
    *   **Solar Panels** to generate clean energy.
*   **Dynamic HUD & Live Metrics:** Monitor real-time statistics including money, clean energy reserves, global pollution levels, and active environmental missions.
*   **Research & Technology Tree:** Unlock advanced recycling methodologies and building efficiency upgrades through the research system.
*   **Diplomatic Missions:** Form alliances and coordinate cleaning campaigns with neighboring regions through interactive dialogue events.
*   **Achievement Matrix:** Track milestones and achievements as you progress in building a greener society.
*   **Cloud Synchronization:** Cloud saving backed by **Firebase Cloud Firestore** alongside offline caching via **SharedPreferences** ensures seamless progress.
*   **Thematic Audio Experience:** Engaging 8-bit chiptunes and responsive sound effects powered by `flame_audio`.

---

## 🛠️ Tech Stack & Dependencies

*   **Core Game Engine:** [Flame](https://pub.dev/packages/flame) & [Flame Tiled](https://pub.dev/packages/flame_tiled) (2D game loops, camera mechanics, sprites, and TMX map loaders).
*   **State Management:** [Riverpod](https://pub.dev/packages/flutter_riverpod) (Type-safe annotation-driven reactive state logic).
*   **Backend Integration:**
    *   `firebase_core` & `firebase_auth`
    *   `cloud_firestore` (User-profile sync, scores, and saves)
    *   `firebase_analytics` & `firebase_crashlytics`
*   **Animations:** [Flutter Animate](https://pub.dev/packages/flutter_animate) (Rich, beautiful micro-interactions in menus and overlays).
*   **Storage & Utilities:** `shared_preferences` (offline local state), `easy_debounce`, and `intl`.

---

## 📁 Repository Structure

```text
d:\Plastic-Punk-Retro
├── assets/                          # Static Game Assets
│   ├── audio/                       # SFX loops and chiptunes
│   ├── fonts/                       # Customized Fonts (Teko, 04B_30)
│   ├── images/                      # App UI sprites, app_assets, flag codes
│   └── tiles/                       # TMX map files & PNG tilesets
├── lib/                             # Core Application Source Code
│   ├── services/                    # Remote & Local Integrations
│   │   ├── auth/                    # Game authentication logic
│   │   ├── firebase/                # Cloud Firestore communication
│   │   └── user/                    # Current user profile management
│   ├── state/                       # Riverpod State Management
│   │   └── game/                    # Game system providers (Camera, Save, Score, etc.)
│   ├── screens/                     # Flutter UI Screens & Overlays
│   │   ├── splash/                  # Game introduction/Splash
│   │   ├── menu/                    # Main lobby / Settings screen
│   │   └── game/                    # HUD overlay, Build, Research, Saves, Diplomacy
│   └── utils/                       # Calculations, math helpers, constants
├── pubspec.yaml                     # Dependencies and assets declaration
└── README.md                        # Project Overview (This File)
```

---

## 🚀 Getting Started

Follow these steps to run the game locally:

### 1. Prerequisites
Ensure you have the Flutter SDK installed on your system.
*   **Flutter SDK:** `>=3.2.3 <4.0.0`
*   **Dart SDK:** Matches Flutter version requirements.

### 2. Clone and Setup
Get the dependencies:
```bash
flutter pub get
```

### 3. Generate Riverpod & Freezed Classes
The project uses code generation for Riverpod states and serialization:
```bash
dart run build_runner build --delete-conflicting-outputs
```

### 4. Build & Run
Run on your emulator, browser, or connected device:
```bash
flutter run
```

---

## 🎨 Asset Credits
*   **Fonts:** `Teko` & `04B_30` pixel-art font styles.
*   **Audio:** Retro 8-bit soundtracks, SFX loops, and chiptunes.
*   **Map System:** Created using [Tiled Map Editor](https://www.mapeditor.org/) and parsed with Flame.
