# 🎮 Plastic Punk Retro

[![Flutter SDK](https://img.shields.io/badge/Flutter-SDK%20%3E%3D3.2.3%20%3C4.0.0-02569B?style=for-the-badge&logo=flutter&logoColor=white)](https://flutter.dev)
[![Flame Engine](https://img.shields.io/badge/Flame-v1.17.0-F57C00?style=for-the-badge)](https://flame-engine.org)
[![Riverpod](https://img.shields.io/badge/Riverpod-v2.5.1-02569B?style=for-the-badge)](https://riverpod.dev)
[![Firebase](https://img.shields.io/badge/Firebase-Connected-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com)
[![Platform Support](https://img.shields.io/badge/Platforms-Android%20%7C%20iOS%20%7C%20Web%20%7C%20macOS-474747?style=for-the-badge)](#)

A retro-style eco-strategy and simulation game built with **Flutter** and the **Flame Engine**. Embodying classic 8-bit aesthetics, *Plastic Punk Retro* takes players on a journey into plastic pollution cleanup, ocean recycling, and diplomatic coordination to restore balance and create a happier, greener world.

---

## 💡 Inspiration

The inspiration behind **Plastic Punk Retro** stems from two major influences: a deep concern for the global plastic pollution crisis and a nostalgic love for retro simulation and strategy games like *SimCity*, *Theme Hospital*, and classic tycoon titles. 

Every year, millions of tons of plastic waste enter our oceans, destroying ecosystems and impacting human health. While awareness campaigns exist, we felt that dry statistics often fail to engage people on an emotional level. We wanted to create something that gamifies environmental consciousness—not by lecturing the player, but by letting them experience the strategic complexity of ecological restoration firsthand. 

The term "Plastic Punk" represents a spin on the classic "cyberpunk" genre. Instead of a dystopian future dominated by high-tech corporate oppression, *Plastic Punk* represents a world grappling with the physical and environmental debris of the synthetic age, where the "punks" are the eco-engineers, community organizers, and scientists working to reclaim the Earth. By packaging this message in a charming, nostalgic 8-bit aesthetic, we make a heavy subject approachable, engaging, and fun.

---

## 🕹️ What It Does

**Plastic Punk Retro** is a fully interactive, cross-platform eco-strategy game where players take charge of cleaning up highly polluted regions. 

Upon launching a level, players are presented with an isometric grid map divided into land, water, and various types of contamination (plastic piles, toxic runoff, oil spills). To succeed, players must balance economic growth with environmental remediation using a variety of tools:
1.  **Remediation Infrastructure:** Players build structures such as **Water Treatment Plants** to purify rivers and oceans, **Recycling Factories** to convert plastic debris into spendable credits, and **Solar Arrays** to generate clean energy.
2.  **Resource Management:** Every action costs money or energy. Players must build a self-sustaining economy where recycling generates revenue, which is then reinvested into more advanced cleanup systems.
3.  **Active HUD & Eco-Metrics:** A dynamic HUD monitors global pollution index, energy levels, and funds. If the pollution index hits 100%, the ecosystem collapses, resulting in a game over.
4.  **Research & Development:** The technology tree allows players to research advanced recycling methods, reduce carbon footprints, and increase the efficiency of their cleanup buildings.
5.  **Diplomatic Missions & Narrative:** The game includes interactive dialog campaigns. Players must coordinate with neighboring cities to clean up cross-border pollution, negotiate budgets, and respond to environmental disasters.
6.  **Cloud Sync:** Progress is automatically saved locally using `shared_preferences` and synced to the cloud via **Firebase Firestore**, ensuring players never lose their progress across devices.

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

## 🛠️ How I Built It & Tech Stack

Building a real-time simulation game on a cross-platform framework required a modern, highly efficient technology stack:
*   **Core Game Engine:** [Flame](https://pub.dev/packages/flame) & [Flame Tiled](https://pub.dev/packages/flame_tiled) (2D game loops, camera mechanics, sprites, and TMX map loaders).
*   **State Management:** [Riverpod](https://pub.dev/packages/flutter_riverpod) (Type-safe annotation-driven reactive state logic).
*   **Backend Integration:**
    *   `firebase_core` & `firebase_auth`
    *   `cloud_firestore` (User-profile sync, scores, and saves)
    *   `firebase_analytics` & `firebase_crashlytics`
*   **Animations:** [Flutter Animate](https://pub.dev/packages/flutter_animate) (Rich, beautiful micro-interactions in menus and overlays).
*   **Storage & Utilities:** `shared_preferences` (offline local state), `easy_debounce`, and `intl`.
*   **Tiled Map Editor:** All game levels were designed in Tiled. We configured custom isometric projections, layer hierarchies, and trigger objects. The maps are dynamically parsed at runtime using `flame_tiled`.

---

## 🚧 Challenges I Ran Into

Integrating a high-performance game engine (Flame) with a reactive UI framework (Flutter) presented several architectural hurdles:
*   **Bridging Flame and Riverpod:** The Flame game loop runs independently of Flutter's build cycle. Passing real-time stats (like money and pollution) from Flame's update loop into Riverpod providers without triggering infinite build loops or lagging the UI was extremely tricky. We resolved this by using a custom state controller layer that debounces non-critical updates and only pushes UI-relevant state changes at fixed tick intervals.
*   **Isometric Coordinates & Collision:** Translating raw screen touch coordinates (Cartesian) into isometric grid coordinates for building placement was mathematically challenging. We had to implement custom coordinate transformation matrices and handle bounding boxes for multi-tile structures to prevent placement overlap.
*   **Asset Management and Flutter Web:** Web browsers handle image decoding and caching differently than native mobile apps. Initial attempts led to memory bloat and stuttering when loading the full sprite sheet. We optimized this by packing all tiles into a unified texture atlas, utilizing `loadAllFromPattern` during the splash screen, and caching assets locally to prevent network lag.
*   **Offline Saving Synchronicity:** Managing state when a player loses internet connection mid-game required a robust syncing algorithm. We created a local-first architecture where the game saves to `shared_preferences` instantly, queues the save event, and pushes it to Firestore once a stable connection is re-established.

---

## 🏆 Accomplishments That I'm Proud Of

*   **Fluid Cross-Platform Experience:** The game runs at a locked 60 FPS on Android, macOS, and Web platforms without any platform-specific code branch differences.
*   **Deep State Synchronization:** We created a highly reactive HUD and build menu overlay in Flutter that reflects changes in the underlying Flame game world instantly.
*   **Charming Retro Atmosphere:** The synergy between the custom 8-bit pixel art, the custom Teko and 04B_30 typography, and the retro chiptunes creates a highly polished, nostalgic aesthetic that immediately hooks the player.
*   **Strategic Depth:** The balancing of the economy (energy vs. funds vs. pollution cleanup speed) works naturally, providing a genuine challenge reminiscent of classic strategy games.

---

## 📖 What I Learned

*   **Advanced Game Loop Architecture:** I gained deep experience in separating rendering logic from game simulation logic, using tick-based updates to decouple heavy calculations from the render loop.
*   **Isometric Vector Mathematics:** Working on this project deepened my understanding of coordinate systems, specifically translation, rotation, and skew matrices required to project 2D assets into a pseudo-3D isometric perspective.
*   **State Management in Hybrid Apps:** I learned the limits of combining declarative UI state with imperative game loop engines, establishing a robust paradigm for Flame and Riverpod integration.
*   **Optimization of Web Canvas Assets:** I discovered the importance of image asset optimization, sprite sheeting, and garbage collection mechanisms on web browsers.

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

## 📁 Repository Structure

Click on any folder or file to inspect its content:

<details>
<summary>📂 View Repository Tree</summary>

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
</details>

*   📂 [assets](file:///d:/Plastic-Punk-Retro/assets) — Static assets (Audio, Fonts, Images, Map tiles)
*   📂 [lib](file:///d:/Plastic-Punk-Retro/lib) — Core application package
    *   📂 [services](file:///d:/Plastic-Punk-Retro/lib/services) — Authenticators, analytics, database services
    *   📂 [state](file:///d:/Plastic-Punk-Retro/lib/state) — [Riverpod](https://pub.dev/packages/flutter_riverpod) controllers and app state notifier providers
    *   📂 [screens](file:///d:/Plastic-Punk-Retro/screens) — Flutter UI components, game controller wrappers, overlay components
        *   📄 [splash.dart](file:///d:/Plastic-Punk-Retro/screens/splash/splash.dart) — Initial game introduction splash screen
        *   📄 [menu.dart](file:///d:/Plastic-Punk-Retro/screens/menu/menu.dart) — Main landing page lobby screen
        *   📄 [game.dart](file:///d:/Plastic-Punk-Retro/screens/game/game.dart) — Game play arena viewport wrapper
    *   📂 [utils](file:///d:/Plastic-Punk-Retro/lib/utils) — Shared helper functions, metrics formulas, mathematical coordinates translations
*   📄 [pubspec.yaml](file:///d:/Plastic-Punk-Retro/pubspec.yaml) — Project dependencies configuration
*   📄 [README.md](file:///d:/Plastic-Punk-Retro/README.md) — Documentation manual (This file)

---

## 🔮 What's Next for Plastic-Punk-Retro

We have big plans to expand the game into a fully-featured simulation experience:
*   **Procedural Map Generation:** Instead of fixed pre-designed levels, we want to build a procedural generator that creates unique coastlines, pollution distributions, and resource nodes for infinite replayability.
*   **Weather and Seasonal Dynamics:** Introducing environmental variables like storms (which increase ocean plastic movement), droughts (which reduce water treatment efficiency), and clear days (which boost solar panel production).
*   **Real-Time Community Events:** Global leaderboards and cooperative campaigns where players combine their recycled resources to unlock global upgrades and restore planetary health.
*   **Deeper Diplomatic Decision Tree:** Expanding the narrative mechanics to include moral dilemmas, corporate negotiations, and public relations campaigns that affect citizen happiness and funding.
*   **Mobile App Store Launch:** Packaging the game for a formal release on the Google Play Store and iOS App Store.

---

## 🎨 Asset Credits

*   **Fonts:** `Teko` & `04B_30` pixel-art font styles.
*   **Audio:** Retro 8-bit soundtracks, SFX loops, and chiptunes.
*   **Map System:** Created using [Tiled Map Editor](https://www.mapeditor.org/) and parsed with Flame.

