# 📱 Sistemas IoT con ESP32 y Flutter

Colección de 3 aplicaciones IoT profesionales con ESP32 y Flutter.

---

## 🎯 Proyectos Incluidos

### 1. 🔥 GASOX - Sistema de Detección de Gases
**Carpeta:** `gasox/`
- Detecta gas metano (MQ4) y monóxido de carbono (MQ7)
- Alarma visual y sonora
- Umbrales configurables
- Base de datos local

### 2. 🌤️ FERSXMET - Estación Meteorológica
**Carpeta:** `fersxmet/`
- Temperatura y humedad (DHT22)
- Temperatura infrarroja (MLX90614)
- Luminosidad (BH1750)
- Historial de mediciones

### 3. 🏥 DrHome - Sistema Médico
**Carpeta:** `drhome_app/drhome/`
- Frecuencia cardíaca y SpO2 (MAX30102)
- Temperatura corporal (MLX90614)
- Gestión de pacientes
- Diagnósticos automáticos
- Historial clínico completo

---

## 📁 Estructura del Proyecto

```
.
├── gasox/                          # App GASOX
│   ├── gasox.ino                   # Código ESP32
│   └── [archivos Flutter]
│
├── fersxmet/                       # App FERSXMET
│   └── [archivos Flutter]
│
├── drhome_app/drhome/              # App DrHome
│   ├── drhome_esp32_FINAL.ino      # Código ESP32
│   ├── lib/                        # Código Flutter
│   └── README.md                   # Documentación DrHome
│
├── unified_esp32.ino               # ESP32 unificado GASOX+FERSXMET
├── README.md                       # Este archivo
├── GUIA_RAPIDA.md                  # Guía de inicio rápido
└── DOCUMENTACION_TECNICA.md        # Detalles técnicos
```

---

## 🚀 Inicio Rápido

### Requisitos
- Arduino IDE con soporte ESP32
- Flutter SDK 3.0+
- ESP32 DevKit
- Sensores según el proyecto

### Instalación Rápida

1. **Clonar repositorio**
```bash
git clone [tu-repo]
cd [tu-repo]
```

2. **Cargar código ESP32**
```bash
# Abre Arduino IDE
# Abre el archivo .ino del proyecto
# Selecciona placa ESP32
# Carga el código
```

3. **Ejecutar app Flutter**
```bash
cd [carpeta-proyecto]
flutter pub get
flutter run
```

---

## 📖 Documentación

- **[GUIA_RAPIDA.md](GUIA_RAPIDA.md)** - Configuración paso a paso
- **[DOCUMENTACION_TECNICA.md](DOCUMENTACION_TECNICA.md)** - Detalles técnicos completos
- **Cada proyecto tiene su propio README** con instrucciones específicas

---

## 🔌 Hardware Necesario

### GASOX
- ESP32 DevKit
- Sensor MQ4 (gas metano)
- Sensor MQ7 (monóxido de carbono)
- LED y buzzer

### FERSXMET
- ESP32 DevKit
- Sensor DHT22 (temperatura/humedad)
- Sensor MLX90614 (temperatura IR)
- Sensor BH1750 (luminosidad)

### DrHome
- ESP32 DevKit
- Sensor MAX30102 (pulso/SpO2)
- Sensor MLX90614 (temperatura)

---

## 🎨 Características Comunes

✅ Conexión WiFi con WiFiManager
✅ Interfaz Flutter moderna
✅ Base de datos SQLite local
✅ Temas personalizables
✅ Gráficos en tiempo real
✅ Historial de datos
✅ Exportación de datos

---

## 📱 Capturas de Pantalla

Ver carpeta de cada proyecto para capturas específicas.

---

## 🛠️ Tecnologías

**Hardware:**
- ESP32 (WiFi + Bluetooth)
- Sensores I2C y analógicos

**Software:**
- Arduino C++ (ESP32)
- Flutter/Dart (Apps móviles)
- SQLite (Base de datos)
- Provider (Gestión de estado)

---

## 📄 Licencia

MIT License - Libre para uso personal y comercial

---

## 👨‍💻 Autor

Desarrollado como sistema IoT educativo y profesional.

---

## 🆘 Soporte

Para problemas o preguntas:
1. Revisa la documentación del proyecto específico
2. Consulta GUIA_RAPIDA.md
3. Revisa DOCUMENTACION_TECNICA.md

---

**Versión:** 1.0.0
**Última actualización:** 2025
