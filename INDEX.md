# Índice Rápido - LLM Commerce Course

**Navegación rápida para instructores y estudiantes**

---

## 📋 Para Empezar

1. **Primero lee:** [`README.md`](./README.md) - Visión general del curso
2. **Luego revisa:** [`syllabus/SYLLABUS.md`](./syllabus/SYLLABUS.md) - Programa completo

> Nota: El proyecto avanza de forma incremental con foco en el backend LLM; el frontend se mantiene mínimo (chat, catálogo, login).

---

## 🎓 Material por Clase

### Clase 1: Introducción a LLMs (4 nov)
- 📖 [Material completo](./lectures/clase-01/README.md)
- 📊 [Slides](./lectures/clase-01/SLIDES.md)
- 💬 [Ejemplos de Prompts](./lectures/clase-01/demo-prompts.md)
- **Enfoque:** Fundamentos LLM, backlog del proyecto, plan incremental
- **Entregable:** Definición del catálogo inicial + 5 conversaciones objetivo

### Clase 2: Backend Base y Primer Prompt (7 nov)
- 📖 [Material completo](./lectures/clase-02/README.md)
- **Enfoque:** Estructura del repositorio, endpoint `/chat` mínimo, control de prompts
- **Dinámica:** Avance guiado + práctica en clase
- **Entregable:** Backend que responde usando modelo externo/local

> A partir de la Clase 3 cada sesión inicia con **revisión breve de la tarea**, continúa con **avance guiado** y cierra con **práctica supervisada**.

### Clase 3: RAG — Ingesta y Búsqueda (11 nov)
- 📖 [Material completo](./lectures/clase-03/README.md)
- **Revisión:** Catálogo limpio y endpoint `/chat`
- **Avance:** Embeddings del catálogo, buscador semántico en el backend
- **Práctica:** Ajustar prompts para citas con contexto
- **Entregable:** `/catalog/search` operativo + casos de prueba documentados

### Clase 4: Function Calling y Estado de Carrito (14 nov)
- 📖 [Material completo](./lectures/clase-04/README.md)
- **Revisión:** Pruebas de búsqueda semántica
- **Avance:** Definición de funciones (JSON schema) y orquestación del carrito
- **Práctica:** Ejecución de flujos de compra controlados
- **Entregable:** Carrito persistente en backend + prompts instrumentados

### Clase 5: Evaluaciones y Preparación Checkpoint (18 nov)
- 📖 [Material completo](./lectures/clase-05/README.md)
- **Revisión:** Flujos end-to-end del carrito
- **Avance:** Métricas de respuesta, prompts de evaluación, mejoras de recomendaciones
- **Práctica:** Rutinas de pruebas rápidas y logging
- **Entregable:** Script de evaluación + backlog de mejoras para demo

### Clase 6: Presentaciones Parciales (20 nov)
- 📖 [Material completo](./lectures/clase-06/README.md)
- **Actividad:** Presentación del MVP (10 min) + retroalimentación de pares e instructores
- **Entregable:** Demo funcional que integra catálogo, RAG y carrito

### Clase 7: Endurecimiento Backend y Soporte Frontend (25 nov)
- 📖 [Material completo](./lectures/clase-07/README.md)
- **Revisión:** Acciones derivadas del checkpoint
- **Avance:** Validaciones, manejo de errores, autenticación básica y UI mínima (chat, catálogo, login)
- **Práctica:** Testing manual guiado + preparación de deploy local
- **Entregable:** Release candidate con endpoints robustos y front mínimo conectado

### Clase 8: Presentaciones Finales (27 nov)
- 📖 [Material completo](./lectures/clase-08/README.md)
- **Actividad:** Demo final, Q&A y evaluación sumativa
- **Entregable:** Paquete final (repo, docs, video, slides)

---

## 💻 Recursos de Código

### Datasets
- 📦 [Catálogo de productos de ejemplo](./examples/datasets/products.json) - 20 productos listos

### Configuración
- ⚙️ [Variables de entorno template](./examples/.env.example) - Todas las configuraciones necesarias

### Templates (Próximamente)
- 🐍 FastAPI Starter - `templates/fastapi-starter/`
- 🟢 NestJS Starter - `templates/nestjs-starter/`
- ⚛️ React Starter - `templates/react-starter/`

### Ejemplos (Próximamente)
- 🐍 Python Backend Examples - `examples/backend-python/`
- 🟢 Node.js Backend Examples - `examples/backend-nodejs/`
- ⚛️ React Frontend Examples - `examples/frontend-react/`

---

## 🎯 Checklists Rápidos

### Para Estudiantes - Antes de Clase 1
- [ ] Node.js instalado (v18+)
- [ ] Python instalado (3.10+)
- [ ] Git configurado
- [ ] VS Code o IDE preferido
- [ ] Cuenta de GitHub
- [ ] OpenAI API key **o** Ollama instalado

### Para Estudiantes - Proyecto Final
- [ ] README completo
- [ ] Código en GitHub
- [ ] Catálogo ≥20 productos
- [ ] RAG funcionando
- [ ] Function calling implementado
- [ ] UI de chat completa
- [ ] Video demo (≤3 min)
- [ ] Slides (≤10)
- [ ] .env.example incluido

## 📊 Evaluación

### Rúbrica General
| Criterio | Peso |
|----------|------|
| Presentación 1 | 20% |
| Presentación 2 | 20% |
| Trabajos en clases y tareas | 60% |

Ver detalles completos en: [`syllabus/SYLLABUS.md`](./syllabus/SYLLABUS.md)

---

## 🛠️ Troubleshooting Rápido

### Problemas Comunes

**"Cannot find module"**
```bash
pip install -r requirements.txt  # Python
npm install                      # Node.js
```

**"API key not found"**
```bash
cp .env.example .env
# Editar .env con tu API key
```

**"ChromaDB connection error"**
```bash
mkdir -p data/chroma
```

**Frontend no conecta**
```bash
# En .env.local
VITE_API_URL=http://localhost:8000
```

Ver más en: [README.md - Troubleshooting](./README.md#-troubleshooting-común)

---

## 📚 Enlaces Externos Útiles

### Documentación
- [OpenAI Platform](https://platform.openai.com/docs)
- [Ollama Docs](https://ollama.ai)
- [ChromaDB Guide](https://docs.trychroma.com)
- [LangChain Python](https://python.langchain.com)
- [FastAPI Tutorial](https://fastapi.tiangolo.com)
- [React Docs](https://react.dev)

### Herramientas
- [Postman](https://www.postman.com) - Testing de APIs
- [Excalidraw](https://excalidraw.com) - Diagramas
- [Loom](https://loom.com) - Grabar videos demo

---

## 🗺️ Estructura Visual del Curso

```
Semana 1 · Fundamentos y primer backend
├─ Clase 1 (4 nov) · Introducción y plan incremental
└─ Clase 2 (7 nov) · Backend base y primer prompt

Semana 2 · Núcleo conversacional
├─ Clase 3 (11 nov) · RAG en backend
└─ Clase 4 (14 nov) · Function calling y carrito

Semana 3 · Evaluar y mostrar
├─ Clase 5 (18 nov) · Métricas y preparación demo
└─ Clase 6 (20 nov) · Presentaciones parciales ⭐

Semana 4 · Endurecer y entregar
├─ Clase 7 (25 nov) · Backend robusto + front esencial
└─ Clase 8 (27 nov) · Presentación final 🎓
```

---

## ⚡ Atajos Rápidos

| Quiero... | Ir a... |
|-----------|---------|
| Ver el programa completo | [`syllabus/SYLLABUS.md`](./syllabus/SYLLABUS.md) |
| Empezar la Clase 1 | [`lectures/clase-01/README.md`](./lectures/clase-01/README.md) |
| Ver ejemplos de prompts | [`lectures/clase-01/demo-prompts.md`](./lectures/clase-01/demo-prompts.md) |
| Configurar el entorno | [`examples/.env.example`](./examples/.env.example) |
| Ver el dataset de ejemplo | [`examples/datasets/products.json`](./examples/datasets/products.json) |
| Entender la evaluación | [`syllabus/SYLLABUS.md#evaluación`](./syllabus/SYLLABUS.md) |

---

## 📝 Notas

- Este índice se actualiza conforme se agrega nuevo material
- Para sugerencias o correcciones, contacta a los instructores
- Todos los archivos están en formato Markdown para fácil lectura

---

**Última actualización:** 4 de noviembre 2025

<div align="center">

[↑ Volver arriba](#índice-rápido---llm-commerce-course)

</div>
