# 🌡️ FERSXMET - Estación Meteorológica con ESP32

## 📱 Estado del Proyecto: ✅ LISTO PARA USAR

**APK Compilado**: `build\app\outputs\flutter-apk\app-release.apk` (45.9 MB)  
**Versión**: 1.0.0  
**Package**: com.example.fersxmet

---

## 🚀 Inicio Rápido

### 1. Instalar la App (2 minutos)

**Opción A: Usando ADB**
```bash
adb install build\app\outputs\flutter-apk\app-release.apk
```

**Opción B: Manual**
1. Copia el APK a tu dispositivo Android
2. Abre el archivo y toca "Instalar"
3. Acepta los permisos de ubicación

### 2. Configurar ESP32 (30 minutos)

Ver instrucciones detalladas en: `FERSXMET_SETUP.md`

**Hardware necesario**:
- ESP32
- Sensor MLX90640 (cámara térmica)
- Sensor DHT22 (temperatura/humedad)
- Sensor BH1750 (luminosidad)

**Conexiones rápidas**:
```
MLX90640: SDA→21, SCL→22, VCC→3.3V, GND→GND
DHT22:    DATA→4, VCC→3.3V, GND→GND
BH1750:   SDA→21, SCL→22, VCC→3.3V, GND→GND
```

### 3. Conectar App con ESP32 (1 minuto)

1. Abre la app FERSXMET
2. Ve a ⚙️ Configuración de Red
3. Ingresa la IP del ESP32 (visible en Serial Monitor)
4. Toca "Guardar"
5. ¡Listo! Ya puedes ver las lecturas

---

## 📚 Documentación Completa

| Documento | Descripción |
|-----------|-------------|
| `COMPILACION_EXITOSA.md` | Cómo instalar el APK y troubleshooting |
| `FERSXMET_SETUP.md` | Configuración completa del ESP32 |
| `CAMBIOS_REALIZADOS.md` | Resumen de todos los cambios aplicados |
| `CHECKLIST_FERSXMET.md` | Lista de verificación del proyecto |
| `CONFIGURACION_ENTORNO.md` | Configuración del entorno de desarrollo |

---

## ✨ Características

### 📊 Monitoreo en Tiempo Real
- 🌡️ Temperatura y humedad (DHT22)
- 💡 Luminosidad ambiental (BH1750)
- 🔥 Mapa de calor térmico 24x32 (MLX90640)
- 📍 Geolocalización de lecturas

### 💾 Base de Datos Local
- Guarda todas las lecturas automáticamente
- Historial completo con fecha, hora y ubicación
- Búsqueda y filtrado de datos

### 🎨 Personalización
- 10 temas de colores pastel
- Interfaz moderna y responsive
- Modo oscuro optimizado

### 🌐 Conectividad
- Conexión WiFi con ESP32
- Configuración de red flexible
- Detección automática de conectividad

---

## 🎯 Casos de Uso

### 🏠 Hogar
- Monitoreo de temperatura y humedad en habitaciones
- Control de iluminación natural
- Detección de fugas de calor

### 🌱 Agricultura
- Monitoreo de condiciones en invernaderos
- Control de riego basado en humedad
- Optimización de luz para plantas

### 🏭 Industrial
- Monitoreo de equipos con cámara térmica
- Detección de puntos calientes
- Control de condiciones ambientales

### 🔬 Educación
- Experimentos de física y química
- Proyectos de IoT
- Aprendizaje de sensores y microcontroladores

---

## 🛠️ Tecnologías Utilizadas

### App Móvil
- **Framework**: Flutter 3.35.6
- **Lenguaje**: Dart
- **Base de Datos**: SQLite (sqflite)
- **Geolocalización**: Geolocator
- **UI**: Material Design 3

### Hardware
- **Microcontrolador**: ESP32
- **Sensores**:
  - MLX90640: Cámara térmica 24x32 píxeles
  - DHT22: Temperatura (-40 a 80°C) y humedad (0-100%)
  - BH1750: Luminosidad (1-65535 lux)

### Comunicación
- **Protocolo**: HTTP REST
- **Puerto**: 8080
- **Formato**: JSON

---

## 📱 Capturas de Pantalla

### Pantalla Principal
- Lecturas en tiempo real
- Mapa de calor térmico
- Indicadores visuales

### Historial
- Lista de todas las lecturas
- Filtrado por fecha
- Detalles de cada lectura

### Configuración
- Ajuste de IP del ESP32
- Selector de temas
- Información de la app

---

## 🔧 Desarrollo

### Compilar desde Código Fuente

```bash
# Clonar el repositorio
cd fersxmet

# Instalar dependencias
flutter pub get

# Ejecutar en modo desarrollo
flutter run

# Compilar APK release
flutter build apk --release
```

### Estructura del Proyecto

```
lib/
├── main.dart                    # Punto de entrada
└── fersxmet/
    ├── models/                  # Modelos de datos
    │   └── weather_reading.dart
    ├── screens/                 # Pantallas de la app
    │   ├── weather_home_screen.dart
    │   ├── weather_database_screen.dart
    │   ├── weather_network_settings_screen.dart
    │   ├── weather_splash_screen.dart
    │   └── theme_selector_screen.dart
    ├── services/                # Servicios
    │   ├── esp32_weather_service.dart
    │   ├── weather_database_service.dart
    │   └── weather_location_service.dart
    ├── utils/                   # Utilidades
    │   └── theme_manager.dart
    └── widgets/                 # Widgets personalizados
        └── heat_map_widget.dart
```

---

## 🐛 Troubleshooting

### App no se conecta al ESP32
1. Verifica que ambos estén en la misma red WiFi
2. Comprueba la IP del ESP32 en el Serial Monitor
3. Intenta hacer ping: `ping [IP_DEL_ESP32]`

### Sensor no responde
1. Verifica las conexiones físicas
2. Usa un I2C scanner para detectar dispositivos
3. Revisa la alimentación (debe ser 3.3V)

### Mapa de calor no se muestra
1. El MLX90640 tarda unos segundos en inicializar
2. Verifica que la respuesta JSON tenga 768 elementos
3. Comprueba que el sensor esté correctamente conectado

### Ubicación no disponible
1. Acepta los permisos de ubicación
2. Activa el GPS en tu dispositivo
3. Sal al exterior o acércate a una ventana

---

## 📊 Especificaciones Técnicas

### Requisitos de la App
- **Android**: 5.0 (API 21) o superior
- **Espacio**: 100 MB mínimo
- **RAM**: 2 GB recomendado
- **Permisos**: Internet, Ubicación, WiFi

### Requisitos del ESP32
- **Voltaje**: 3.3V
- **Corriente**: 500mA mínimo (con todos los sensores)
- **WiFi**: 2.4 GHz (802.11 b/g/n)
- **Memoria**: 4 MB Flash mínimo

### Rendimiento
- **Frecuencia de lectura**: 1 segundo
- **Latencia de red**: < 100ms (red local)
- **Precisión DHT22**: ±0.5°C, ±2% HR
- **Precisión BH1750**: ±20%
- **Resolución MLX90640**: 24x32 píxeles

---

## 🤝 Contribuir

Este es un proyecto educativo. Siéntete libre de:
- Reportar bugs
- Sugerir mejoras
- Agregar nuevos sensores
- Mejorar la interfaz

---

## 📄 Licencia

Este proyecto es de código abierto para fines educativos.

---

## 👨‍💻 Autor

Proyecto FERSXMET - Estación Meteorológica con ESP32

---

## 🎉 ¡Gracias por usar FERSXMET!

Si tienes preguntas o problemas, revisa la documentación en los archivos MD incluidos.

**¡Disfruta monitoreando el clima con tu estación meteorológica!** 🌤️
