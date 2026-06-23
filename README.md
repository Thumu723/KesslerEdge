# KesslerEdge v2.5

KesslerEdge is an interactive 3D orbital debris tracking and collision-avoidance simulation built from scratch for the Hack Club Stardance Challenge. It simulates a satellite navigating a high-density, low-Earth-orbit (LEO) environment cluttered with dangerous space junk, visualizing the compounding threats of Kessler syndrome.

## Technical Architecture

* **Deterministic Orbital Propagation:** Abandoned basic linear bounce vectors for true orbital mechanics. All 3,500 independent pieces of debris are tracked using fixed radii, orbital speeds, inclinations, and azimuths on individual 2D planes, continuously mapped to 3D Cartesian coordinates.
* **Post-Processing Pipeline:** Built a high-performance graphics stack using Three.js `EffectComposer`, `RenderPass`, and `UnrealBloomPass`. A tight luminosity threshold isolates lighting emission, forcing the GPU to calculate real-world optical bloom and atmospheric glare exclusively on the holographic wireframe Earth and tracking particles.
* **Frame-Rate Independence:** Integrated `THREE.Clock()` delta tracking across the execution loop. Positional updates, kinetic drift, and automated fuel burn metrics run at identical speeds regardless of hardware presentation layer (60Hz vs 144Hz monitors).
* **Autonomous Evasion State Machine:** Features an isolated kinematic loop where the satellite automatically tracks debris crossing a critical threshold radius ($<1.8$ units). The automated engine triggers a separate positioning offset rather than fighting manual input variables directly.
* **Gritty Terminal UI:** Clean, raw terminal aesthetic styled via `Courier New` with a matrix green/white high-contrast theme. Refactored completely away from fragile DOM index selections to explicit element ID binding.

## Interactive Controls

* **Up / Down Arrow Keys:** Manually override altitude vectors to dodge oncoming clusters.
* **Fuel Dynamics:** Both manual thrusting and autonomous evasion burn through a finite Fuel Bank (100%), creating a high-stakes survival loop.

## Development Setup

Simply clone the repository and run `index.html` directly in any standard, modern web browser supporting WebGL:

```bash
git clone [https://github.com/Thumu723/KesslerEdge.git](https://github.com/Thumu723/KesslerEdge.git)
cd KesslerEdge
# Open index.html in your browser
