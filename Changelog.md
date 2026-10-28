# Changelog - SolarApp for AWTRIX

## [4.3.1] - 2026-10-22

### Changed

* **Max Power Setting:** Removed the upper limit for `max_power`.

---

## [4.3.0] - 2026-10-20

### Added
* **Hardware Button Toggle:** Pressing `Select` switches the lower line and right graphics between Daily Yield (`kWh`/`Wh` + solar panel) and live House Consumption (`W` + animated house).
* **House Consumption Tracking:** Added `# @config topic_consumption` for live household demand metrics.
* **Persistent View:** Active screen is saved to flash storage (`active_view`), paired with a `# @config default_view` setting.
* **Pixel-Art House Animation:**
  * **Surplus:** Green roof (`#00E676`) and golden window flashes as photons enter the house.
  * **Grid Import:** Warm amber roof (`#FF9100`) and coral-red readout (`#FF5252`).
  * **Window Glow:** Asynchronous hearth flicker (`#E65100`–`#FFD54F`) during grid import and night.

### Changed
* **Streamlined Styles:** Removed `sun_and_panel`; focused on `sun_large` and `sun_half`.
* **Zero Allocation Render Loop:** Removed runtime string builds and repeated `store.get()` calls in `draw()`.
* **Native Parsing:** Replaced `json.load()` with lightweight `num()` and native regex lookups.
* **Clean MQTT Lifecycle:** Subscriptions are now handled cleanly in `setup()`.

---

## [3.9.2] - 2026-10-20

### Added
* **Support for `consumption` JSON key:** The power topic now also accepts payloads such as `{"consumption": 420}` or `{"Consumption": 420}`, so the app can display values from sources that report power under this name.

---

## [3.9.1] - 2026-10-18

### Added
* **Expanded MQTT JSON Compatibility:** Added native support for `production`, `Production`, `solar_power`, `solar_production`, `P_PV`, `daily_production`, and `energy_today` JSON keys.
* **Broader Inverter & Smart Meter Support:** Plug-and-play compatibility with Enphase Envoy, SolarEdge, Shelly EM / Plus 1PM, Tasmota, OpenDTU, and Home Assistant sensors without requiring custom MQTT transformations.

---

## [3.9.0] - 2026-10-11

### Changed
* **Elongated Photon Streaks:** Solar particles now feature a smooth 2–3 pixel fading trail (comet-style streak) instead of isolated single dots.
* **Darker, Glare-Free Particle Tones:** Particle colors are now deeper terracotta, ember, and amber hues (`#C2410C`, `#B45309`, `#9A3412`, `#92400E`) with brightness capped at 60% so they remain subtle and never outshine digits.
* **Calmer Solar Panel Shimmer:** Reduced the shimmer speed of the right-edge solar panel by ~3.5× (~3.5 seconds per wave) for a serene, breathing visual effect.

---

## [3.8.0] - 2026-10-10

### Added
* **Dynamic Watt-Scaled Particle Speed:** Photons now flow visibly faster during high solar output (e.g. 800 W+) and drift leisurely during partial sun or morning/evening hours.
* **Subpixel Motion Smoothing:** Implemented horizontal subpixel brightness interpolation for buttery-smooth particle movement without LED stutter or jumping.

---

## [3.7.0] - 2026-10-10

### Added
* **Right-Edge Vertical Solar Module:** Added a sleek, 4-pixel wide pixel-art solar panel (`x: 48..51`) on the right side of the screen featuring a cyan aluminum frame and deep-blue silicon cells.
* **Flowing Solar Photons:** Added animated energy particles traveling across the screen from the sun through the numbers into the solar module.

---

## [3.6.0] - 2026-10-10

### Added
* **New Visual Style `sun_half`:** Added an oversized XXL half-sun rising along the left border with full 3D rotation and breathing corona.
* **Layout Selector:** Users can now choose their preferred style in the Web UI:
  * `sun_large`: Full 16×16 3D sun on the left with particle stream and right solar module.
  * `sun_half`: Giant half-sun on the left with particle stream and right solar module.
  * `sun_and_panel`: Compact sun top-left paired with a tilted ground solar module bottom-left.

---

## [3.5.0] - 2026-10-10

### Changed
* **Unified Power Display:** Matched the color of the Watt value and `W` unit in warm golden yellow (`#FFC107`).
* **Eco-Green Daily Yield:** Updated daily energy yield and unit (`kWh` / `Wh`) to fresh solar green (`#00E676`).

---

## [3.4.0] - 2026-10-10

### Added
* **Pixel-Art 8-Lobe Corona:** Completely redesigned sun sprite with an 8-lobed warm-gradient corona based on the community pixel-art mockup.
* **Real 3D Spherical Rotation:** True spherical projection with longitude tracking and 3D limb-darkening; surface textures realistically rotate across the sphere.
* **Watt-Dependent Rotation Speed:** Sun rotation speed scales in real time with solar power generation.
* **Peaceful Night Mode:** When power is 0 W, the sun dims to a quiet sleeping glow, the panel turns deep night blue, particles stop flowing, and the power readout dims to calm gray.