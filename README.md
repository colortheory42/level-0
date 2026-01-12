# THE BACKROOMS

A procedurally generated 3D horror game engine built entirely in Python with Pygame. Features destructible environments, realistic debris physics, VHS camcorder aesthetics, and spatial audio.

![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Pygame](https://img.shields.io/badge/pygame-2.0+-green.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## 🎮 Features

### Core Gameplay
- **Infinite Procedural Generation**: Explore endlessly generating Backrooms with consistent seed-based generation
- **Destructible Environments**: Progressive wall damage system with pixel-perfect debris physics
- **First-Person Movement**: Smooth camera controls with walking, running, crouching, and jumping
- **VHS Aesthetic**: Authentic found-footage visual style with subtle effects

### Technical Highlights
- **Custom 3D Engine**: Built from mathematical first principles using only Pygame and NumPy
- **Advanced Physics**: Realistic debris with gravity, collision, and settling behaviors
- **Precision Collision**: Circle-vs-segment collision with sliding response for smooth movement
- **Spatial Audio**: Directional sound with stereo panning based on player orientation
- **Save/Load System**: Persistent game state with multiple save slots
- **Voice Echo System**: Optional microphone loopback for atmospheric voice effects

### World Generation
- **Procedural Zones**: Different zone types (normal, dense, sparse, maze, open) with unique characteristics
- **Smart Hallways**: Automatic doorway and corridor generation for navigable spaces
- **Pillar Variation**: Configurable pillar density modes from none to fully dense
- **Structural Physics**: Walls crack, lean, and fall realistically when destroyed

## 📋 Requirements

### Core Dependencies
```bash
pip install pygame numpy
```

### Optional Dependencies
For voice echo features:
```bash
pip install sounddevice  # Recommended
# OR
pip install pyaudio      # Alternative
```

## 🚀 Quick Start

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/the-backrooms.git
cd the-backrooms
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Run the game**
```bash
python main.py
```

## 🎮 Controls

### Movement
- **WASD** or **Arrow Keys**: Move
- **SHIFT**: Run
- **C**: Toggle crouch
- **SPACE**: Jump
- **M**: Toggle mouse look
- **J/L**: Turn left/right (when mouse look is off)

### Destruction
- **LEFT CLICK** or **E**: Damage/destroy wall (aim at center)
- Walls take multiple hits and show progressive damage
- Watch debris accumulate on the floor!

### System
- **H**: Toggle help overlay
- **R**: Toggle performance mode (render scale)
- **ESC**: Pause game
- **N**: Toggle voice loopback (requires microphone)

### Save/Load
- **F5**: Quick save to slot 1
- **F9**: Quick load from slot 1

## 🏗️ Architecture

The engine follows a clean modular architecture:

```
main.py              # Game loop and state management
engine.py            # Main orchestrator
├── world.py         # Procedural generation and geometry
├── player.py        # Player state and input
├── camera.py        # Camera transforms and projection
├── renderer.py      # 3D rendering pipeline
├── collision.py     # Precise collision detection
├── debris.py        # Physics simulation for destruction
└── audio.py         # Procedural sound generation
```

### Key Systems

**World System** (`world.py`)
- Seed-based procedural generation
- Wall and pillar management
- Destruction tracking
- Debris spawning

**Collision System** (`collision.py`)
- Circle collider vs line segments
- Multi-pass resolution for corners
- Sliding collision response
- Depenetration for stuck states

**Renderer** (`renderer.py`)
- Custom 3D projection
- Near-plane clipping
- Painter's algorithm depth sorting
- Dynamic lighting and fog

**Debris System** (`debris.py`)
- Pixel-sized debris particles
- Realistic physics with gravity
- Settling detection
- Rubble chunk formation

## ⚙️ Configuration

Edit `config.py` to customize:

```python
# Display
WIDTH = 960
HEIGHT = 540
FULLSCREEN = True
FPS = 60

# Pillar density modes
PILLAR_MODE = "normal"  # Options: none, sparse, normal, dense, all

# Movement speeds
WALK_SPEED = 75
RUN_SPEED = 100
CROUCH_SPEED = 10

# World generation
PILLAR_SPACING = 400
HALLWAY_WIDTH = 100
WALL_THICKNESS = 20
```

## 🎨 Customization

### Pillar Density
Change the `PILLAR_MODE` in `config.py`:
- `"none"`: Wide open spaces
- `"sparse"`: Occasional pillars (10%)
- `"normal"`: Balanced (30%)
- `"dense"`: Maze-like (60%)
- `"all"`: Grid of pillars (100%)

### Colors
Modify the color scheme in `config.py`:
```python
WALL_COLOR = (240, 220, 80)     # Yellow walls
FLOOR_COLOR = (30, 60, 120)     # Blue floor
CEILING_COLOR = (200, 200, 240) # Light ceiling
```

## 🔊 Audio Features

### Built-in Sounds
All sounds are procedurally generated at runtime:
- Ambient hum (low-frequency drone)
- Footsteps (player and ambient)
- Electrical buzz
- Wall destruction effects
- Crack and fracture sounds

### Voice Echo System
Optional microphone loopback with spatial audio:
```bash
# Install sounddevice (recommended)
pip install sounddevice

# Or pyaudio
pip install pyaudio
```

Press **N** in-game to toggle voice loopback.

## 💾 Save System

Saves are stored in JSON format in the `backrooms_saves/` directory:
- **F5**: Quick save to slot 1
- **F9**: Quick load from slot 1
- Saves include: player position, world seed, destroyed walls, play time

## 🎯 Design Philosophy

This engine is built on several core principles:

1. **Build from First Principles**: Everything is constructed from mathematical foundations rather than using high-level frameworks

2. **Emergent Behavior**: Simple rules create complex, realistic behavior (debris physics, procedural generation)

3. **Performance Through Simplicity**: Efficient algorithms over brute force (spatial partitioning, near-plane clipping)

4. **Durable Architecture**: Clean separation of concerns makes the codebase maintainable and extensible

## 🐛 Troubleshooting

### Audio Issues
If you encounter audio problems:
```bash
# Try sounddevice first
pip install sounddevice

# If that doesn't work, try pyaudio
pip install pyaudio

# Fallback: Test tone generator
# (automatically used if no microphone library found)
```

### Performance Issues
- Press **R** to toggle render scale (performance mode)
- Reduce `WIDTH` and `HEIGHT` in `config.py`
- Set `PILLAR_MODE = "sparse"` for open areas
- Disable fog: `FOG_ENABLED = False`

### Collision Problems
- Ensure `WALL_THICKNESS` is reasonable (10-30)
- Check `player_radius` in collision system (default: 15.0)
- Verify `PILLAR_SIZE` doesn't exceed `PILLAR_SPACING`

## 🚧 Future Enhancements

Planned features:
- [ ] Full raycast-based acoustic system
- [ ] Dynamic lighting with shadows
- [ ] Entities and NPCs
- [ ] Multiple floor levels
- [ ] Procedural textures
- [ ] Network multiplayer

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

Built with:
- Python 3.8+
- Pygame for rendering
- NumPy for math operations
- Mathematical foundations in 3D graphics
- Inspired by the Backrooms creepypasta

## 📧 Contact

For questions, suggestions, or bug reports, please open an issue on GitHub.

---

**Made with mathematical precision and creative chaos** 🎮

*"In the Backrooms, every wall is temporary."*
