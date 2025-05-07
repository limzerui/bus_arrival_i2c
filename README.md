# Bus Arrival OLED Display for Raspberry Pi

I made this project to help make it easier to check bus timings in the morning. Things are always rushed, and my dad depends on the bus to get around. I thought it’d be cool to do something useful with a Raspberry Pi and a small I2C display—just a simple screen to show when the next buses are coming.

## Hardware Requirements

- Raspberry Pi (any model with I2C pins)
- SSD1306 OLED display (128x64 pixels)
- Jumper wires

## Software Setup

1. Enable I2C on Raspberry Pi:
   ```bash
   sudo raspi-config
   ```
   Navigate to Interface Options > I2C and enable it.

2. Update packages and install required system dependencies:
   ```bash
   sudo apt-get update
   sudo apt-get install -y python3-pip python3-pil i2c-tools python3-smbus
   ```

3. Check if the OLED display is detected:
   ```bash
   sudo i2cdetect -y 1
   ```
   You should see a device at address 0x3C (or possibly 0x3D).

4. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Running the Bus Arrival Display

1. Make the script executable:
   ```bash
   chmod +x oled_bus_display.py
   ```

2. Run the display script:
   ```bash
   ./oled_bus_display.py
   ```
## Customization

- Edit `BUS_STOP_CODE` in the script to monitor a different bus stop.

## Troubleshooting

1. If the display doesn't show anything:
   - Check your wiring connections.
   - Verify the I2C address with `sudo i2cdetect -y 1`.
   - Ensure I2C is enabled with `sudo raspi-config`.

2. If bus data isn't appearing:
   - Check your internet connection.
   - Verify the LTA API credentials and bus stop code.
