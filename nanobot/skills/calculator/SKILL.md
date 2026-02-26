---
name: calculator
description: "Perform mathematical calculations. Use this when you need to do arithmetic, algebra, or other math operations."
metadata: {"nanobot":{"emoji":"🔢","requires":{"bins":[]},"always":true}}
---

# Calculator Skill

Use this skill to perform mathematical calculations and conversions.

## Basic Arithmetic

When asked to calculate something, use the shell tool with `node -e` or Python:

```bash
# Using Node.js
node -e "console.log(2 + 2)"
node -e "console.log(Math.sqrt(16))"
node -e "console.log(Math.PI * 10)"

# Using Python (if available)
python -c "print(2 ** 10)"
python -c "import math; print(math.sin(math.pi/2))"
```

## Unit Conversions

For unit conversions, you can use online tools or calculate manually:

- Temperature: F to C = (F - 32) * 5/9
- Length: 1 inch = 2.54 cm
- Weight: 1 lb = 0.453592 kg

## Examples

User: "What is 15% of 200?"
```bash
node -e "console.log(200 * 0.15)"
```

User: "Convert 100 Fahrenheit to Celsius"
```bash
node -e "console.log((100 - 32) * 5/9)"
```

User: "Calculate the area of a circle with radius 5"
```bash
node -e "console.log(Math.PI * 5 * 5)"
```

## Notes

- Always verify complex calculations
- For financial calculations, be precise with decimal places
- Use appropriate precision for the context
