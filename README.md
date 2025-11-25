# EcoScan Backend

Backend para la aplicación **EcoScan**, diseñado para ayudar en la clasificación de residuos y promover la educación ambiental en Colombia mediante el uso de Inteligencia Artificial.

## 🚀 Características

- **Análisis de Imágenes con IA**: Clasifica fotos de residuos en los contenedores de reciclaje correspondientes (Blanco, Negro, Verde) según la normativa colombiana.
- **Generación de Quiz**: Crea preguntas dinámicas de reciclaje con imágenes generadas por IA.
- **Consejos Ambientales**: Proporciona tips prácticos y motivadores sobre el cuidado del medio ambiente.

## 🛠️ Tecnologías Utilizadas

- **Node.js** & **Express**: Servidor y API REST.
- **Google Generative AI (Gemini)**:
  - Modelo `gemini-2.5-flash-image` para análisis de imágenes y generación de imágenes para el quiz.
- **Groq SDK**: Generación de texto para preguntas del quiz y consejos ambientales.
- **Multer**: Manejo de subida de imágenes en memoria.

## 📋 Requisitos Previos

- [Node.js](https://nodejs.org/) (v14 o superior)
- Una cuenta y API Key de [Google AI Studio](https://aistudio.google.com/) (para Gemini).
- Una cuenta y API Key de [Groq](https://groq.com/).

## ⚙️ Instalación

1. **Clonar el repositorio** (o descargar los archivos):
   ```bash
   git clone <url-del-repositorio>
   cd EcoScan_Backend
   ```

2. **Instalar dependencias**:
   ```bash
   npm install
   ```

3. **Configurar variables de entorno**:
   Crea un archivo `.env` en la raíz del proyecto y añade tus claves de API:
   ```env
   GEMINI_API_KEY=tu_api_key_de_google
   GROQ_API_KEY=tu_api_key_de_groq
   ```

## ▶️ Ejecución

Para iniciar el servidor en modo desarrollo o producción:

```bash
npm start
# O
npm run dev
```

El servidor iniciará en `http://localhost:3000`.

## 📡 Endpoints de la API

### 1. Analizar Residuo
**POST** `/api/analyze`

Clasifica una imagen subida.

- **Body (form-data)**:
  - `image`: Archivo de imagen (jpg, png, etc.).
- **Respuesta (JSON)**:
  ```json
  {
    "container": "Blanco (Aprovechables)",
    "details": {
      "confidence": "Alta",
      "objectName": "Botella de plástico",
      "reason": "Es un material reciclable limpio y seco."
    }
  }
  ```

### 2. Crear Pregunta de Quiz
**GET** `/api/create`

Genera una pregunta aleatoria para el juego de reciclaje.

- **Respuesta (JSON)**:
  ```json
  {
    "imageUrl": "data:image/png;base64,...",
    "wasteName": "Lata de aluminio",
    "correctContainer": "Blanco (Aprovechables)",
    "justification": "El aluminio es un metal altamente reciclable."
  }
  ```

### 3. Obtener Consejo Ambiental
**GET** `/api/tips`

Obtiene un consejo breve sobre sostenibilidad.

- **Respuesta (JSON)**:
  ```json
  {
    "tip": "Lleva tu propia bolsa reutilizable al supermercado y reduce el uso de plástico."
  }
  ```

## 🗑️ Código de Colores (Colombia)

El sistema sigue la resolución 2184 de 2019 para el código de colores en Colombia:
- ⚪ **Blanco**: Residuos aprovechables (plástico, cartón, vidrio, papel, metales).
- 🟢 **Verde**: Residuos orgánicos aprovechables (restos de comida, desechos agrícolas).
- ⚫ **Negro**: Residuos no aprovechables (papel higiénico, servilletas, cartones contaminados).
