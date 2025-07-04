# Yogi

🧘‍♂️ A personal development environment setup tool that builds software from source and manages configuration files.

## Overview

Yogi is a modular development environment setup tool designed to:
- Build and install software from source (currently Neovim v0.10.1)
- Deploy configuration files for development tools
- Provide a scriptable, extensible framework for environment setup
- Support dry-run mode for testing changes

## Features

- **🔧 Source Building**: Automatically clone, build, and install software from source
- **📁 Configuration Management**: Deploy dotfiles and configuration files to appropriate locations
- **🔀 Modular Scripts**: Add custom setup scripts to the `runs/` directory
- **🧪 Dry Run Mode**: Test your setup scripts without making actual changes
- **🎯 Selective Execution**: Run specific scripts using name filtering

## Project Structure

```
yogi/
├── dev-env              # Script to deploy configuration files
├── run                  # Script to execute all setup scripts
├── runs/                # Directory containing modular setup scripts
│   └── neovim          # Script to build and install Neovim from source
├── .config/            # Configuration files to be deployed
│   ├── nvim/           # Neovim configuration
│   │   └── init.lua
│   └── tmux/           # tmux configuration
│       └── tmux.conf
└── neovim/             # Cloned Neovim repository (created during setup)
```

## Installation

```bash
git clone https://github.com/yourusername/yogi.git
cd yogi
```

## Usage

### Deploy Configuration Files

Deploy your configuration files to `$HOME/.config/`:

```bash
./dev-env
```

**Dry run mode** (see what would be copied without making changes):
```bash
./dev-env --dry
```

### Run All Setup Scripts

Execute all scripts in the `runs/` directory:

```bash
./run
```

**Dry run mode**:
```bash
./run --dry
```

**Run specific scripts** (filter by name):
```bash
./run neovim
```

### Current Setup Scripts

- **`runs/neovim`**: Clones Neovim v0.10.1, installs dependencies via Homebrew, builds from source, and installs system-wide

## Configuration Files

The `.config/` directory contains:
- **`nvim/init.lua`**: Neovim configuration
- **`tmux/tmux.conf`**: tmux configuration

These files are deployed to `$HOME/.config/` when you run `./dev-env`.

## Adding New Setup Scripts

To add a new setup script:

1. Create an executable script in the `runs/` directory
2. Make it executable: `chmod +x runs/your-script`
3. Run `./run` to execute all scripts, or `./run your-script` to run just yours

## Dependencies

- **macOS**: Uses Homebrew for package management
- **Bash**: All scripts are written in Bash
- **Git**: For cloning repositories

## Examples

**Complete environment setup:**
```bash
# Deploy configuration files
./dev-env

# Install and build all software
./run
```

**Test your setup without making changes:**
```bash
./dev-env --dry
./run --dry
```

**Install only Neovim:**
```bash
./run neovim
```

## Contributing

Feel free to:
- Add new setup scripts to the `runs/` directory
- Contribute additional configuration files to `.config/`
- Improve existing scripts
- Add support for other operating systems

## License

This project is licensed under the MIT License.

## Contact

For questions or support, contact [your.email@example.com].
