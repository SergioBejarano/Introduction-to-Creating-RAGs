# Introduction to Creating RAGs

Este repositorio contiene material de ejemplo para aprender a crear sistemas RAG (Retrieval-Augmented Generation). Todo el código y las instrucciones están en el notebook principal:

- `rag/rag.ipynb`

## Arquitectura y componentes del proyecto

El proyecto está estructurado como una pequeña demo basada en notebooks. Componentes principales:

- Notebooks
  - `rag/rag.ipynb` — Notebook principal que contiene el flujo completo: ingestión de datos, creación de vectores, embeddings, configuración del modelo y ejemplos de consultas RAG. (Ruta: `rag/rag.ipynb`)
  - `rag/setup.ipynb` — Notebook auxiliar para pasos de configuración o experimentos de preparación.
- Dependencias de Python y entornos virtuales — el notebook usa librerías de Python (Jupyter, bibliotecas de embeddings/LLM, librerías de búsqueda vectorial).

> Nota: el diseño exacto (por ejemplo: tipo de vector store o proveedor de LLM) se define en `rag/rag.ipynb`. Abrir ese notebook para ver las decisiones concretas y las celdas con configuraciones.
