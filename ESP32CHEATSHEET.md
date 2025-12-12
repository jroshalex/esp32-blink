# 📘 ESP-IDF Command Reference (VS Code + idf.py)

---

# 🧰 **1. Common ESP-IDF Commands**

### Build the project

```bash
idf.py build
```

### Flash firmware to the ESP32

```bash
idf.py -p PORT flash
```

Example (Windows):

```bash
idf.py -p COM3 flash
```

Example (Linux/macOS):

```bash
idf.py -p /dev/ttyUSB0 flash
```

### Flash & Monitor (most common)

```bash
idf.py -p PORT flash monitor
```

---

# 🖥️ **2. Serial Monitor**

### Start monitor

```bash
idf.py monitor
```

### Exit monitor

(VERY important for ESP-IDF)

```
Ctrl + ]
```

### Restart monitor after exit

```bash
idf.py monitor
```

### Set monitor baud rate (default = 115200)

```bash
idf.py monitor -b 115200
```

---

# 🔧 **3. Device Ports**

### List all connected serial devices

```bash
idf.py --list-ports
```

### Set a default port (saves time)

```bash
idf.py set-target esp32
idf.py -p COM3
```

---

# ⚙️ **4. Menuconfig (Project Configuration UI)**

### Open Menuconfig

```bash
idf.py menuconfig
```

### Change ESP-IDF target (esp32 / esp32s3 / etc.)

```bash
idf.py set-target esp32
```

---

# 🧹 **5. Cleaning Commands**

### Clean compiled files

(Removes `/build`, but keeps sdkconfig)

```bash
idf.py clean
```

### Clean EVERYTHING

(Restores project to a nearly fresh state)

```bash
idf.py fullclean
```

### Erase the entire flash chip

(Useful when switching projects or fixing corrupted flash)

```bash
idf.py erase-flash
```

---

# 🧪 **6. Flash Partition & Bootloader Only**

Sometimes you only want to flash a specific component:

### Flash bootloader only

```bash
idf.py bootloader
idf.py flash-bootloader
```

### Flash partition table only

```bash
idf.py partition_table
idf.py flash-partition_table
```

### Flash app only

```bash
idf.py app
idf.py flash-app
```

---

# 🐛 **7. Debugging (VS Code)**

### Start debugging session

(using the ESP-IDF extension)

* Press **F5**
* Or click the green **Run and Debug** button

### Stop debugging

* Click the **red Stop ⛔ button**

---

# 📂 **8. ESP-IDF Project Structure**

```
project/
│
├── main/
│   ├── main.c / main.cpp
│   └── CMakeLists.txt
│
├── components/          # Optional custom libraries
├── build/               # Auto-generated
├── sdkconfig            # Saved project config
├── CMakeLists.txt       # Project definition
└── README.md
```

---

# 📡 **9. Logging in ESP-IDF**

Use ESP-IDF logging instead of printf:

```c
#include "esp_log.h"

static const char *TAG = "APP";

ESP_LOGI(TAG, "Info message");
ESP_LOGW(TAG, "Warning!");
ESP_LOGE(TAG, "Error happened");
```

### Change log level globally

```bash
idf.py menuconfig
 → Component Config
   → Log output
```

---

# 🔄 **10. Reset & Restart**

### Soft reboot ESP32 from code

```c
esp_restart();
```

### Hardware reset

Press the **EN / RESET button** on your board.

---

# 🌐 **11. Wi-Fi / BLE Examples**

List examples installed on your machine:

```bash
idf.py example list
```

Or browse:

```
vscode → ESP-IDF: Show Examples
```

---

# 🔗 **12. Useful Extras**

### Check IDF version

```bash
idf.py --version
```

### Reconfigure tools after environment issues

```bash
idf.py doctor
```

### Create a new project

```bash
idf.py create-project my_project
```

---

# 📖 Quick Cheat Sheet

| Action                  | Command                        |
| ----------------------- | ------------------------------ |
| Build                   | `idf.py build`                 |
| Flash                   | `idf.py -p PORT flash`         |
| Monitor                 | `idf.py monitor`               |
| Exit monitor            | `Ctrl + ]`                     |
| Build + flash + monitor | `idf.py -p PORT flash monitor` |
| Menuconfig              | `idf.py menuconfig`            |
| Set target              | `idf.py set-target esp32`      |
| Clean                   | `idf.py clean`                 |
| Full clean              | `idf.py fullclean`             |
| Erase flash             | `idf.py erase-flash`           |

