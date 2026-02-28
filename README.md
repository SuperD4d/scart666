Raspberry Pi SCART 6-6-6 RGB for PAL CRT TVs

This project demonstrates how to output high-quality PAL RGB video from a Raspberry Pi GPIO to a CRT TV via SCART using a 6-6-6 bit per color scheme.

Overview

The Raspberry Pi GPIOs are digital-only (0V or 3.3V). To generate analog RGB signals suitable for a CRT, we use a 6-bit-per-color resistor network, producing 64 levels per color. This allows for 262,144 possible colors (64×64×64) with a smooth gradient for each channel.

Resistor Network

Each color channel (Red, Green, Blue) uses 6 GPIO pins connected through resistors with weights proportional to their significance:

Bit	Resistance (Ω)	Weight
b5 (MSB)	500	Highest
b4	1k	
b3	2k	
b2	4k	
b1	8k	
b0 (LSB)	16k	Lowest

The resistor network sums the contributions of each active bit to generate an analog voltage for each color. The MSB passes more current, producing a higher voltage contribution, while the LSB passes much less.

Voltage Levels

The GPIO outputs 3.3V digital signals.

The resistor network converts these to approximately 0–1V per color channel, suitable for SCART input.

This ensures a nearly linear scale across all 64 intensity levels, providing smooth color gradients on a CRT.

Sync and PAL Compatibility

Horizontal sync (HSYNC) is connected directly to the CRT to maintain PAL timing.

No additional buffers are required for short SCART cables (<2 meters).

This configuration produces a high-fidelity PAL image using Raspberry Pi GPIOs without external DACs.

Summary

Digital to analog conversion via weighted resistor network

6-bit per color (6-6-6 RGB) → 64 levels per channel

0–1V analog output for SCART RGB

Direct HSYNC connection for PAL CRT TVs

Over 260,000 colors achievable with this setup

This design is suitable for retro gaming and other projects where accurate RGB output to a PAL CRT is required.
