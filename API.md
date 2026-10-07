# API Reference

## SwiftParserOSS

The main entry point for the library.

### Constructor

```javascript
const parser = new SwiftParserOSS(config);
```

**Parameters:**

- `config` (Object) [Optional]: Configuration object.
    - `enableLogging` (boolean): Default `true`.
    - `strictValidation` (boolean): Default `true`.

### Methods

#### `parse(message, format)`

Parses a message string.

- `message` (string): The raw message content.
- `format` (string) [Optional]: Specific format to use (e.g., 'MT103', 'ISO20022', 'BANCS_XML'). If omitted, auto-detection is attempted.
- **Returns**: `Object` - The standardized parsed message object.
- **Throws**: `Error` if parsing fails or format is unsupported.

#### `detectFormat(message)`

Attempts to detect the format of a message string.

- `message` (string): The raw message content.
- **Returns**: `string` - The detected format code (e.g., 'MT103', 'ISO20022') or 'UNKNOWN'.

#### `validate(message)`

Validates if a message is in a supported format.

- `message` (string): The raw message content.
- **Returns**: `boolean` - `true` if valid, `false` otherwise.

#### `getSupportedFormats()`

Returns a list of supported format codes.

- **Returns**: `Array<string>` - List of format strings.

## Specialized Parsers

Access specific parsers directly via properties on the main instance:

- `parser.swift`: Core SWIFT MT parser.
- `parser.iso20022`: ISO 20022 XML parser.
- `parser.bancs`: TCS BaNCS parser.
- `parser.fis`: FIS Systematics parser.
- `parser.fiserv`: Fiserv DNA parser.
- `parser.temenos`: Temenos T24 parser.
- `parser.enhanced`: Enhanced aggregator parser (delegates to others).
