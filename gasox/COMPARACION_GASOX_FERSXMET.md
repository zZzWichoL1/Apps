# Comparación: GASOX vs FERSXMET

## 🔄 Diferencias Principales

### Propósito
| GASOX | FERSXMET |
|-------|----------|
| Detector de gases peligrosos | Sistema meteorológico |
| Enfoque en seguridad y alarmas | Enfoque en monitoreo ambiental |
| Alertas críticas | Registro de datos |

### Sensores
| GASOX | FERSXMET |
|-------|----------|
| MQ4 (Metano) | MLX90640 (Térmico IR) |
| MQ7 (Monóxido de Carbono) | DHT22 (Temp/Humedad) |
| - | BH1750 (Luminosidad) |

### Diseño
| GASOX | FERSXMET |
|-------|----------|
| Tema oscuro con naranja | Temas personalizables (10 colores) |
| Diseño industrial | Diseño minimalista y elegante |
| Enfoque en alarmas visuales | Enfoque en visualización de datos |
| Múltiples pantallas | 3 pantallas principales |

## 📱 Comparación de Pantallas

### GASOX (Original)
```
├── Pantalla Principal
│   ├── Valores MQ4 y MQ7
│   ├── Umbrales configurables
│   ├── Alarma visual/sonora
│   └── Estado de conexión
│
├── Notificaciones
│   ├── Configuración de alertas
│   ├── Sonidos personalizados
│   └── Vibración
│
├── Base de Datos
│   ├── Historial de lecturas
│   └── Lecturas de alarma
│
├── Configuración de Red
│   └── WiFi ESP32
│
├── Información
│   └── Acerca de la app
│
└── Lecturas con Ubicación
    └── GPS tracking
```

### FERSXMET (Nueva)
```
├── Pantalla Principal
│   ├── Temperatura ambiental
│   ├── Humedad
│   ├── Luminosidad
│   ├── Mapa de calor térmico
│   ├── Ubicación GPS (compacta)
│   └── Botón guardar
│
├── Base de Datos
│   ├── Historial completo
│   ├── Fecha y hora
│   ├── Coordenadas GPS
│   └── Todos los valores
│
├── Configuración WiFi
│   ├── Conexión ESP32
│   ├── Portal de config
│   └── Reinicio de red
│
└── Selector de Temas
    └── 10 colores pastel
```

## 🎨 Comparación Visual

### Paleta de Colores

**GASOX:**
```
Primario: Naranja (#FF9500)
Fondo: Negro (#000000)
Superficie: Gris oscuro (#1C1C1E)
Acento: Naranja claro (#FFB84D)
```

**FERSXMET:**
```
Primario: Personalizable (10 opciones)
Fondo: Azul oscuro (#1A1A2E)
Superficie: Azul medio (#16213E)
Gradientes: Suaves y elegantes

Temas disponibles:
1. Morado Pastel (#7B68EE)
2. Azul Pastel (#87CEEB)
3. Rosa Pastel (#FFB6C1)
4. Verde Pastel (#98D8C8)
5. Coral Pastel (#FF9999)
6. Lavanda (#E6E6FA)
7. Menta (#98FF98)
8. Durazno (#FFDAB9)
9. Turquesa (#40E0D0)
10. Lila (#C8A2C8)
```

## 🔧 Comparación Técnica

### Arquitectura

**GASOX:**
```
lib/
├── main.dart
├── models/
│   ├── sensor_reading.dart
│   └── sensor_reading_with_location.dart
├── services/
│   ├── esp32_service.dart
│   ├── database_service.dart
│   ├── database_service_with_location.dart
│   ├── enhanced_sensor_service.dart
│   └── location_service.dart
├── screens/
│   ├── splash_screen.dart
│   ├── network_settings_screen.dart
│   ├── notifications_screen.dart
│   ├── database_screen.dart
│   ├── location_readings_screen.dart
│   └── info_screen.dart
├── widgets/
│   └── location_widget.dart
└── utils/
    └── location_integration.dart
```

**FERSXMET:**
```
lib/
├── main_fersxmet.dart
└── fersxmet/
    ├── models/
    │   └── weather_reading.dart
    ├── services/
    │   ├── esp32_weather_service.dart
    │   ├── weather_database_service.dart
    │   └── weather_location_service.dart
    ├── screens/
    │   ├── weather_splash_screen.dart
    │   ├── weather_home_screen.dart
    │   ├── weather_database_screen.dart
    │   ├── weather_network_settings_screen.dart
    │   └── theme_selector_screen.dart
    ├── widgets/
    │   └── heat_map_widget.dart
    └── utils/
        └── theme_manager.dart
```

### Funcionalidades Únicas

**Solo en GASOX:**
- ✅ Sistema de alarmas sonoras
- ✅ Vibración de emergencia
- ✅ Notificaciones push críticas
- ✅ Umbrales configurables
- ✅ WorkManager para monitoreo en segundo plano
- ✅ Múltiples sonidos de alarma
- ✅ Pantalla de información detallada

**Solo en FERSXMET:**
- ✅ Mapa de calor térmico (MLX90640)
- ✅ Selector de temas personalizables
- ✅ Diseño minimalista
- ✅ Visualización de luminosidad
- ✅ Interfaz más limpia y moderna
- ✅ Gradientes suaves
- ✅ Animaciones elegantes

**Compartidas:**
- ✅ Conexión WiFi con ESP32
- ✅ Base de datos SQLite
- ✅ Geolocalización GPS
- ✅ Historial de lecturas
- ✅ Portal de configuración WiFi

## 📊 Comparación de Datos

### Estructura de Datos

**GASOX:**
```dart
class SensorReading {
  int? id;
  DateTime timestamp;
  int mq4Value;        // PPM
  int mq7Value;        // PPM
  bool isHighReading;  // Alarma
}
```

**FERSXMET:**
```dart
class WeatherReading {
  int? id;
  DateTime timestamp;
  double temperature;      // °C
  double humidity;         // %
  double luminosity;       // lux
  double? latitude;        // GPS
  double? longitude;       // GPS
  double? locationAccuracy;
  bool hasLocation;
}
```

## 🌐 Protocolo de Comunicación

### GASOX
```
Comandos:
- GET_VALUES → {mq4: int, mq7: int}
- GET_ALARM_STATE → bool
- SET_MQ4_THRESHOLD → void
- SET_MQ7_THRESHOLD → void
- GET_THRESHOLDS → {mq4_threshold, mq7_threshold}
- FORGET_WIFI → void
```

### FERSXMET
```
Comandos:
- GET_WEATHER → {temperature, humidity, luminosity}
- GET_HEATMAP → {heatmap: [[float]]}
- GET_STATUS → {wifi, sensors, uptime}
- FORGET_WIFI → void
```

## 💾 Base de Datos

### GASOX
```sql
CREATE TABLE sensor_readings (
  id INTEGER PRIMARY KEY,
  timestamp TEXT,
  mq4Value INTEGER,
  mq7Value INTEGER,
  isHighReading INTEGER
);

CREATE TABLE sensor_readings_with_location (
  id INTEGER PRIMARY KEY,
  timestamp TEXT,
  mq4Value INTEGER,
  mq7Value INTEGER,
  isHighReading INTEGER,
  latitude REAL,
  longitude REAL,
  locationAccuracy REAL,
  hasLocation INTEGER
);
```

### FERSXMET
```sql
CREATE TABLE weather_readings (
  id INTEGER PRIMARY KEY,
  timestamp TEXT,
  temperature REAL,
  humidity REAL,
  luminosity REAL,
  latitude REAL,
  longitude REAL,
  locationAccuracy REAL,
  hasLocation INTEGER
);
```

## 🎯 Casos de Uso

### GASOX
- ✅ Detección de fugas de gas en cocinas
- ✅ Monitoreo de CO en garajes
- ✅ Sistemas de seguridad industrial
- ✅ Alertas de emergencia
- ✅ Prevención de intoxicaciones

### FERSXMET
- ✅ Estaciones meteorológicas personales
- ✅ Monitoreo de invernaderos
- ✅ Control de ambientes interiores
- ✅ Estudios de temperatura
- ✅ Análisis de patrones térmicos
- ✅ Proyectos educativos

## 🔋 Consumo de Recursos

### GASOX
```
Tamaño APK: ~25 MB
RAM: ~150 MB
Batería: Media-Alta (alarmas activas)
Permisos: 15+
```

### FERSXMET
```
Tamaño APK: ~20 MB
RAM: ~120 MB
Batería: Media (sin alarmas)
Permisos: 4 (Internet, WiFi, Ubicación)
```

## 🚀 Rendimiento

### Actualización de Datos
| GASOX | FERSXMET |
|-------|----------|
| Cada 2 segundos | Cada 3 segundos |
| Prioridad en alarmas | Prioridad en precisión |

### Tiempo de Respuesta
| GASOX | FERSXMET |
|-------|----------|
| <100ms (crítico) | <500ms (normal) |
| Alarma inmediata | Visualización suave |

## 📈 Escalabilidad

### GASOX
- Fácil añadir más sensores MQ
- Sistema de alarmas extensible
- Múltiples umbrales configurables

### FERSXMET
- Fácil añadir más sensores ambientales
- Sistema de temas extensible
- Visualizaciones personalizables

## 🎓 Curva de Aprendizaje

### GASOX
```
Complejidad: Media-Alta
- Configuración de umbrales
- Gestión de alarmas
- Múltiples pantallas
- Sonidos personalizados
```

### FERSXMET
```
Complejidad: Baja-Media
- Interfaz intuitiva
- Menos opciones
- Diseño minimalista
- Fácil personalización
```

## 🔐 Seguridad

### GASOX
- Enfoque en seguridad física
- Alarmas críticas
- Notificaciones persistentes
- Monitoreo en segundo plano

### FERSXMET
- Enfoque en privacidad de datos
- Almacenamiento local
- Sin notificaciones intrusivas
- Datos encriptados (opcional)

## 📱 Compatibilidad

### Ambas Apps
```
Android: 5.0+ (API 21+)
iOS: 11.0+
Web: Limitado (sin sensores)
Windows/Linux/macOS: Limitado
```

## 🎨 Filosofía de Diseño

### GASOX
```
"Seguridad primero"
- Visibilidad de alarmas
- Colores de advertencia
- Diseño industrial
- Funcionalidad sobre estética
```

### FERSXMET
```
"Elegancia y simplicidad"
- Minimalismo
- Colores suaves
- Diseño moderno
- Estética y funcionalidad equilibradas
```

## 🔄 Migración de GASOX a FERSXMET

Si quieres migrar datos de GASOX a FERSXMET:

```dart
// Script de migración (ejemplo)
Future<void> migrateData() async {
  // 1. Leer datos de GASOX
  final gasoxReadings = await DatabaseService.instance.getAllReadings();
  
  // 2. Convertir a formato FERSXMET
  for (var reading in gasoxReadings) {
    final weatherReading = WeatherReading(
      timestamp: reading.timestamp,
      temperature: 0.0, // No disponible
      humidity: 0.0,    // No disponible
      luminosity: 0.0,  // No disponible
      // Mantener ubicación si existe
    );
    
    // 3. Guardar en FERSXMET
    await WeatherDatabaseService.instance.insertReading(weatherReading);
  }
}
```

## 📝 Conclusión

### Usa GASOX si:
- ✅ Necesitas detección de gases peligrosos
- ✅ Requieres alarmas críticas
- ✅ Priorizas la seguridad
- ✅ Necesitas monitoreo 24/7

### Usa FERSXMET si:
- ✅ Necesitas monitoreo meteorológico
- ✅ Quieres un diseño moderno
- ✅ Prefieres personalización visual
- ✅ Necesitas mapas de calor térmicos

---

**Ambas apps comparten la misma base técnica pero sirven propósitos diferentes. GASOX es para seguridad, FERSXMET es para monitoreo ambiental.**
