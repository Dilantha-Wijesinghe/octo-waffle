# Octo Waffle CLI

```
                        ___
                     .-'   `'.
                    /         \
                    |         ;
                    |         |           ___.--,
           _.._     |0) ~ (0) |    _.---'`__.-( (_.
    __.--'`_.. '.__.\    '--. \_.-' ,.--'`     `""`
   ( ,.--'`   ',__ /./;   ;, '.__.'`    __
   _`) )  .---.__.' / |   |\   \__..--""  """--.,_
  `---' .'.''-._.-'`_./  /\ '.  \ _.-~~~````~~~-._`-.__.'
        | |  .' _.-' |  |  \  \  '.               `~---`
         \ \/ .'     \  \   '. '-._)
          \/ /        \  \    `=.__`~-.
          / /\         `) )    / / `"".`\
    , _.-'.'\ \        / /    ( (     / /
     `--~`   ) )    .-'.'      '.'.  | (
            (/`    ( (`          ) )  '-;
             `      '-;         (-'
```


A colorful directory listing tool written in Rust that provides elegant file system navigation with both table and JSON output formats.

## Features

- **Colorful table output**: Beautiful styled tables with rounded borders and color-coded columns
- **JSON export**: Machine-readable JSON output for scripting and automation
- **File metadata**: Display file sizes, types, and modification dates
- **Cross-platform**: Works on Windows, macOS, and Linux
- **Zero configuration**: Works out of the box with sensible defaults

## Installation

### Prerequisites
- Rust and Cargo installed ([Install Rust](https://rustup.rs/))

### Build from source
```bash
git clone https://github.com/Dilantha-Wijesinghe/octo-waffle.git
cd octo-waffle
cargo build --release
```

## Usage

### Basic Commands

```bash
# Build the project
cargo build

# Quick syntax check
cargo check

# List current directory contents
cargo run

# List specific directory
cargo run -- /path/to/directory

# Output as JSON
cargo run -- --json

# List specific directory with JSON output
cargo run -- /path/to/directory --json

# Show help
cargo run -- -h
```

### Examples

```bash
# List current directory (default behavior)
cargo run

# List home directory
cargo run -- ~

# List root directory
cargo run -- /

# Get JSON output for scripting
cargo run -- --json

# List Documents folder with JSON output
cargo run -- ~/Documents --json

# Show help message
cargo run -- -h
```

## How It Works

The tool uses a simple but effective approach:

1. **Path Resolution**: Accepts optional path argument (defaults to current directory)
2. **Directory Reading**: Safely reads directory contents using standard library
3. **Metadata Extraction**: Gathers file size, type, and modification date for each entry
4. **Output Formatting**: Presents data in either a styled table or JSON format

## Command Line Options

- `<path>`: Directory path to list (optional, defaults to current directory)
- `--json, -j`: Output results in JSON format instead of table
- `--help, -h`: Show help information
- `--version, -V`: Show version information

## Output Format

### Table Mode (Default)
- **Name**: File or directory name (bright cyan)
- **Type**: File or Dir (bright magenta)
- **Size B**: File size in bytes (bright yellow)
- **Modified**: Last modification date (default color)
- Header row highlighted in bright green

### JSON Mode
```json
[
  {
    "name": "example.txt",
    "e_type": "File",
    "len_bytes": 1024,
    "modified": "Wed Jan 15 2025"
  }
]
```

## Development

### Code Structure

- `src/main.rs`: Main application logic and entry point
- `Cli` struct: Command-line argument parsing using `clap`
- `FileEntry` struct: Data structure for file/directory information
- `EntryType` enum: File vs Directory classification
- `get_files()`: Core directory reading functionality
- `print_table()`: Styled table output formatting

### Development Commands

```bash
# Format code
cargo fmt

# Run linter
cargo clippy

# Run tests
cargo test

# Clean build artifacts
cargo clean
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run `cargo fmt` and `cargo clippy`
5. Submit a pull request

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Dependencies

- `clap` - Command-line argument parsing
- `owo-colors` - Terminal color support
- `tabled` - Table formatting and styling
- `chrono` - Date and time formatting
- `serde` + `serde_json` - JSON serialization
- `strum` - Enum utilities
