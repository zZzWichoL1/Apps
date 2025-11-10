# 🌤️ FERSXMET - Sistema Meteorológico

<div align="center">

![FERSXMET](https://img.shields.io/badge/FERSXMET-v1.0.0-7B68EE?style=for-the-badge)
![Flutter](https://img.shields.io/badge/Flutter-3.0+-02569B?style=for-the-badge&logo=flutter)
![ESP32](https://img.shields.io/badge/ESP32-IoT-000000?style=for-the-badge&logo=espressif)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**Sistema meteorológico moderno y elegante con ESP32**

[Características](#-características) • [Instalación](#-instalación-rápida) • [Documentación](#-documentación) • [Soporte](#-soporte)

</div>

---

## 📖 Descripción

FERSXMET es una aplicación Flutter minimalista y elegante para monitoreo meteorológico en tiempo real. Utiliza un ESP32 con sensores especializados para capturar temperatura, humedad, luminosidad y mapas de calor térmicos.

### 🎯 Características Principales

- **🎨 Diseño Minimalista**: Interfaz moderna y elegante con 10 temas personalizables
- **📊 Mapa de Calor**: Visualización térmica en tiempo real con sensor MLX90640
- **📍 Geolocalización**: Registro automático de coordenadas GPS
- **💾 Base de Datos**: Historial completo con SQLite
- **🌐 WiFi ESP32**: Configuración fácil mediante portal web
- **🎨 Temas Personalizables**: 10 colores pastel para elegir

## 🚀 Instalación Rápida

### Opción 1: Ejecutar Directamente

```bash
# Desde el proyecto GASOX
flutter run -t lib/main_fersxmet.dart
```

### Opción 2: Compilar APK

```bash
flutter build apk -t lib/main_fersxmet.dart --release
```

### Opción 3: Proyecto Nuevo

```bash
flutter create fersxmet
# Copiar archivos de lib/fersxmet/
flutter pub get
flutter run
```

## 📱 Capturas de Pantalla

```
┌─────────────────────────────────────┐
│  🌤️ FERSXMET                        │
│  Sistema Meteorológico              │
│                                     │
│  📍 Lat: 19.432608, Lng: -99.133209│
│                                     │
│  ┌──────────┐  ┌──────────┐       │
│  │ 🌡️ 25.5°C│  │ 💧 60.2% │       │
│  │ Temp     │  │ Humedad  │       │
│  └──────────┘  └──────────┘       │
│                                     │
│  ┌─────────────────────────┐       │
│  │ ☀️ 450 lux              │       │
│  │ Luminosidad             │       │
│  └─────────────────────────┘       │
│                                     │
│  ┌─────────────────────────┐       │
│  │ 🔥 Mapa de Calor        │       │
│  │ [Visualización 32x24]   │       │
│  └─────────────────────────┘       │
│                                     │
│  [💾 Guardar Lecturas]             │
└─────────────────────────────────────┘
```

## 🔧 Hardware Necesario

### Componentes

| Componente | Descripción | Precio Aprox. |
|------------|-------------|---------------|
| ESP32 DevKit | Microcontrolador WiFi | $5-10 USD |
| MLX90640 | Sensor térmico IR 32x24 | $50-70 USD |
| DHT22 | Temperatura y humedad | $3-5 USD |
| BH1750 | Sensor de luminosidad | $2-3 USD |
| Cables | Jumper wires | $2 USD |

### Conexiones

```
ESP32 Pinout:
┌─────────────────────────────────────┐
│                                     │
│  MLX90640 (I2C)                    │
│  ├─ SDA → GPIO 21                  │
│  ├─ SCL → GPIO 22                  │
│  ├─ VCC → 3.3V                     │
│  └─ GND → GND                      │
│                                     │
│  DHT22                             │
│  ├─ DATA → GPIO 4                  │
│  ├─ VCC → 3.3V                     │
│  └─ GND → GND                      │
│                                     │
│  BH1750 (I2C)                      │
│  ├─ SDA → GPIO 21 (compartido)    │
│  ├─ SCL → GPIO 22 (compartido)    │
│  ├─ VCC → 3.3V                     │
│  └─ GND → GND                      │
│                                     │
└─────────────────────────────────────┘
```

## 📚 Documentación

### Guías Disponibles

| Documento | Descripción |
|-----------|-------------|
| [INICIO_RAPIDO.md](INICIO_RAPIDO.md) | Guía de inicio rápido |
| [FERSXMET_README.md](FERSXMET_README.md) | Documentación técnica completa |
| [FERSXMET_SETUP.md](FERSXMET_SETUP.md) | Configuración detallada |
| [COMPARACION_GASOX_FERSXMET.md](COMPARACION_GASOX_FERSXMET.md) | Diferencias con GASOX |
| [PERSONALIZACION_AVANZADA.md](PERSONALIZACION_AVANZADA.md) | Personalización y extensiones |
| [CHECKLIST_IMPLEMENTACION.md](CHECKLIST_IMPLEMENTACION.md) | Lista de verificación |
| [ESP32_FERSXMET.ino](ESP32_FERSXMET.ino) | Código Arduino |

### Estructura del Proyecto

```
fersxmet/
├── lib/
│   ├── main_fersxmet.dart              # Punto de entrada
│   └── fersxmet/
│       ├── models/
│       │   └── weather_reading.dart    # Modelo de datos
│       ├── services/
│       │   ├── esp32_weather_service.dart
│       │   ├── weather_database_service.dart
│       │   └── weather_location_service.dart
│       ├── screens/
│       │   ├── weather_splash_screen.dart
│       │   ├── weather_home_screen.dart
│       │   ├── weather_database_screen.dart
│       │   ├── weather_network_settings_screen.dart
│       │   └── theme_selector_screen.dart
│       ├── widgets/
│       │   └── heat_map_widget.dart
│       └── utils/
│           └── theme_manager.dart
├── ESP32_FERSXMET.ino                  # Código Arduino
└── docs/                               # Documentación
```

## 🎨 Temas Disponibles

FERSXMET incluye 10 temas de colores pastel:

1. 🟣 **Morado Pastel** (por defecto)
2. 🔵 **Azul Pastel**
3. 🌸 **Rosa Pastel**
4. 🟢 **Verde Pastel**
5. 🧡 **Coral Pastel**
6. 💜 **Lavanda**
7. 🌿 **Menta**
8. 🍑 **Durazno**
9. 🌊 **Turquesa**
10. 💐 **Lila**

## 🔌 Protocolo de Comunicación

### Comandos Disponibles

```
GET_WEATHER
→ {"temperature": 25.5, "humidity": 60.2, "luminosity": 450.0}

GET_HEATMAP
→ {"heatmap": [[20.1, 20.3, ...], [20.2, 20.4, ...], ...]}

GET_STATUS
→ {"wifi_ssid": "...", "wifi_rssi": -45, "ip": "...", ...}

FORGET_WIFI
→ "OK" (reinicia ESP32)
```

## 📊 Características Técnicas

### Aplicación

- **Framework**: Flutter 3.0+
- **Lenguaje**: Dart 3.0+
- **Base de Datos**: SQLite
- **Geolocalización**: Geolocator
- **Tamaño APK**: ~20 MB
- **Uso de RAM**: ~120 MB
- **Plataformas**: Android, iOS

### ESP32

- **Microcontrolador**: ESP32 (240 MHz dual-core)
- **WiFi**: 802.11 b/g/n
- **Protocolo**: TCP Socket (puerto 8080)
- **Formato de datos**: JSON
- **Actualización**: Cada 3 segundos

## 🛠️ Dependencias

```yaml
dependencies:
  flutter:
    sdk: flutter
  shared_preferences: ^2.2.2
  sqflite: ^2.3.0
  path: ^1.8.3
  geolocator: ^13.0.2
  intl: ^0.20.2
  url_launcher: ^6.2.6
```

## 📝 Uso

### 1. Configurar ESP32

```bash
1. Cargar ESP32_FERSXMET.ino en Arduino IDE
2. Conectar sensores según el diagrama
3. Subir código al ESP32
4. Conectar a red WiFi "FERSXMET"
5. Configurar WiFi en http://192.168.4.1
```

### 2. Conectar App

```bash
1. Abrir FERSXMET
2. Ir a Configuración WiFi
3. Ingresar IP del ESP32
4. Presionar "Conectar"
5. ¡Listo!
```

### 3. Monitorear Datos

```bash
1. Ver datos en tiempo real
2. Presionar "Guardar Lecturas"
3. Revisar historial en Base de Datos
4. Personalizar tema en Selector de Temas
```

## 🐛 Solución de Problemas

### Problemas Comunes

| Problema | Solución |
|----------|----------|
| No se conecta al ESP32 | Verificar IP y red WiFi |
| Sensor no detectado | Revisar conexiones I2C |
| Ubicación no disponible | Activar GPS y permisos |
| Mapa de calor vacío | Esperar inicialización MLX90640 |
| App crashea | Revisar logs con `flutter run -v` |

### Logs Útiles

```bash
# Flutter
flutter run -v

# ESP32
# Abrir Serial Monitor (115200 baud)
```

## 🤝 Contribuir

¿Quieres mejorar FERSXMET? ¡Genial!

1. Fork el proyecto
2. Crea una rama (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver `LICENSE` para más detalles.

## 👥 Autores

- **Desarrollador Principal** - *Trabajo inicial* - FERSXMET Team

## 🙏 Agradecimientos

- Basado en el proyecto GASOX
- Inspirado en diseños minimalistas modernos
- Comunidad de Flutter y ESP32

## 📞 Soporte

¿Necesitas ayuda?

- 📧 Email: support@fersxmet.com
- 💬 Discord: [FERSXMET Community](https://discord.gg/fersxmet)
- 📖 Wiki: [Documentación Completa](https://github.com/fersxmet/wiki)
- 🐛 Issues: [Reportar Bug](https://github.com/fersxmet/issues)

## 🗺️ Roadmap

### Versión 1.1 (Próximamente)
- [ ] Gráficos de tendencias
- [ ] Exportación a CSV/Excel
- [ ] Notificaciones push
- [ ] Modo claro/oscuro

### Versión 2.0 (Futuro)
- [ ] Sincronización en la nube
- [ ] Múltiples dispositivos ESP32
- [ ] Dashboard web
- [ ] API REST

## 📈 Estadísticas

![GitHub stars](https://img.shields.io/github/stars/fersxmet/fersxmet?style=social)
![GitHub forks](https://img.shields.io/github/forks/fersxmet/fersxmet?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/fersxmet/fersxmet?style=social)

## 🌟 Showcase

¿Usas FERSXMET? ¡Comparte tu proyecto!

- Envía un PR con tu implementación
- Comparte en redes sociales con #FERSXMET
- Únete a nuestra comunidad

---

<div align="center">

**Hecho con ❤️ por el equipo FERSXMET**

[⬆ Volver arriba](#-fersxmet---sistema-meteorológico)

</div>
