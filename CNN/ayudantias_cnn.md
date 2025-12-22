# Temas de Ayudantía - Clasificador de imágenes con redes neuronales

## Módulo 1: Fundamentos de Herramientas

### 1. Git y GitHub desde cero
- **Conceptos básicos**: repositorio, commit, branch, push, pull, merge
- Creación de cuenta GitHub y configuración inicial (SSH keys)
- Primer repositorio: estructura y organización para proyectos de ML
- Archivo `.gitignore` para proyectos de ML (modelos, datos, checkpoints, `__pycache__`)
- Flujo de trabajo básico: add, commit, push
- Comandos esenciales que se usarán durante el semestre
- Resolución de conflictos comunes

### 2. Markdown y documentación técnica
- Sintaxis básica de Markdown: encabezados, listas, código, enlaces, imágenes
- Estructura de un README.md profesional
- Documentación de experimentos y resultados en notebooks
- Plantilla de README para el proyecto del curso
- Tablas y fórmulas matemáticas en Markdown
- GitHub Pages básico (opcional para portafolio personal)

### 3. Entorno de desarrollo Python
- **Gestores de paquetes modernos**: `venv` vs `uv` (Astral) - ventajas y casos de uso
- Instalación y configuración de `uv`
- Gestión de dependencias: `requirements.txt` y `pyproject.toml`
- Creación de ambientes virtuales con `uv venv`
- Instalación rápida de paquetes con `uv pip`
- Jupyter Notebooks vs scripts (`.py`): cuándo usar cada uno
- Estructura de directorios profesional para proyectos de ML
- Buenas prácticas: nomenclatura, modularización, separación de código y datos

### 4. Google Colab y recursos en la nube
- Configuración de Google Colab (gratuito y Pro)
- Conexión con Google Drive para persistencia de datos
- Instalación y gestión de librerías (PyTorch, Hugging Face, etc.)
- Gestión de sesiones y uso eficiente de GPU/TPU
- Límites y mejores prácticas de uso
- Alternativas gratuitas: Kaggle Notebooks, Paperspace Gradient

## Módulo 2: APIs y Servicios Web

### 5. Consumo de APIs REST
- ¿Qué es una API REST? Conceptos fundamentales
- Métodos HTTP: GET, POST, PUT, DELETE
- Librería `requests` en Python
- Manejo de autenticación y headers
- Procesamiento de respuestas JSON
- Ejemplo práctico: consumo de API pública

### 6. Creación de APIs con FastAPI
- Instalación y configuración de FastAPI
- Estructura básica de una aplicación
- Definición de endpoints y modelos de datos (Pydantic)
- Testing local con Uvicorn
- Documentación automática (Swagger UI)
- Integración con modelos de ML
- Consumo de la API desde otras aplicaciones

## Módulo 3: Hugging Face Ecosystem

### 7. Primeros pasos con Hugging Face
- Introducción al ecosistema Hugging Face
- Navegación del Hub de modelos y datasets
- Carga de modelos preentrenados con `transformers`
- Primeras inferencias: clasificación de imágenes y texto
- Exploración y carga de datasets con `datasets`
- Autenticación y uso de modelos privados

### 8. Uso avanzado de modelos preentrenados
- Fine-tuning vs Transfer Learning: conceptos clave
- Selección del modelo adecuado según la tarea
- Configuración de hiperparámetros
- Uso de `pipeline` para inferencia rápida
- Optimización de modelos: cuantización y pruning básico
- Manejo de diferentes modalidades (visión, texto, multimodal)

## Módulo 4: Despliegue y Producción

### 9. Docker y contenedores para ML
- **Conceptos básicos**: imágenes, contenedores, volúmenes, redes
- Instalación de Docker y Docker Desktop
- Creación de `Dockerfile` para proyectos de ML
- Gestión de dependencias y layers
- **Best practices**: 
  - Multi-stage builds para reducir tamaño
  - Cache de capas para builds rápidos
  - Archivo `.dockerignore` optimizado
- Push a Docker Hub o GitHub Container Registry
- Docker Compose para orquestar múltiples servicios

### 10. Despliegue de modelos en producción
- Opciones de deployment: Hugging Face Spaces, Render, Railway
- Containerización de API con modelo integrado
- Variables de entorno y configuración
- Monitoreo básico y logs
- Consideraciones de costo y escalabilidad

## Módulo 5: Presentación de Resultados

### 11. Preparación de la presentación final (Latex)
- Estructura de presentación técnica
- Visualizaciones efectivas
- Ensayo y retroalimentación
