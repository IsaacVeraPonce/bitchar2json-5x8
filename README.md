# bitchar2json-5x8

A comprehensive collection of 5x8 pixel matrix character definitions for use in displays, LED matrices, and custom rendering applications.

## Overview

bitchar2json-5x8 provides a standardized JSON format for representing characters as 5x8 pixel matrices. Each character is defined as an array of 8 rows, with each row containing 5 binary values (0 or 1) that represent the pixel state (off or on). This format is particularly useful for:

- LCD displays
- LED matrix modules
- Custom displays and signage
- Retro-style game development
- Microcontroller-based text rendering
- Arduino projects

## Character Set

The library includes:

- Full ASCII character set (uppercase and lowercase letters)
- Numbers and punctuation
- Extended Latin characters with accents (á, é, í, ó, ú, ñ, ü, etc.)
- Mathematical symbols (±, ×, ÷, √, ∞, ≈, etc.)
- Currency symbols (€, £, $)
- Greek letters (α, β, γ, δ, Ω, µ)
- Special symbols and shapes (arrows, boxes, hearts, etc.)
- Emoticons and special characters

## Usage

### Basic Implementation

```javascript
// Import the character definitions
const chars = require('bitchar2json-5x8');

// Get a specific character matrix
const letterA = chars['A'];

// Render the character (example)
function renderCharacter(charMatrix) {
  for (let row of charMatrix) {
    let line = '';
    for (let pixel of row) {
      line += pixel ? '█' : ' ';
    }
    console.log(line);
  }
}

renderCharacter(letterA);
```

Output:
```
 ███ 
█   █
█   █
█████
█   █
█   █
█   █
     
```

### Arduino Example

```cpp
#include <LedControl.h>

// Define pins for the LED matrix
LedControl lc = LedControl(12, 11, 10, 1);

// Function to display a character on the LED matrix
void displayChar(byte charMatrix[8]) {
  for (int row = 0; row < 8; row++) {
    lc.setRow(0, row, charMatrix[row]);
  }
}

void setup() {
  lc.shutdown(0, false);
  lc.setIntensity(0, 8);
  lc.clearDisplay(0);
  
  // Example: Display letter 'A'
  byte letterA[8] = {
    B01110,
    B10001,
    B10001,
    B11111,
    B10001,
    B10001,
    B10001,
    B00000
  };
  
  displayChar(letterA);
}

void loop() {
  // Your code here
}
```

## Integration

### Web Projects

```html
<script src="./bitchar2json-5x8.min.js"></script>
<script>
  // Character set is now available as a global variable
  const myChar = bitchar2json['A'];
  
  // Use the character matrix in your project
  // ...
</script>
```

### Node.js Projects

```bash
npm install bitchar2json-5x8
```

```javascript
const BitChar = require('bitchar2json-5x8');

// Use the character matrices in your project
const greeting = "HELLO";
const matrices = greeting.split('').map(char => BitChar[char]);
```

## Custom Character Creation

You can create your own custom characters following the same 5x8 format:

```javascript
const myCustomChar = [
  [0, 1, 1, 1, 0],
  [1, 0, 0, 0, 1],
  [1, 0, 1, 0, 1],
  [1, 0, 0, 0, 1],
  [1, 0, 0, 0, 1],
  [1, 1, 0, 1, 1],
  [1, 0, 1, 0, 1],
  [0, 0, 0, 0, 0]
];

// Add to the existing character set
bitchar2json['myChar'] = myCustomChar;
```

## Pixel Format

Each character is represented as an 8-row array, with each row containing 5 values:

```javascript
[
  [0, 1, 1, 1, 0], // Row 1
  [1, 0, 0, 0, 1], // Row 2
  [1, 0, 0, 0, 1], // Row 3
  [1, 1, 1, 1, 1], // Row 4
  [1, 0, 0, 0, 1], // Row 5
  [1, 0, 0, 0, 1], // Row 6
  [1, 0, 0, 0, 1], // Row 7
  [0, 0, 0, 0, 0]  // Row 8
]
```

Where:
- `0` represents an off pixel (background)
- `1` represents an on pixel (foreground)

## Contributing

Contributions are welcome! If you'd like to add new characters or improve existing ones:

1. Fork the repository
2. Create your feature branch (`git checkout -b IsaacVeraPonce/bitchar2json-5x8`)
3. Commit your changes (`git commit -m 'Add some amazing character'`)
4. Push to the branch (`git push origin IsaacVeraPonce/bitchar2json-5x8`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.

## Acknowledgments

- Special thanks to all contributors who have helped expand the character set
- Inspired by LCD and LED matrix display projects in the maker community

---

Made with ♥ for the creative coding and maker community.
