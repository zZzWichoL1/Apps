# 🚀 Guía Rápida - Sistemas IoT ESP32

Configuración rápida para poner en marcha cualquiera de los 3 proyectos.

---

## 📋 Requisitos Previos

### Software
- ✅ Arduino IDE 1.8.19 o superior
- ✅ Flutter SDK 3.0 o superior
- ✅ Android Studio / VS Code
- ✅ Drivers USB (CH340/CP2102)

### Hardware
- ✅ ESP32 DevKit
- ✅ Cable USB
- ✅ Sensores del proyecto elegido
- ✅ Cables jumper

---

## ⚡ Configuración en 10 Minutos

### Paso 1: Configurar Arduino IDE (2 min)

1. **Instalar soporte ESP32:**
```
Archivo → Preferencias → URLs adicionales:
https://dl.espressif.com/dl/package_esp32_index.json
```

2. **Instalar placa ESP32:**
```
Herramientas → Placa → Gestor de tarjetas
Buscar: "esp32"
Instalar: "ESP32 by Espressif Systems"
```

3. **Instalar librerías necesarias:**
```
Herramientas → Administrar bibliotecas
Instalar:
- WiFiManager
- ArduinoJson
- [Librerías específicas del proyecto]
```

---

### Paso 2: Cargar Código ESP32 (3 min)

1. **Abrir código:**
```
Archivo → Abrir → [proyecto].ino
```

2. **Configurar placa:**
```
Herramientas → Placa → ESP32 Dev Module
Herramientas → Puerto → [tu puerto COM]
```

3. **Cargar código:**
```
Sketch → Subir
```

4. **Verificar en Monitor Serial:**
```
Herramientas → Monitor Serial (115200 baud)
Debe mostrar: "WiFi conectado! IP: 192.168.X.X"
```

---

### Paso 3: Configurar WiFi (2 min)

1. **Conectar a red del ESP32:**
```
Red WiFi: [Nombre del proyecto]
Contraseña: (ninguna)
```

2. **Abrir portal:**
```
Se abre automáticamente o ir a: 192.168.4.1
```

3. **Configurar red:**
```
Seleccionar tu red WiFi
Ingresar contraseña
Guardar
```

4. **Anotar IP:**
```
El ESP32 muestra su IP en el Monitor Serial
Ejemplo: 192.168.1.100
```

---

### Paso 4: Ejecutar App Flutter (3 min)

1. **Instalar dependencias:**
```bash
cd [carpeta-proyecto]
flutter pub get
```

2. **Ejecutar app:**
```bash
flutter run
```

3. **Configurar conexión:**
```
En la app:
Ajustes → Configurar ESP32
Ingresar IP: 192.168.1.100
Probar Conexión
```

---

## 🔌 Conexiones de Hardware

### GASOX
```
MQ4:
- VCC → 5V
- GND → GND
- AO → GPIO 34

MQ7:
- VCC → 5V
- GND → GND
- AO → GPIO 35

LED → GPIO 13
Buzzer → GPIO 26
```

### FERSXMET
```
DHT22:
- VCC → 3.3V
- GND → GND
- DATA → GPIO 4

MLX90614:
- VCC → 3.3V
- GND → GND
- SDA → GPIO 16
- SCL → GPIO 17

BH1750:
- VCC → 3.3V
- GND → GND
- SDA → GPIO 21
- SCL → GPIO 22
```

### DrHome
```
MAX30102:
- VCC → 3.3V
- GND → GND
- SDA → GPIO 16
- SCL → GPIO 17

MLX90614:
- VCC → 3.3V
- GND → GND
- SDA → GPIO 21
- SCL → GPIO 22
```

---

## ✅ Verificación

### ESP32 Funciona Si:
- ✅ Monitor Serial muestra "Servidor iniciado"
- ✅ Tiene una IP asignada
- ✅ Responde a ping: `ping 192.168.1.100`

### App Funciona Si:
- ✅ Muestra "Conectado" (luz verde)
- ✅ Valores se actualizan en tiempo real
- ✅ Puedes guardar datos

---

## 🐛 Solución Rápida de Problemas

### ESP32 no carga código
```
✅ Verifica cable USB
✅ Instala drivers CH340/CP2102
✅ Selecciona puerto COM correcto
✅ Presiona botón BOOT al cargar
```

### ESP32 se reinicia constantemente
```
✅ Usa cargador de pared 5V 2A
✅ No uses puerto USB de PC
✅ Desconecta sensores al cargar
```

### App no conecta
```
✅ Verifica IP correcta
✅ Ambos en la misma red WiFi
✅ Desactiva datos móviles
✅ Prueba con PowerShell primero
```

### Sensores no responden
```
✅ Verifica conexiones
✅ Revisa voltaje (3.3V o 5V según sensor)
✅ Escanea I2C en Monitor Serial
```

---

## 🧪 Prueba de Conexión (PowerShell)

Antes de usar la app, prueba con PowerShell:

```powershell
$IP = "192.168.1.100"  # Tu IP
$client = New-Object System.Net.Sockets.TcpClient($IP, 8080)
$stream = $client.GetStream()
$writer = New-Object System.IO.StreamWriter($stream)
$reader = New-Object System.IO.StreamReader($stream)

$writer.WriteLine("GET_STATUS")
$writer.Flush()
Start-Sleep -Milliseconds 500

$response = $reader.ReadLine()
Write-Host $response

$client.Close()
```

**Debe responder con JSON.**

---

## 📱 Primer Uso de la App

### GASOX
1. Configurar umbrales de gas
2. Probar alarma
3. Ver lecturas en tiempo real

### FERSXMET
1. Ver datos meteorológicos
2. Revisar historial
3. Exportar datos

### DrHome
1. Agregar paciente
2. Realizar medición
3. Ver diagnóstico automático
4. Guardar en historial

---

## 🎯 Próximos Pasos

1. ✅ Revisa README.md de cada proyecto
2. ✅ Consulta DOCUMENTACION_TECNICA.md para detalles
3. ✅ Personaliza según tus necesidades

---

## ⚡ Comandos Útiles

### Arduino IDE
```
Ctrl+U - Subir código
Ctrl+Shift+M - Monitor Serial
Ctrl+R - Verificar código
```

### Flutter
```bash
flutter pub get          # Instalar dependencias
flutter run             # Ejecutar app
flutter clean           # Limpiar build
flutter doctor          # Verificar instalación
```

---

## 📞 Checklist Final

- [ ] Arduino IDE configurado
- [ ] Librerías instaladas
- [ ] Código ESP32 cargado
- [ ] WiFi configurado
- [ ] IP anotada
- [ ] Sensores conectados
- [ ] App Flutter ejecutándose
- [ ] Conexión exitosa
- [ ] Datos en tiempo real

---

**¡Listo! Tu sistema IoT está funcionando.** 🎉

Para más detalles, consulta DOCUMENTACION_TECNICA.md
