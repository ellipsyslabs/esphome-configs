# EllipsysLabs Switch 4C

Welcome to the official repository for the **EllipsysLabs Switch 4C**, a fully offline-capable, 4-channel smart switch built natively for Home Assistant and ESPHome. 

Designed with zero cloud dependency, the Switch 4C gives you complete local control over your lighting and appliances, ensuring your smart home remains private, fast, and reliable.

## Features
* **4-Channel Relay Control:** Independently control up to four distinct circuits.
* **Physical Switch Support:** Connect up to four standard wall switches. The state-based toggling ensures your physical switches always work seamlessly with digital commands.
* **100% Local Control:** No cloud accounts, no external servers, and instant response times.
* **Zero-Touch Provisioning:** Seamless adoption into Home Assistant via Improv Wi-Fi and mDNS discovery.
* **Hardware Factory Reset:** Dedicated physical reset pin to clear Wi-Fi credentials safely.

---

## Wiring Guide

The Switch 4C is powered by the ESP32-C3 microcontroller. If you are wiring the board yourself or connecting external switches, please follow the pinout below:

### Relays (Outputs)
* **Relay 1:** `GPIO0`
* **Relay 2:** `GPIO1`
* **Relay 3:** `GPIO3`
* **Relay 4:** `GPIO4`

### Physical Switches (Inputs)
Wire your physical wall switches between the following GPIO pins and **Ground (GND)**. The internal pull-up resistors are already configured in the firmware.
* **Switch 1:** `GPIO5`
* **Switch 2:** `GPIO6`
* **Switch 3:** `GPIO7`
* **Switch 4:** `GPIO10`

### System
* **Factory Reset:** `GPIO21` (Connect to Ground for 5 seconds to wipe credentials).

---

## Installation & Adoption

Getting the Switch 4C onto your network and into Home Assistant takes less than two minutes.

### 1. Connect to Wi-Fi
1. Power on the EllipsysLabs Switch 4C.
2. Open the Wi-Fi settings on your phone or computer and look for a new network called **"Switch 4C Setup"**.
3. Connect to this network. A captive portal will automatically pop up.
4. Select your home Wi-Fi network from the list, enter your password, and click **Save**.
5. The device will reboot and connect to your home network.

### 2. Adopt in Home Assistant
Because the Switch 4C is built for ESPHome, Home Assistant will automatically discover it on your network.
1. Open your **Home Assistant** dashboard.
2. Navigate to **Settings** > **Devices & Services**.
3. You will see the Switch 4C under the "Discovered" section. Click **Configure**.
4. Open your **ESPHome Add-on** dashboard. You will see the new device with an **Adopt** button.
5. Click **Adopt**. Home Assistant will securely generate a unique API key, download the latest official configuration from this repository, and finalize the setup.

---

## Troubleshooting

### How do I factory reset the device?
If you change your Wi-Fi router or password, you will need to clear the old credentials from the device.
1. Ensure the device is powered on.
2. Use a jumper wire or button to connect **GPIO21** to **Ground (GND)**.
3. Hold the connection for exactly **5 seconds**.
4. The device will wipe all saved networks, restart, and begin broadcasting the **"Switch 4C Setup"** network again.
