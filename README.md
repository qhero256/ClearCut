# 🎬 Qhero ClearCut v3.40 (Total Control Edition)

![Python](https://img.shields.io/badge/Python-3.10.8-blue?style=for-the-badge&logo=python)
![FFmpeg](https://img.shields.io/badge/FFmpeg-Required-green?style=for-the-badge&logo=ffmpeg)
![Status](https://img.shields.io/badge/Status-Stable-success?style=for-the-badge)

---

## 🇪🇸 Descripción en Español

**Qhero ClearCut** es una herramienta automatizada de post-producción de video y audio diseñada para creadores de contenido. Transforma grabaciones "crudas" en material listo para publicar (Broadcast Quality) mediante el uso de Inteligencia Artificial y procesamiento de señal digital (DSP).

Esta herramienta no solo corta los silencios automáticamente, sino que limpia, nivela, ecualiza y masteriza tu voz para que suene como un locutor de radio, solucionando además problemas técnicos de video como pantallas negras o desincronización.

---

## 🚀 Características Principales

* **✂️ Edición Automática (Jump-cuts):** Detecta y elimina silencios basándose en el volumen de tu voz.
* **🧠 Limpieza con IA (DeepFilterNet):** Elimina ruidos de fondo complejos (ventiladores, tecleo, tráfico) sin dañar la voz.
* **🎛️ Masterización DSP "Broadcast":** Cadena de efectos profesional integrada:
    * *Voice Deepener:* Añade cuerpo y autoridad.
    * *Surgical EQ:* Elimina el sonido de "caja" o habitación pequeña.
    * *De-Esser:* Suaviza las "S" y "Ch" molestas.
    * *Voice Leveler:* Mantiene el volumen de voz constante.
    * *Noise Gate:* Silencio absoluto digital cuando no hablas.
* **🛡️ Video Bulletproof:** Convierte videos con tasa de cuadros variable (VFR) a 30fps constantes (H.264) para evitar errores de renderizado y pantallas negras.
* **🔀 Modo "Selective Master":** Interruptor para elegir entre **Solo Cortes** (sin tocar el audio) o **Procesamiento Completo**.
* **🌍 Universal:** Soporta casi cualquier formato de entrada (`.mp4`, `.mkv`, `.mov`, `.mp3`, `.wav`, etc.).

---

## 🛠️ Requisitos Previos (Instalación)

Para usar este script, necesitas instalar algunas herramientas en tu computadora. Sigue estos pasos según tu sistema operativo.

### 1. Python (El Motor)
Este script está optimizado para **Python 3.10.x**. Versiones muy nuevas (como 3.12) pueden tener conflictos con librerías de audio.
* **Windows/Mac/Linux:** Descarga Python 3.10.8 desde [python.org](https://www.python.org/downloads/release/python-3108/).
* ⚠️ **Importante al instalar en Windows:** Marca la casilla **"Add Python to PATH"** antes de dar clic en instalar.

### 2. FFmpeg (El Procesador Multimedia)
Es vital para leer y escribir video. Sin esto, el script no funcionará.

* **Windows:**
    1.  Descarga la "full build" desde [gyan.dev](https://www.gyan.dev/ffmpeg/builds/).
    2.  Descomprime la carpeta y renómbrala a `ffmpeg`. Muévela a `C:\ffmpeg`.
    3.  Abre "Editar las variables de entorno del sistema" en Windows.
    4.  Ve a "Variables de entorno" -> Busca la variable `Path` en "Variables del sistema" -> "Editar" -> "Nuevo".
    5.  Escribe: `C:\ffmpeg\bin` y guarda todo.
* **Mac (usando Homebrew):**
    * Abre la terminal y escribe: `brew install ffmpeg`
* **Linux (Ubuntu/Debian):**
    * Abre la terminal y escribe: `sudo apt update && sudo apt install ffmpeg`

### 3. Git (Opcional, para descargar este repo)
* Descarga e instala desde [git-scm.com](https://git-scm.com/).

### 4. Editor de Código
Recomendamos **Visual Studio Code (VS Code)**.
1.  Descárgalo [aquí](https://code.visualstudio.com/).
2.  Instala la extensión de **Python** y la extensión de **Jupyter** dentro de VS Code.

---

## 📦 Instalación de Librerías

Una vez instalado Python, abre tu terminal (o CMD) e instala las dependencias necesarias copiando y pegando este comando:

```bash
pip install rich auto-editor deepfilternet numpy soundfile torch torchaudio
```

⚠️ Nota: Si tienes tarjeta gráfica NVIDIA, se recomienda instalar la versión de PyTorch con CUDA para que la IA vuele (aunque el script funciona en CPU).

---

## ⚙️ Configuración y Uso
El script está diseñado como un Jupyter Notebook (.ipynb).

1. Abre el archivo Qhero ClearCut v3.40.ipynb en VS Code o Jupyter Lab.
2. Dirígete a la celda "🎛️ ZONA DE CONFIGURACIÓN MAESTRA" al inicio del script.
3. Modifica los parámetros según tu necesidad:

```bash
CONFIG = {
    # MODO DE OPERACIÓN:
    # True = Solo corta silencios (Rápido, audio original).
    # False = Aplica IA, EQ, Compresión y Cortes (Calidad Pro).
    "SOLO_CORTES": False,

    # RUTA DEL ARCHIVO (Video o Audio):
    "ARCHIVO": r"C:\Tus_Documentos\Videos\mi_grabacion.mp4",

    # AJUSTES DE AUDIO (Ejemplos):
    "HIGHPASS_FREQ": "115",      # Cortar graves (moto, golpes)
    "GATE_THRESHOLD": "-35dB",   # Nivel para silenciar fondo
    "DEESSER_INTENSITY": "0.4",  # Suavizar 'S'

    # CALIDAD DE VIDEO:
    "VIDEO_CRF": "20",           # Calidad (18=Cine, 23=YouTube)
    "VIDEO_FPS": "30",           # FPS fijos para evitar errores
}
```
4. Ejecuta la celda del script (Botón "Play" o Shift + Enter).
5. Verás un Dashboard visual indicando el progreso.
6. Al finalizar, el archivo se guardará en la misma carpeta con el sufijo _V40_Master.mp4.

---

### ☁️ Ejecución en Google Colab
Si no tienes una PC potente, puedes ejecutar esto en la nube de Google.

1. Sube el archivo .ipynb a Google Colab.
2. Crea una celda al principio e instala las dependencias del sistema linux de Colab:

```bash
!apt-get install ffmpeg
!pip install rich auto-editor deepfilternet numpy soundfile torch torchaudio
```
3. Sube tu video a la carpeta de archivos de Colab.
4. Cambia la ruta en CONFIG (ej: "/content/mi_video.mp4").
5. Ejecuta el script.

---

### 📝 Créditos
Desarrollado para optimizar flujos de trabajo de creación de contenido. Basado en tecnologías Open Source: Auto-Editor, DeepFilterNet y FFmpeg.

---

⚠️ Disclaimer: 
Este script realiza cambios permanentes en el archivo de salida. Siempre conserva una copia de seguridad de tu archivo original.

---

## 🇬🇧 Description in English

**Qhero ClearCut** is an automated video and audio post-production tool designed for content creators. It transforms "raw" recordings into publish-ready material (Broadcast Quality) by using Artificial Intelligence and digital signal processing (DSP).

This tool not only cuts silences automatically, but also cleans, levels, equalizes, and masters your voice so it sounds like a radio announcer—while also fixing technical video issues such as black screens or desynchronization.

---

## 🚀 Key Features

* **✂️ Automatic Editing (Jump-cuts):** Detects and removes silences based on your voice volume.
* **🧠 AI Cleanup (DeepFilterNet):** Removes complex background noise (fans, typing, traffic) without harming the voice.
* **🎛️ "Broadcast" DSP Mastering:** Built-in professional effects chain:
    * *Voice Deepener:* Adds body and authority.
    * *Surgical EQ:* Removes the "boxy" or small-room sound.
    * *De-Esser:* Softens harsh "S" and "Ch" sounds.
    * *Voice Leveler:* Keeps voice volume consistent.
    * *Noise Gate:* Total digital silence when you're not speaking.
* **🛡️ Video Bulletproof:** Converts variable frame rate (VFR) videos to constant 30fps (H.264) to prevent rendering errors and black screens.
* **🔀 "Selective Master" Mode:** Toggle to choose between **Cuts Only** (without touching the audio) or **Full Processing**.
* **🌍 Universal:** Supports almost any input format (`.mp4`, `.mkv`, `.mov`, `.mp3`, `.wav`, etc.).

---

## 🛠️ Prerequisites (Installation)

To use this script, you need to install a few tools on your computer. Follow these steps depending on your operating system.

### 1. Python (The Engine)
This script is optimized for **Python 3.10.x**. Very new versions (like 3.12) may conflict with audio libraries.
* **Windows/Mac/Linux:** Download Python 3.10.8 from [python.org](https://www.python.org/downloads/release/python-3108/).
* ⚠️ **Important when installing on Windows:** Check **"Add Python to PATH"** before clicking install.

### 2. FFmpeg (The Multimedia Processor)
It’s vital for reading and writing video. Without this, the script will not work.

* **Windows:**
    1.  Download the "full build" from [gyan.dev](https://www.gyan.dev/ffmpeg/builds/).
    2.  Extract the folder and rename it to `ffmpeg`. Move it to `C:\ffmpeg`.
    3.  Open "Edit the system environment variables" on Windows.
    4.  Go to "Environment Variables" -> Find the `Path` variable in "System variables" -> "Edit" -> "New".
    5.  Type: `C:\ffmpeg\bin` and save everything.
* **Mac (using Homebrew):**
    * Open Terminal and run: `brew install ffmpeg`
* **Linux (Ubuntu/Debian):**
    * Open Terminal and run: `sudo apt update && sudo apt install ffmpeg`

### 3. Git (Optional, to download this repo)
* Download and install it from [git-scm.com](https://git-scm.com/).

### 4. Code Editor
We recommend **Visual Studio Code (VS Code)**.
1.  Download it [here](https://code.visualstudio.com/).
2.  Install the **Python** extension and the **Jupyter** extension inside VS Code.

---

## 📦 Installing Libraries

Once Python is installed, open your terminal (or CMD) and install the required dependencies by copying and pasting this command:

```bash
pip install rich auto-editor deepfilternet numpy soundfile torch torchaudio
```

⚠️ Note: If you have an NVIDIA graphics card, it’s recommended to install the PyTorch build with CUDA so the AI flies (although the script works on CPU).

---

## ⚙️ Configuration and Usage
The script is designed as a Jupyter Notebook (.ipynb).

1. Open the file Qhero ClearCut v3.40.ipynb in VS Code or Jupyter Lab.
2. Go to the cell "🎛️ ZONA DE CONFIGURACIÓN MAESTRA" at the start of the script.
3. Modify the parameters as needed:

```bash
CONFIG = {
    # OPERATION MODE:
    # True = Only cut silences (Fast, original audio).
    # False = Apply AI, EQ, Compression and Cuts (Pro Quality).
    "SOLO_CORTES": False,

    # FILE PATH (Video or Audio):
    "ARCHIVO": r"C:\Tus_Documentos\Videos\mi_grabacion.mp4",

    # AUDIO SETTINGS (Examples):
    "HIGHPASS_FREQ": "115",      # Cut low end (motorbike, bumps)
    "GATE_THRESHOLD": "-35dB",   # Level to silence background
    "DEESSER_INTENSITY": "0.4",  # Soften 'S'

    # VIDEO QUALITY:
    "VIDEO_CRF": "20",           # Quality (18=Cinema, 23=YouTube)
    "VIDEO_FPS": "30",           # Fixed FPS to avoid errors
}
```
4. Run the script cell (Play button or Shift + Enter).
5. You’ll see a visual Dashboard indicating progress.
6. When finished, the file will be saved in the same folder with the suffix _V40_Master.mp4.

---

### ☁️ Running on Google Colab
If you don’t have a powerful PC, you can run this on Google’s cloud.

1. Upload the .ipynb file to Google Colab.
2. Create a cell at the top and install Colab’s Linux system dependencies:

```bash
!apt-get install ffmpeg
!pip install rich auto-editor deepfilternet numpy soundfile torch torchaudio
```
3. Upload your video to Colab’s file folder.
4. Change the path in CONFIG (e.g.: "/content/mi_video.mp4").
5. Run the script.

---

### 📝 Credits
Developed to optimize content creation workflows. Based on Open Source technologies: Auto-Editor, DeepFilterNet and FFmpeg.

---

⚠️ Disclaimer: 
This script makes permanent changes to the output file. Always keep a backup copy of your original file.

---

Made with ❤️ by [Qhero](https://www.qhero.net)