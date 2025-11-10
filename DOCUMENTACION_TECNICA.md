# 📚 Documentación Técnica - Sistemas IoT ESP32

Detalles técnicos completos de los 3 proyectos.

---

## 🏗️ Arquitectura General

```
┌─────────────────┐
│   App Flutter   │ ← Interfaz de usuario
└────────┬────────┘
         │ WiFi (TCP/IP)
         │ Puerto 8080
┌────────▼────────┐
│     ESP32       │ ← Microcontrolador
└────────┬────────┘
         │ I2C / Analógico
┌────────▼────────┐
│    Sensores     │ ← Hardware
└─────────────────┘
```

---

## 🔌 Protocolo de Comunicación

### Conexión TCP/IP
- **Puerto:** 8080
- **Formato:** Comandos de texto + JSON
- **Timeout:** 3 segundos
- **Encoding:** UTF-8

### Comandos Comunes

| Comando | Respuesta | Descripción |
|---------|-----------|-------------|
| `GET_STATUS` | JSON | Estado del sistema |
| `GET_IP` | IP | Dirección IP del ESP32 |
| `FORGET_WIFI` | OK | Resetea configuración WiFi |

### Formato de Respuestas

**GET_STATUS:**
```json
{
  "wifi_ssid": "MiRed",
  "wifi_rssi": -50,
  "ip": "192.168.1.100",
  "uptime": 3600,
  "free_heap": 200000,
  "sensors": {...}
}
```

---

## 🔥 GASOX - Sistema de Detección de Gases

### Hardware
- **Sensores:** MQ4 (metano), MQ7 (CO)
- **Actuadores:** LED (GPIO 13), Buzzer (GPIO 26)
- **Pines analógicos:** 34, 35

### Comandos Específicos

| Comando | Respuesta | Descripción |
|---------|-----------|-------------|
| `GET_VALUES` | JSON | Lecturas de sensores |
| `GET_THRESHOLDS` | JSON | Umbrales configurados |
| `SET_THRESHOLD_MQ4:3000` | JSON | Configura umbral MQ4 |
| `SET_THRESHOLD_MQ7:3000` | JSON | Configura umbral MQ7 |
| `GET_ALARM_STATE` | Texto | Estado de alarma |

### Respuesta GET_VALUES
```json
{
  "mq4": 2500,
  "mq7": 1800,
  "alarm": false,
  "mq4_threshold": 3000,
  "mq7_threshold": 3000
}
```

### Lógica de Alarma
```cpp
if (mq4Value > mq4Threshold || mq7Value > mq7Threshold) {
    activateAlarm(true);  // LED y buzzer parpadean
} else {
    activateAlarm(false);
}
```

### Base de Datos
```sql
CREATE TABLE measurements (
    id INTEGER PRIMARY KEY,
    mq4 INTEGER,
    mq7 INTEGER,
    alarm BOOLEAN,
    timestamp TEXT
);
```

---

## 🌤️ FERSXMET - Estación Meteorológica

### Hardware
- **DHT22:** GPIO 4 (temperatura/humedad)
- **MLX90614:** I2C (SDA=16, SCL=17) - temperatura IR
- **BH1750:** I2C (SDA=21, SCL=22) - luminosidad

### Comandos Específicos

| Comando | Respuesta | Descripción |
|---------|-----------|-------------|
| `GET_WEATHER` | JSON | Datos meteorológicos |
| `GET_THERMAL` | JSON | Datos térmicos IR |

### Respuesta GET_WEATHER
```json
{
  "temperature": 25.5,
  "humidity": 60.0,
  "luminosity": 450.0
}
```

### Respuesta GET_THERMAL
```json
{
  "ambient_temp": 24.0,
  "object_temp": 36.5,
  "difference": 12.5
}
```

### Buses I2C Separados
```cpp
TwoWire I2C_MLX = TwoWire(0);    // Bus 1
TwoWire I2C_BH1750 = TwoWire(1); // Bus 2
```

---

## 🏥 DrHome - Sistema Médico

### Hardware
- **MAX30102:** I2C (SDA=16, SCL=17) - pulso/SpO2
- **MLX90614:** I2C (SDA=21, SCL=22) - temperatura

### Comandos Específicos

| Comando | Respuesta | Descripción |
|---------|-----------|-------------|
| `GET_VITALS` | JSON | Signos vitales |
| `START_MEASUREMENT` | JSON | Inicia medición |
| `STOP_MEASUREMENT` | JSON | Detiene medición |

### Respuesta GET_VITALS
```json
{
  "heart_rate": 75,
  "spo2": 98,
  "body_temp": 36.5,
  "finger_detected": true,
  "measuring": false
}
```

### Algoritmo de Detección de Latidos
```cpp
if (checkForBeat(irValue)) {
    long delta = millis() - lastBeat;
    beatsPerMinute = 60 / (delta / 1000.0);
    // Promedio de últimas 4 lecturas
    beatAvg = average(rates, RATE_SIZE);
}
```

### Cálculo de SpO2
```cpp
float ratio = (float)redValue / (float)irValue;
currentSpO2 = 104 - 17 * ratio;
// Limitar entre 70-100%
```

### Base de Datos

**Tabla Pacientes:**
```sql
CREATE TABLE patients (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER,
    gender TEXT,
    height REAL,
    weight REAL,
    blood_type TEXT,
    allergies TEXT,
    notes TEXT,
    created_at TEXT,
    updated_at TEXT
);
```

**Tabla Mediciones:**
```sql
CREATE TABLE measurements (
    id INTEGER PRIMARY KEY,
    patient_id INTEGER,
    heart_rate INTEGER,
    spo2 INTEGER,
    body_temp REAL,
    notes TEXT,
    timestamp TEXT,
    FOREIGN KEY (patient_id) REFERENCES patients(id)
);
```

### Diagnóstico Automático

**Parámetros evaluados:**
- Frecuencia cardíaca: <60 (bradicardia), 60-100 (normal), >100 (taquicardia)
- SpO2: <90% (crítico), 90-94% (bajo), ≥95% (normal)
- Temperatura: <36.5°C (baja), 36.5-37.4°C (normal), ≥38°C (fiebre)
- IMC: <18.5 (bajo peso), 18.5-24.9 (normal), 25-29.9 (sobrepeso), ≥30 (obesidad)

---

## 📱 Arquitectura Flutter

### Estructura de Carpetas
```
lib/
├── main.dart                 # Punto de entrada
├── models/                   # Modelos de datos
│   ├── patient.dart
│   └── measurement.dart
├── providers/                # Gestión de estado
│   ├── theme_provider.dart
│   ├── patient_provider.dart
│   └── esp32_provider.dart
├── database/                 # SQLite
│   └── database_helper.dart
├── screens/                  # Pantallas
│   ├── splash_screen.dart
│   ├── home_screen.dart
│   └── ...
└── utils/                    # Utilidades
    └── theme.dart
```

### Gestión de Estado (Provider)

```dart
// ESP32Provider - Comunicación con hardware
class ESP32Provider extends ChangeNotifier {
  Future<String?> _sendCommand(String command) async {
    socket.write('$command\n');
    await socket.flush();
    final response = await socket.first;
    return utf8.decode(response).trim();
  }
}

// PatientProvider - Lógica de negocio
class PatientProvider extends ChangeNotifier {
  Future<void> addPatient(Patient patient) async {
    await db.insert(patient);
    notifyListeners();
  }
}
```

### Temas Personalizables

```dart
enum AppThemeMode {
  medical,   // Azul médico
  ocean,     // Turquesa
  lavender,  // Morado
  mint,      // Verde
}
```

---

## 🔐 Seguridad y Privacidad

### Datos Locales
- ✅ Toda la información se almacena localmente
- ✅ No se envía a servidores externos
- ✅ Conexión directa ESP32 ↔ App

### WiFi
- ✅ WPA2 encryption
- ✅ Portal cautivo para configuración
- ✅ Opción de olvidar red

---

## ⚡ Optimizaciones

### ESP32
- **Consumo de energía:** ~250-400mA con sensores
- **Frecuencia de actualización:** 100ms
- **Memoria libre:** ~200KB después de inicialización

### Flutter
- **Tamaño APK:** ~15-20MB
- **Uso de RAM:** ~100-150MB
- **Base de datos:** SQLite optimizada con índices

---

## 🧪 Testing

### Prueba de Conexión
```powershell
$client = New-Object System.Net.Sockets.TcpClient("192.168.1.100", 8080)
$stream = $client.GetStream()
$writer = New-Object System.IO.StreamWriter($stream)
$writer.WriteLine("GET_STATUS")
$writer.Flush()
$reader = New-Object System.IO.StreamReader($stream)
$response = $reader.ReadLine()
Write-Host $response
$client.Close()
```

### Escaneo I2C
```cpp
for (address = 1; address < 127; address++) {
    Wire.beginTransmission(address);
    error = Wire.endTransmission();
    if (error == 0) {
        Serial.print("Dispositivo en 0x");
        Serial.println(address, HEX);
    }
}
```

---

## 🔧 Troubleshooting Técnico

### Brownout Detector
```cpp
// Deshabilitar temporalmente
#include <soc/soc.h>
#include <soc/rtc_cntl_reg.h>

void setup() {
    WRITE_PERI_REG(RTC_CNTL_BROWN_OUT_REG, 0);
}
```

### Timeout de Socket
```dart
socket = await Socket.connect(
    ip, 
    8080,
    timeout: const Duration(seconds: 3),
);
```

### Memoria Fragmentada
```cpp
// Monitorear heap
Serial.println(ESP.getFreeHeap());
Serial.println(ESP.getMinFreeHeap());
```

---

## 📊 Especificaciones Técnicas

### ESP32
- **CPU:** Dual-core Xtensa 32-bit LX6 @ 240MHz
- **RAM:** 520KB SRAM
- **Flash:** 4MB
- **WiFi:** 802.11 b/g/n
- **Bluetooth:** v4.2 BR/EDR y BLE

### Sensores

| Sensor | Interfaz | Voltaje | Consumo | Precisión |
|--------|----------|---------|---------|-----------|
| MQ4 | Analógico | 5V | 150mA | ±10% |
| MQ7 | Analógico | 5V | 150mA | ±10% |
| DHT22 | Digital | 3.3-5V | 2.5mA | ±0.5°C, ±2% |
| MLX90614 | I2C | 3.3-5V | 2mA | ±0.5°C |
| BH1750 | I2C | 3.3-5V | 0.12mA | ±20% |
| MAX30102 | I2C | 3.3-5V | 50mA | HR: ±2 BPM |

---

## 🚀 Mejoras Futuras

### Hardware
- [ ] Agregar pantalla OLED
- [ ] Batería recargable
- [ ] Carcasa impresa en 3D
- [ ] Más sensores

### Software
- [ ] Sincronización en la nube
- [ ] Notificaciones push
- [ ] Gráficos avanzados
- [ ] Exportar a PDF
- [ ] Modo oscuro
- [ ] Múltiples idiomas

---

## 📚 Referencias

- [ESP32 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)
- [Flutter Documentation](https://docs.flutter.dev/)
- [Arduino ESP32](https://github.com/espressif/arduino-esp32)
- [Provider Package](https://pub.dev/packages/provider)

---

**Versión:** 1.0.0
**Última actualización:** 2025
