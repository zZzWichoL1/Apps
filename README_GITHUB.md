# 📱 Apps IoT con ESP32 y Flutter

Colección de 3 aplicaciones IoT profesionales desarrolladas con ESP32 y Flutter.

[![Flutter](https://img.shields.io/badge/Flutter-3.0+-blue.svg)](https://flutter.dev/)
[![ESP32](https://img.shields.io/badge/ESP32-Arduino-green.svg)](https://www.espressif.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 🎯 Proyectos

### 1. 🔥 GASOX - Sistema de Detección de Gases
Detecta gas metano (MQ4) y monóxido de carbono (MQ7) con alarma visual y sonora.

**Características:**
- Detección en tiempo real
- Umbrales configurables
- Alarma LED + Buzzer
- Historial de mediciones
- Base de datos local

**Hardware:**
- ESP32 DevKit
- Sensor MQ4 (metano)
- Sensor MQ7 (CO)
- LED y Buzzer

---

### 2. 🌤️ FERSXMET - Estación Meteorológica
Estación meteorológica completa con múltiples sensores.

**Características:**
- Temperatura y humedad ambiente
- Temperatura infrarroja sin contacto
- Medición de luminosidad
- Gráficos de evolución
- Exportación de datos

**Hardware:**
- ESP32 DevKit
- DHT22 (temperatura/humedad)
- MLX90614 (temperatura IR)
- BH1750 (luminosidad)

---

### 3. 🏥 DrHome - Sistema Médico Profesional
Sistema médico para monitoreo de signos vitales con gestión de pacientes.

**Características:**
- Frecuencia cardíaca en tiempo real
- Saturación de oxígeno (SpO2)
- Temperatura corporal
- Gestión de pacientes completa
- Diagnósticos automáticos
- Historial clínico
- Cálculo de IMC
- 4 temas personalizables

**Hardware:**
- ESP32 DevKit
- MAX30102 (pulso/SpO2)
- MLX90614 (temperatura)

---

## 🚀 Inicio Rápido

### Requisitos
```bash
- Arduino IDE con soporte ESP32
- Flutter SDK 3.0+
- Android Studio / VS Code
- ESP32 DevKit
- Sensores según el proyecto
```

### Instalación

1. **Clonar repositorio**
```bash
git clone https://github.com/zZzWichoL1/Apps.git
cd Apps
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

## 📁 Estructura del Proyecto

```
Apps/
├── gasox/                          # App GASOX
│   ├── gasox.ino                   # Código ESP32
│   └── [archivos Flutter]
│
├── fersxmet/                       # App FERSXMET
│   └── [archivos Flutter]
│
├── drhome_app/drhome/              # App DrHome
│   ├── drhome_esp32_FINAL/         # Código ESP32
│   ├── lib/                        # Código Flutter
│   └── README.md
│
├── unified_esp32.ino               # ESP32 unificado GASOX+FERSXMET
├── README.md                       # Documentación principal
├── GUIA_RAPIDA.md                  # Guía de inicio rápido
└── DOCUMENTACION_TECNICA.md        # Detalles técnicos
```

---

## 🎨 Capturas de Pantalla

### GASOX
<p align="center">
  <img src="screenshots/gasox_1.png" width="250" />
  <img src="screenshots/gasox_2.png" width="250" />
  <img src="screenshots/gasox_3.png" width="250" />
</p>

### FERSXMET
<p align="center">
  <img src="screenshots/fersxmet_1.png" width="250" />
  <img src="screenshots/fersxmet_2.png" width="250" />
  <img src="screenshots/fersxmet_3.png" width="250" />
</p>

### DrHome
<p align="center">
  <img src="screenshots/drhome_1.png" width="250" />
  <img src="screenshots/drhome_2.png" width="250" />
  <img src="screenshots/drhome_3.png" width="250" />
</p>

---

## 🛠️ Tecnologías

**Hardware:**
- ESP32 (WiFi + Bluetooth)
- Sensores I2C y analógicos
- Actuadores (LED, Buzzer)

**Software:**
- Arduino C++ (ESP32)
- Flutter/Dart (Apps móviles)
- SQLite (Base de datos)
- Provider (Gestión de estado)
- Material Design 3

---

## 📖 Documentación

- **[README.md](README.md)** - Documentación principal
- **[GUIA_RAPIDA.md](GUIA_RAPIDA.md)** - Configuración paso a paso
- **[DOCUMENTACION_TECNICA.md](DOCUMENTACION_TECNICA.md)** - Detalles técnicos completos

Cada proyecto tiene su propio README con instrucciones específicas.

---

## 🔌 Conexiones de Hardware

### GASOX
```
MQ4:  VCC→5V, GND→GND, AO→GPIO34
MQ7:  VCC→5V, GND→GND, AO→GPIO35
LED:  GPIO13
Buzzer: GPIO26
```

### FERSXMET
```
DHT22:    VCC→3.3V, GND→GND, DATA→GPIO4
MLX90614: VCC→3.3V, GND→GND, SDA→GPIO16, SCL→GPIO17
BH1750:   VCC→3.3V, GND→GND, SDA→GPIO21, SCL→GPIO22
```

### DrHome
```
MAX30102: VCC→3.3V, GND→GND, SDA→GPIO16, SCL→GPIO17
MLX90614: VCC→3.3V, GND→GND, SDA→GPIO21, SCL→GPIO22
```

---

## ✨ Características Comunes

✅ Conexión WiFi con WiFiManager
✅ Interfaz Flutter moderna y responsive
✅ Base de datos SQLite local
✅ Temas personalizables
✅ Gráficos en tiempo real
✅ Historial de datos
✅ Exportación de datos
✅ Diseño Material Design 3

---

## 🤝 Contribuir

Las contribuciones son bienvenidas! Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

---

## 👨‍💻 Autor

**Wicho**
- GitHub: [@zZzWichoL1](https://github.com/zZzWichoL1)

---

## 🆘 Soporte

Para problemas o preguntas:
1. Revisa la [documentación](README.md)
2. Consulta la [guía rápida](GUIA_RAPIDA.md)
3. Abre un [issue](https://github.com/zZzWichoL1/Apps/issues)

---

## 📊 Estado del Proyecto

- ✅ GASOX - Completo y funcional
- ✅ FERSXMET - Completo y funcional
- ✅ DrHome - Completo y funcional
- ✅ Unified ESP32 - Completo y funcional

---

## 🎓 Aprendizajes

Este proyecto integra:
- IoT con ESP32
- Desarrollo móvil con Flutter
- Comunicación WiFi TCP/IP
- Sensores I2C y analógicos
- Bases de datos SQLite
- Diseño UI/UX profesional
- Gestión de estado con Provider

---

## 🔮 Roadmap

- [ ] Sincronización en la nube
- [ ] Notificaciones push
- [ ] Modo oscuro completo
- [ ] Soporte para más sensores
- [ ] Exportar a PDF
- [ ] Múltiples idiomas
- [ ] Integración con Google Fit / Apple Health

---

**⭐ Si te gusta este proyecto, dale una estrella!**

---

**Versión:** 1.0.0  
**Última actualización:** 2025
