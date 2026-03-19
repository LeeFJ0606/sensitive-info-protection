# sensitive-info-protection

A general-purpose sensitive information real-time protection Skill for OpenClaw. Automatically detects, alerts, and handles sensitive data in user interactions.

## Features

- **Real-time detection** - Scans text for multiple types of sensitive information
- **Custom rules** - Add your own detection rules with regex patterns
- **Interactive processing** - Standard output format with operation options
- **Desensitization** - One-click replacement of sensitive content
- **Built-in rules** for common sensitive types:
  - API Keys & tokens (OpenAI, GitHub, AWS)
  - Credit card, bank card numbers
  - Chinese ID card, phone numbers
  - Emails, passwords, secrets

## Installation

In OpenClaw:
```
clawhub install sensitive-info-protection
```

Or clone to your skills directory:
```
git clone <repo> /path/to/sensitive-info-protection
```

## Quick Start

### Python API

```python
from scripts.detector import SensitiveDetector

detector = SensitiveDetector()
result = detector.scan("My API key is sk-1234567890abcdef1234567890abcdef1234567890abcdef")

if result.has_sensitive:
    print(result.to_markdown())
    # Get desensitized text
    clean = detector.desensitize(result.content)
    print("\nDesensitized:")
    print(clean)
```

### CLI

```bash
# Scan a file
python scripts/cli.py /path/to/file.txt

# Desensitize and output
python scripts/cli.py --desensitize /path/to/file.txt
```

## Documentation

- [Configuration Guide](references/configuration.md)
- [API Documentation](references/api.md)

## Structure

```
sensitive-info-protection/
├── SKILL.md                 # Skill definition for OpenClaw
├── scripts/
│   ├── detector.py          # Main detection engine
│   ├── models.py            # Data models
│   ├── cli.py               # Command-line interface
│   └── default_rules.json   # Built-in detection rules
├── references/
│   ├── configuration.md     # Configuration guide
│   └── api.md               # API documentation
├── assets/
│   └── default_config.json  # Default settings template
└── tests/
    └── test_basic.py        # Basic functionality tests
```

## License

MIT
