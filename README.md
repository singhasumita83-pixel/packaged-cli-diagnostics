# Packaged CLI Diagnostics Tool

A lightweight Python command-line tool that inspects a machine and produces both a human-readable report and structured JSON.

## Features

- Checks the running Python version.
- Checks disk usage for a selected path.
- Inspects environment-variable names with values redacted by default.
- Detects common developer tools such as Git, Node.js, npm, Java, GCC and VS Code.
- Supports an optional JSON configuration file.
- Produces JSON output for automation.
- Uses meaningful exit codes.
- Includes unit tests for success, missing dependency, and malformed configuration paths.

## Installation

### From a local clone

```bash
python -m pip install .
```

After installation, run:

```bash
diagnostics
```

You can also run the package without installing the console command:

```bash
python -m diagnostics
```

## Usage

Human-readable report:

```bash
diagnostics
```

JSON report:

```bash
diagnostics --json
```

Check a specific disk path:

```bash
diagnostics --path .
```

Use a configuration file:

```bash
diagnostics --config config/example.json
```

Show help:

```bash
diagnostics --help
```

## Configuration

Example:

```json
{
  "disk_path": ".",
  "developer_tools": ["git", "python", "node", "npm", "java", "gcc", "code"]
}
```

The configuration path must point to a valid JSON file. A malformed JSON file or invalid configuration structure produces a configuration error.

## Exit codes

- `0` - diagnostic completed successfully.
- `1` - diagnostic completed with one or more missing/unavailable dependencies or tools.
- `2` - invalid command-line argument or malformed configuration.
- `3` - unexpected diagnostic error.

## Security note

Environment-variable names are reported, but values are redacted by default. This prevents accidental disclosure of API keys, passwords, tokens, and other secrets in diagnostic reports.

## Example JSON

See `samples/sample_report.json`.

## Tests

Install pytest if it is not already available:

```bash
python -m pip install pytest
```

Run:

```bash
pytest
```
