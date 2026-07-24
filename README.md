# challenge-ia
plataforma digital
# ✏️ LápizDigital - Plataforma SaaS & Agente IA de Soporte

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Framework](https://img.shields.io/badge/LangChain-RAG-green)
![Interface](https://img.shields.io/badge/Streamlit-UI-red)
![Cloud](https://img.shields.io/badge/Oracle_Cloud-OCI_Deployed-orange)
![License](https://img.shields.io/badge/License-MIT-brightgreen)

## 📌 1. Descripción General del Proyecto

**LápizDigital** es una plataforma digital moderna enfocada en la distribución, catálogo interactivo y suscripciones para herramientas de escritura, dibujo técnico y bellas artes (lápices de grafito, acuarelables, estilográficas y tabletas digitales). 

Para mejorar la experiencia de atención al cliente y resolver dudas sobre productos, envíos, garantías y planes de suscripción, el proyecto integra un **Agente Inteligente con arquitectura RAG (Retrieval-Augmented Generation)**. Este agente procesa la base de conocimiento oficial (documentos PDF/CSV) para ofrecer respuestas precisas y automatizadas las 24 horas.

## 🏗️ 2. Arquitectura de la Solución

El sistema funciona bajo una arquitectura RAG desacoplada y desplegada en la nube:
[ Usuario ] ──> [ Interfaz Web (Streamlit) ]
│
▼
[ Carga y Lectura de PDF / CSV ]
│
▼
[ Chunking + Embeddings (Vector Store) ]
│
▼
[ Agente LLM + LangChain ]
│
▼
[ Generación de Respuesta Contextualizada ]

1. **Ingesta de Documentos:** Un módulo en Python procesa y segmenta (*chunking*) la base de conocimiento cargada en formato PDF/CSV.
2. **Vectorización e Indexación:** Los textos procesados se convierten en vectores mediante un modelo de embeddings y se almacenan en una base de datos vectorial (Vector Store).
3. **Recuperación y Generación:** Ante una consulta del usuario, el sistema busca los fragmentos con mayor relevancia semántica y los inyecta en el prompt del LLM para estructurar una respuesta fiel al documento fuente.

## 🛠️ Tecnologías y Herramientas Utilizadas

* **Lenguaje de Programación:** Python 3.10+
* **Framework RAG & IA:** LangChain / LlamaIndex
* **Procesamiento de Documentos:** PyPDF, PDFPlumber o Pandas (según el formato PDF/CSV)
* **Base de Datos Vectorial:** FAISS / ChromaDB
* **Modelos de Lenguaje (LLM):** OpenAI API / Cohere / HuggingFace
* **Interfaz Gráfica de Usuario:** Streamlit
* **Infraestructura Cloud:** Oracle Cloud Infrastructure (OCI)

## 🚀 Instrucciones para Ejecutar el Proyecto

### Prerrequisitos
* Tienes instalado Python 3.10 o superior.
* Cuentas con una API Key válida para el modelo de lenguaje (ej. `OPENAI_API_KEY`).

### Pasos de Instalación Local

1. **Clonar el repositorio:**
   ```bash
   git clone [https://github.com/tu-usuario/lapizdigital-agente-ia.git](https://github.com/tu-usuario/lapizdigital-agente-ia.git)
   cd lapizdigital-agente-ia

## 🛠️ 3. Tecnologías y Herramientas Utilizadas

* **Lenguaje:** Python 3.10+
* **Framework RAG / IA:** LangChain / LlamaIndex
* **Modelo LLM:** OpenAI / Cohere / HuggingFace
* **Procesamiento de Documentos:** PyPDF / Pandas (para archivos PDF/CSV)
* **Vector Store:** FAISS / ChromaDB
* **Interfaz de Usuario:** Streamlit
* **Infraestructura Cloud:** Oracle Cloud Infrastructure (OCI) - Compute Instance & Docker Container

## 📂 4. Estructura del Repositorio

```micro
lapizdigital-agente-ia/
├── data/
│   └── base_conocimiento_lapices.pdf  # Documento fuente de información
├── src/
│   ├── __init__.py
│   ├── document_loader.py            # Lectura y procesado de PDF/CSV
│   ├── vector_store.py              # Generación de embeddings
│   └── agent.py                     # Lógica principal del agente RAG
├── app.py                            # Interfaz gráfica Streamlit
├── requirements.txt                  # Dependencias del proyecto
├── .env.example                      # Plantilla de variables de entorno
└── README.md                         # Documentación del proyecto

## 5❓ Ejemplos de Preguntas que el Agente Puede Responder

Sobre productos: "¿Cuáles son las diferencias entre los lápices de grafito con graduación 2B, HB y 4H?"
Sobre el catálogo: "¿Qué lápices son los más recomendados para acuarela y dibujo técnico profesional?"
Sobre envíos y precios: "¿Cuál es el costo de envío para compras al por mayor y qué planes de suscripción ofrecen?"
Sobre garantías: "¿Qué hago si recibo un set de lápices defectuoso o roto durante el traslado?"

💬 Ejemplos de Respuestas Generadas por el Agente

Ejemplo 1: Consulta de Especificaciones Técnicas
Pregunta: "¿Cuáles son las diferencias entre los lápices de grafito con graduación 2B, HB y 4H?"

Respuesta generada:
"De acuerdo con el catálogo de LápizDigital:

4H: Es un lápiz de mina dura y clara, ideal para trazados finos y dibujo técnico de precisión.*
HB: Posee un tono de dureza media, siendo la opción estándar y versátil para escritura diaria.*
2B: Cuenta con un grafito más suave y oscuro, perfecto para sombreado artístico y bocetos libres."*

Ejemplo 2: Consulta sobre Envíos y Políticas
Pregunta: "¿Cuál es el costo de envío para compras al por mayor?"

Respuesta generada:
"Según la sección de Políticas y Envíos del documento:
Las compras al por mayor o los pedidos superiores a $50 USD cuentan con envío estándar totalmente gratuito. Para pedidos de menor valor, el costo de envío nacional fijo es de $3.50 USD y tarda entre 48 a 72 horas hábiles en ser entregado."
