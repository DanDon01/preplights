# 🍽️ PrepLights

**Smart, reactive kitchen lighting powered by ESP32, sensors, and thermal vision.**

PrepLights is a modular, sci-fi-inspired lighting system that responds to your presence, your appliances, and your cooking flow. Built with ESPHome, Raspberry Pi, and addressable LED strips, it turns your kitchen into a high-functioning interactive workspace.

---

## 🚀 Features

* **Zone-based motion tracking** using VL53L0X ToF sensors
* **Heat-reactive glow** above kettle using MLX90640 thermal camera
* **Slow cooker countdown timer LED bar**
* **Food-prep zones that react to motion or match the food’s colour**
* **Ambient sync lighting across all under-cabinet sections**
* **Modular ESP32 nodes for each kitchen segment**
* **MQTT & Home Assistant integration**
* **Wi-Fi OTA updates + Web dashboard**

---

## 🧠 Architecture

```text
+----------------------------+
|      Linux Dev Machine     |  <- Code, flash, MQTT, Home Assistant
+----------------------------+
            |
     [ESPHome via USB/Wi-Fi]
            |
     +--------------------+
     |      ESP32 DevKit  |  <- Main node for LED + motion
     +--------------------+
      |       |       |
      |   [TCA9548A]    |
      |       |       |
  [VL53L0X] [LED Strip] [...]

Other Nodes:
- ESP32 (Zone nodes)
- Raspberry Pi (thermal + food vision)
- PyPortal (UI controller)
```

---

## 📦 Hardware

| Component                     | Purpose                       |
| ----------------------------- | ----------------------------- |
| ESP32 DevKit + screw terminal | Core controller board         |
| VL53L0X ToF Sensors (x20)     | Motion tracking per zone      |
| TCA9548A Multiplexer (x3)     | Expand I2C bus for sensors    |
| WS2812B/SK6812 LED Strips     | Addressable lighting          |
| MLX90640 Thermal Camera       | Kettle heat tracking          |
| PIR / IR Sensors              | Secondary motion trigger      |
| Raspberry Pi Zero/3           | MQTT + thermal data processor |
| Logic Level Shifters          | 3.3V ↔ 5V conversion          |
| 5V 10A PSU                    | Power LEDs                    |

---

## ⚙️ Setup

1. Install ESPHome on your Linux machine using pipx or a venv
2. Clone this repo:

   ```bash
   git clone https://github.com/youruser/preplights.git
   cd preplights
   ```
3. Flash an ESP32 with the starter config:

   ```bash
   esphome run preplights.yaml
   ```
4. Connect it to Wi-Fi and access it over ESPHome or HA
5. Expand zone configs as hardware arrives

---

## 🧪 Zones Breakdown

| Zone                 | Purpose         | Features                      |
| -------------------- | --------------- | ----------------------------- |
| Long Run (2.3m)      | Main prep area  | ToF tracking + LED reaction   |
| Microwave Zone       | Appliance area  | Ambient light only            |
| Speaker Zone         | Music side      | Audio-reactive mode (future)  |
| Middle (Slow Cooker) | Cooking + timer | 4hr LED timer bar             |
| Kettle Zone          | Heat glow zone  | MLX90640 thermal mapping      |
| Small Prep Zone      | Quick chopping  | Motion trigger or food colour |

---

## 📡 Integrations

* **Home Assistant**

  * Scene switching
  * Automation triggers
* **MQTT**

  * Sensor data broadcast
  * Remote control
* **ESPHome OTA**

  * Update ESPs wirelessly
* **Optional: WLED** for synced ambient lighting in non-tracking zones

---

## 🔧 Roadmap

* [x] ESP32 + LED prototype
* [x] MQTT + HA integration
* [ ] VL53L0X tracking logic
* [ ] Thermal cam live feedback
* [ ] PyPortal control interface
* [ ] Node-RED automations

---

## 🧠 Author

**@AI_TechnoKing**
Engineer, hacker, kitchen technomancer.

---

> "It's not just a kitchen anymore. It's a lighting experiment with snacks."

---

## 📸 Gallery (Coming Soon)

* [ ] Thermal kettle effect
* [ ] Prep zone in motion
* [ ] Full zone sync at night

---

## ⭐ Like what you see?

Drop a star and follow the project for updates. Or build your own PrepLights setup and give it a twist.
