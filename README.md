# Introduction to Creating RAGs

Este repositorio contiene material de ejemplo para aprender a crear sistemas RAG (Retrieval-Augmented Generation). Todo el código y las instrucciones están en el notebook principal:

- `rag/rag.ipynb`

## Arquitectura y componentes del proyecto

El proyecto está estructurado como una pequeña demo basada en notebooks. Componentes principales:

- Notebooks
  - `rag/rag.ipynb` — Notebook principal que contiene el flujo completo: ingestión de datos, creación de vectores, embeddings, configuración del modelo y ejemplos de consultas RAG. (Ruta: `rag/rag.ipynb`)
  - `rag/setup.ipynb` — Notebook auxiliar para configuración.
- Dependencias de Python y entornos virtuales — el notebook usa librerías de Python (Jupyter, bibliotecas de embeddings/LLM, librerías de búsqueda vectorial).

> Nota: el diseño exacto (por ejemplo: tipo de vector store o proveedor de LLM) se define en `rag/rag.ipynb`. Abrir ese notebook para ver las decisiones concretas y las celdas con configuraciones.

### Indexación

<img width="1100" height="553" alt="image" src="https://github.com/user-attachments/assets/11da97ae-a8a1-4d37-bffc-2a83f7b4cebc" />

### Recuperación y generación

<img width="1100" height="564" alt="image" src="https://github.com/user-attachments/assets/c9bf5dd3-281a-489a-b6fb-4895b71ec6c2" />


## Uso de Pinecone como base de datos vectorial

El siguiente código que se encuentra en `rag/rag.ipynb` revisa si existe un índice en Pinecone llamado “langchain-test-index” y, si no está creado, lo genera en modo serverless en AWS con 3072 dimensiones, que es la medida correcta para los embeddings. Luego, establece la conexión con ese índice para que se pueda subir y consultar vectores desde el notebook sin errores.

```python
from pinecone import ServerlessSpec

index_name = "langchain-test-index"  

if not pc.has_index(index_name):
    pc.create_index(
        name=index_name,
        dimension=3072,
        metric="cosine",
        spec=ServerlessSpec(cloud="aws", region="us-east-1"),
    )

index = pc.Index(index_name)
```

Desde el navegador se hace revisión del índce creado:

<img width="2879" height="1525" alt="image" src="https://github.com/user-attachments/assets/14e093e3-9f3c-4f8c-ad1a-e96660e8dc86" />

En la siguiente sección fue donde se realizó por completo la ingestión de datos en la nube:

<img width="2157" height="1169" alt="image" src="https://github.com/user-attachments/assets/4f0c06e2-f49b-45a2-b4b2-69e602499779" />

Así mismo se pueden buscar registros por diferentes filtros:

<img width="2879" height="1536" alt="image" src="https://github.com/user-attachments/assets/9c03dddd-d8be-4c7a-b20c-ddd70f1b0cc1" />

<img width="2879" height="1523" alt="image" src="https://github.com/user-attachments/assets/98d1b271-1ccc-4e74-ba95-d8f48fc0f446" />


### Referencias

* **Documentación de LangChain: RAG**

  Aquí:
    [LangChain RAG Documentation](https://docs.langchain.com/oss/python/langchain/rag)

* **Documentación de pinecone**

  Aquí:
    [Pinecone Documentation](https://docs.langchain.com/oss/python/integrations/vectorstores/pinecone)
