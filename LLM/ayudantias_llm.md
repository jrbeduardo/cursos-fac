# Temas de Ayudantía - Introducción a los Large Language Models

## Fundamentos de Herramientas

### 1. Git y GitHub desde cero
- Conceptos básicos: repositorio, commit, push, pull
- Creación de cuenta GitHub y configuración inicial
- Primer repositorio: estructura para proyecto de tesis
- `.gitignore` para proyectos de ML (modelos, datos, checkpoints)
- Comandos esenciales que usarán todo el semestre

### 2. Markdown y documentación
- Sintaxis básica de Markdown
- Estructura de README.md profesional
- Documentación de experimentos en notebooks
- Plantilla de README para el proyecto del curso
- GitHub Pages básico (opcional para portafolio)

### 3. Docker y contenedores para ML
- Conceptos básicos de Docker: imágenes, contenedores, volúmenes
- Instalación de Docker y Docker Desktop
- Creación de Dockerfile para proyectos de ML:
- Dockerización de modelo con FastAPI
- Docker Compose para servicios múltiples (API + base de datos vectorial)
- Best practices: multi-stage builds, cache de capas, .dockerignore
- Push a Docker Hub o GitHub Container Registry

### 4. Entorno de desarrollo Python
- Ambientes virtuales: venv vs conda
- Archivo `requirements.txt` y `environment.yml`
- Jupyter notebooks vs scripts (.py): cuándo usar cada uno
- Organización de directorios para proyectos ML.


## Setup Técnico para LLMs

### 5. Google Colab y recursos GPU
- Configuración de Colab (gratuito y Pro)
- Conectar Google Drive
- Instalación de librerías (Hugging Face, PyTorch)
- Gestión de sesiones y persistencia de datos
- Alternativas: Kaggle Notebooks

### 6. Primeros pasos con Hugging Face
- Navegación del Hub de modelos
- Carga de modelos preentrenados básicos
- Primeras inferencias (generación de texto simple)
- Datasets: exploración y carga

### 7. Introducción a Ollama
- Ejecutar LLMs localmente de forma simple.
- Instalación desde https://ollama.ai y verificación con `ollama --version`
- Comandos básicos: `ollama run llama3.2`, `ollama pull mistral`, `ollama list`, `ollama rm modelo`
- Modelos disponibles: LLaMA 3.2, Mistral, Phi-3, CodeLlama, Gemma 
- Uso interactivo en terminal y comparación con Hugging Face (cuándo usar cada uno)

## Uso de modelos LLMs

### 8. Uso de Hugging Face
- Uso correcto de modelos preentrenados
- Carga de modelos y tokenizadores (HF).
- Diferencias encoder/decoder/decoder-only.
- Inferencia básica y establecimiento de baseline.

### 9. Casos de uso y personalización de Ollama
- API REST local (localhost:11434): integración con Python usando `requests` o librerías específicas
- Integración con LangChain para construcción de pipelines y chatbots
- Personalización con Modelfiles: system prompts customizados, temperatura, plantillas de prompts
- Casos de uso para el proyecto: prototipado rápido, baseline comparativo, generación de datos sintéticos

### 10. Pipeline de datos
- Carga de datasets (CSV, JSON, Parquet)
- Análisis exploratorio de texto
- Estadísticas básicas: longitud, vocabulario, distribuciones
- Limpieza de datos común

## Deployment 

### 11. FastAPI para modelos
- API básica de inferencia
- Manejo de requests
- Testing local

### 12. Gradio/Streamlit
- Demo interactivo
- Deploy en Hugging Face Spaces
- Compartir el trabajo


## Preparación de presentación final (LaTeX)

### 13. Preparación de presentación final
- Estructura de presentación técnica
- Visualizaciones efectivas
- Ensayo y retroalimentación