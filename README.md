# IsaacLab Pixi

A reproducible development environment for [NVIDIA Isaac Lab](https://github.com/isaac-sim/IsaacLab) using the [Pixi](https://pixi.sh) package manager.

## Overview

This repository provides a streamlined setup for Isaac Sim and Isaac Lab using Pixi, ensuring consistent and reproducible Python environments across different machines.

## Prerequisites

- **Operating System**: Ubuntu 22.04+ (requires glibc 2.35+)
- **GPU**: NVIDIA GPU with CUDA support
- **Pixi**: [Install Pixi](https://pixi.sh/latest/#installation)
- **Git**: For cloning repositories

Check your glibc version:
```bash
ldd --version
```

## Installation

### 1. Clone this repository
```bash
git clone https://github.com/AtharvaBhorpe/isaaclab-pixi.git
cd isaaclab-pixi
```

### 2. Install all dependencies
```bash
pixi install
pixi run setup
```

This will:
- Install PyTorch with CUDA 12.8 support
- Install Isaac Sim 5.1.0
- Clone Isaac Lab
- Install Isaac Lab in development mode

### 3. Accept EULA
On first run, you'll need to accept the NVIDIA Omniverse EULA.

## Usage

### Running Isaac Lab Demos
```bash

# List available demos
pixi run lab-list-demos

# Robotic arm manipulation
pixi run lab-arms

# Quadruped locomotion
pixi run lab-quadrupeds

# Classic cartpole RL environment
pixi run lab-cartpole
```

### Launching Isaac Sim
```bash
# Launch Isaac Sim GUI
pixi run isaac-sim
```

### Development
```bash
# Activate the pixi environment
pixi shell

# Run custom scripts
cd IsaacLab
python scripts/demos/your_script.py
```

### Available Tasks

View all available pixi tasks:
```bash
pixi task list
```

## Project Structure
```
isaaclab-pixi/
├── pixi.toml              # Pixi configuration and tasks
├── pixi.lock              # Locked dependencies for reproducibility
├── IsaacLab/              # Isaac Lab repository (cloned during setup)
└── README.md
```

## Configuration

The main configuration is in `pixi.toml`:

- **Python version**: 3.11
- **PyTorch**: 2.7.0 with CUDA 12.8
- **Isaac Sim**: 5.1.0
- **Platform**: Linux x86_64

## Troubleshooting

### Module 'isaaclab' not found
```bash
pixi run setup  # Re-run setup to ensure Isaac Lab is installed
```

### CUDA not available
Verify CUDA installation:
```bash
pixi shell
python -c "import torch; print(torch.cuda.is_available())"
```

### Git command not found
Pixi includes git as a dependency. If you see this error, run:
```bash
pixi install
```

### glibc version too old
Isaac Sim requires glibc 2.35+. Upgrade to Ubuntu 22.04+ or use a Docker container.

## Learning Resources

- [Isaac Lab Documentation](https://isaac-sim.github.io/IsaacLab/)
- [Isaac Sim Documentation](https://docs.omniverse.nvidia.com/isaacsim/latest/)
- [Pixi Documentation](https://pixi.sh/latest/)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [NVIDIA Isaac Lab](https://github.com/isaac-sim/IsaacLab) - The robotics simulation framework
- [Pixi](https://pixi.sh) - Fast, cross-platform package manager
- [PyTorch](https://pytorch.org/) - Deep learning framework

## Related Projects

- [Isaac Lab](https://github.com/isaac-sim/IsaacLab)
- [Isaac Sim](https://developer.nvidia.com/isaac-sim)

## Support

For issues related to:
- **This setup**: Open an issue in this repository
- **Isaac Lab**: Visit [Isaac Lab Issues](https://github.com/isaac-sim/IsaacLab/issues)
- **Isaac Sim**: Visit [NVIDIA Forums](https://forums.developer.nvidia.com/c/omniverse/simulation/69)
