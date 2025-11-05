# Syllabus: LLM Commerce — Chatbot de Compras Inteligentes

**Materia:** Tópicos Avanzados de Programación (Algoritmos Generativos)
**Universidad:** Universidad Autónoma Gabriel René Moreno (UAGRM)
**Duración:** 4 semanas (4–27 de noviembre 2025)
**Docentes:** Ing. Miguel Peinado (Titular) — Brandon Valle (Invitado)

---

## 📋 Información General

### Descripción del Curso
Este curso integra modelos de lenguaje (LLMs) en aplicaciones del mundo real, combinando backends en Python y Node.js con interfaces modernas desarrolladas en React. Los estudiantes construirán un **Chatbot de Compras Inteligentes** capaz de buscar, comparar y recomendar productos utilizando datos reales de un catálogo. El progreso es incremental y prioriza el backend (RAG, lógica de carrito, evaluaciones); el frontend se mantiene mínimo (chat, catálogo, login) para resaltar las decisiones de arquitectura LLM.

- **Formato:** Trabajo individual o en parejas (1–2 estudiantes)
- **Sesiones:** 8 clases (2 por semana)
- **Horas totales:** ~32 horas (16 horas presenciales + 16 horas de trabajo independiente)
- **Ritmo:** Cada clase (desde la 3) inicia con revisión breve de tarea, continúa con avance guiado y termina con práctica supervisada.

### Roles Posibles
- **Backend & LLM Engineer:** Funciones, embeddings, API, lógica de negocio
- **Frontend & UX Engineer:** Chat UI, diseño, experiencia visual

---

## 🎯 Objetivos de Aprendizaje

### Técnicos
1. Comprender los fundamentos de los LLMs y su integración en aplicaciones
2. Implementar arquitecturas RAG (Retrieval Augmented Generation)
3. Desarrollar APIs con FastAPI o NestJS
4. Diseñar interfaces conversacionales en React
5. Aplicar pruebas de prompts y function calling

### Transversales (Soft Skills)
1. Colaboración técnica efectiva
2. Comunicación clara de soluciones técnicas
3. Pensamiento crítico y ético sobre IA
4. Gestión de proyectos y entregas incrementales

---

## ⚙️ Stack Tecnológico

| Componente | Tecnologías |
|------------|-------------|
| **Frontend** | React + Vite + TailwindCSS |
| **Backend** | FastAPI (Python) o NestJS (Node.js) |
| **Base de Datos** | SQLite o PostgreSQL (con pgvector) |
| **Vector Store** | ChromaDB / pgvector |
| **LLM Provider** | OpenAI API / Ollama (local) |

### Flujo General
```
Usuario → Chat (Frontend) → API /chat → LLM → Función → Respuesta → UI actualizada
```

---

## 📆 Cronograma Detallado de Clases

> A partir de la Clase 3 cada sesión se organiza en tres bloques: **Revisión rápida de tarea**, **Avance guiado del backend** y **Práctica supervisada**.

### Clase 1 — Introducción y Plan Incremental (4 nov)

#### 🎯 Tema / Topic
- Panorama de los LLM y su rol en el proyecto LLM Commerce
- Arquitectura macro (frontend mínimo + backend orientado a servicios + LLM)
- Estrategia incremental y backlog por hitos

#### 💻 En clase / In-class work
- Mapeo del flujo conversacional ideal
- Priorización de módulos backend (catálogo, buscador, carrito, evaluaciones)
- Redacción colaborativa de prompts base sin ejecución técnica

#### 🧪 Tarea / Homework
- Preparar catálogo inicial (≥20 productos) y definir atributos clave
- Documentar 5 casos de uso objetivo (búsqueda, comparación, presupuesto, carrito, checkout simulado)
- Instalar dependencias mínimas (Node 20+, Python 3.10+, provider elegido) y dejar repositorio listo para el scaffolding

### Clase 2 — Backend Base y Primer Prompt (7 nov)

#### 🎯 Tema / Topic
- Estructura del repositorio backend
- Integración mínima con proveedor LLM (SDK o llamada HTTP)
- Gestión centralizada de prompts y configuración

#### 💻 En clase / In-class work
- Scaffolding del proyecto (FastAPI o NestJS) y configuración de `.env`
- Implementación del endpoint `/chat` que pasa el prompt base al LLM
- Práctica guiada con llamadas de prueba y logging básico

#### 🧪 Tarea / Homework
- Documentar el flujo de request/response del endpoint `/chat`
- Ajustar el prompt base según resultados de la práctica
- Preparar script/colab para generar embeddings del catálogo (sin ejecutarlo aún)

### Clase 3 — RAG: Ingesta y Búsqueda Semántica (11 nov)

#### Revisión
- Comprueba entregables de la Clase 2 (endpoint funcionando y documentación)

#### 🎯 Tema / Topic
- Embeddings y vector stores aplicados al catálogo
- Diseño de servicios de búsqueda semántica reutilizables
- Buenas prácticas para citar fuentes en la respuesta del LLM

#### 💻 En clase / In-class work
- Generar embeddings del catálogo (sección práctica) y almacenarlos (ChromaDB o pgvector)
- Exponer `/catalog/search?q=` retornando resultados con score y metadata
- Integrar el buscador con `/chat` para enriquecer respuestas

#### 🧪 Tarea / Homework
- Registrar al menos 6 casos de prueba de búsqueda con resultados esperados
- Ajustar prompts para incluir referencias a productos encontrados
- Identificar huecos de datos en el catálogo y plan de limpieza

### Clase 4 — Function Calling y Carrito Persistente (14 nov)

#### Revisión
- Validar que `/catalog/search` y la integración con `/chat` estén presentes

#### 🎯 Tema / Topic
- Definición de funciones (JSON Schema) para órdenes del LLM
- Gestión de estado del carrito (en memoria, base de datos o cache)
- Estrategias de orquestación y validación de argumentos

#### 💻 En clase / In-class work
- Implementar `add_to_cart`, `remove_from_cart`, `list_cart`
- Configurar el LLM para invocar funciones según la intención del usuario
- Práctica: flujos end-to-end desde prompt hasta actualización del carrito

#### 🧪 Tarea / Homework
- Documentar tres flujos completos (búsqueda → selección → carrito)
- Añadir pruebas unitarias/funcionales mínimas para las funciones del carrito
- Identificar riesgos de seguridad o errores comunes y mitigaciones

### Clase 5 — Evaluación, Observabilidad y Preparación de Checkpoint (18 nov)

#### Revisión
- Repaso de flujos documentados y pruebas básicas del carrito

#### 🎯 Tema / Topic
- Métricas para conversaciones (aciertos, tiempo de respuesta, errores)
- Prompt evals rápidos y registros de interacción (logging estructurado)
- Preparación de narrativa para la presentación del 20 de noviembre

#### 💻 En clase / In-class work
- Configurar almacenamiento de logs (archivo o base de datos)
- Implementar un script de evaluación con prompts representativos
- Revisión cruzada entre equipos del guion de la demo intermedia

#### 🧪 Tarea / Homework
- Pulir backlog de mejoras prioritarias previo a la presentación
- Crear diapositiva/resumen con arquitectura y learnings clave
- Ensayar demo de 8–10 minutos incluyendo preguntas esperadas

### Clase 6 — Presentaciones Parciales (20 nov)

#### Actividades
- Presentación del MVP por equipo (10 min demo + 5 min feedback)
- Retroalimentación en vivo (instructores + compañeros)
- Reforzar próximos hitos hacia la entrega final

#### Entregables
- Demo funcional con catálogo consultable, RAG integrado y carrito operativo
- Lista de mejoras priorizadas post-feedback (próximo sprint)

---

### Clase 7 — Endurecimiento Backend y Front Esencial (25 nov)

#### Revisión
- Seguimiento de tareas surgidas en la presentación parcial

#### 🎯 Tema / Topic
- Validaciones adicionales, manejo de errores y autenticación básica
- Integración del front mínimo (chat, catálogo, login) con el backend
- Preparación de entornos de despliegue local o staging

#### 💻 En clase / In-class work
- Hardening de endpoints críticos (timeouts, reintentos, sanitización)
- Conexión del frontend existente con los endpoints `/chat`, `/catalog`, `/cart`
- Planificación del material de apoyo para la presentación final (slides, video)

#### 🧪 Tarea / Homework
- Pulir experiencia end-to-end (de login a recomendación) en entorno local
- Grabar borrador del video demo (≤3 min) y recolectar feedback
- Finalizar documentación técnica y guía de pruebas

### Clase 8 — Presentaciones Finales (27 nov)

#### Actividades
- Presentación final (10 min) + Q&A (5 min) por equipo
- Evaluación formal con rúbrica completa (backend, LLM, UX, documentación)
- Cierre del curso y reflexión sobre aprendizajes

#### Entregables
- Repositorio actualizado (backend + frontend mínimo) con README completo
- Video demo ≤3 min, slides de apoyo ≤10 diapositivas
- `.env.example`, scripts de inicialización y documentación de decisiones


## 📊 Sistema de Evaluación

### Distribución de Notas

| Criterio / Criterion | Peso / Weight |
|----------------------|---------------|
| Presentación parcial (Clase 6) | 20% |
| Presentación final (Clase 8) | 20% |
| Tareas y prácticas en clase | 60% |
| **TOTAL** | **100%** |

### Evaluación por Rol

**Backend & LLM Engineer:**
- Arquitectura y diseño del sistema
- Implementación de embeddings y RAG
- Desarrollo de API endpoints
- Lógica de negocio y funciones

**Frontend & UX Engineer:**
- Diseño de interfaz intuitiva
- Componentes reutilizables
- Interacción y feedback visual
- Experiencia de usuario

---

## ✅ Checklist de Entregables

### Repositorio
- [ ] Código fuente completo (frontend + backend)
- [ ] Archivo `.env.example` con variables requeridas
- [ ] Scripts de instalación (`requirements.txt` / `package.json`)
- [ ] Dataset de productos con embeddings

### Funcionalidad
- [ ] Catálogo de productos (≥20 items)
- [ ] Búsqueda semántica con RAG
- [ ] Function calling (carrito completo)
- [ ] UI de chat funcional
- [ ] Recomendaciones y comparación

### Pruebas y Calidad
- [ ] 6+ prompt tests documentados
- [ ] Tests unitarios de funciones críticas
- [ ] 5+ LLM evals de recomendaciones
- [ ] Manejo de errores y edge cases

### Documentación
- [ ] README completo con setup instructions
- [ ] Documentación de API endpoints
- [ ] Casos de uso documentados
- [ ] Decisiones arquitectónicas explicadas

### Presentación
- [ ] Video demo (≤3 minutos)
- [ ] Slides de presentación (≤10)
- [ ] Diagrama de arquitectura
- [ ] Demo funcional en vivo

---

## 💻 Preparación Antes de Clase 1

### Instalaciones Requeridas

#### Windows
```bash
# Node.js
winget install OpenJS.NodeJS

# Python
winget install Python.Python.3.11

# Ollama (opcional)
winget install Ollama.Ollama

# Git
winget install Git.Git
```

#### macOS
```bash
# Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Node.js, Python y Git
brew install node python git ollama
```

#### Ubuntu / Linux
```bash
sudo apt update && sudo apt install -y nodejs npm python3 python3-venv git curl

# Instalar Ollama
curl -fsSL https://ollama.ai/install.sh | sh
```

### Verificación
```bash
node -v          # v18+ requerido
python3 --version # 3.10+ requerido
ollama --version # opcional
git --version
```

### Cuentas Necesarias
- GitHub (para repositorio del proyecto)
- OpenAI API (créditos gratuitos) **O** instalar Ollama localmente
- (Opcional) Vercel/Render para deployment

---

## 📚 Recursos y Referencias

### Documentación Oficial
- **OpenAI API:** https://platform.openai.com/docs
- **LangChain Docs:** https://python.langchain.com
- **Ollama Local Models:** https://ollama.ai
- **FastAPI Docs:** https://fastapi.tiangolo.com
- **NestJS Docs:** https://docs.nestjs.com
- **ChromaDB:** https://docs.trychroma.com
- **pgvector:** https://github.com/pgvector/pgvector
- **React + Vite:** https://vitejs.dev/guide/

### Herramientas Recomendadas
- **IDE:** VS Code, Cursor, PyCharm
- **API Testing:** Postman, Thunder Client, HTTPie
- **Git:** GitHub Desktop, GitKraken
- **Deployment:** Vercel, Render, Hugging Face Spaces

---

## 🧠 Extensiones Opcionales

Equipos avanzados pueden implementar:

1. **Voz / Voice:** Integrar Whisper (STT) o Speechify (TTS)
2. **Visión / Vision:** Subir imágenes y reconocer productos
3. **Analítica / Analytics:** Dashboard con métricas de conversación
4. **Despliegue / Deployment:** Deploy en Vercel, Render, HF Spaces
5. **Multi-idioma:** Soporte para español e inglés
6. **Histórico:** Persistencia de conversaciones en DB

---

## 📋 Políticas del Curso

### Asistencia
- Mínimo 75% de asistencia requerida
- Participación activa en clase es valorada

### Entregas
- **Checkpoint obligatorio:** Presentación parcial el 20 de noviembre (Clase 6)
- **Entrega final:** 27 de noviembre 2025, 23:59
- Penalización por retraso: -10% por día

### Integridad Académica
- Uso de LLMs (ChatGPT, Claude, etc.) **permitido y fomentado**
- Documentar el uso de IA en el README
- Código de terceros debe ser citado
- Colaboración entre equipos permitida (pero entregas propias)

### Trabajo en Equipos
- Máximo 2 personas por equipo
- División clara de responsabilidades
- Ambos miembros deben poder explicar todo el proyecto

---

## 📞 Contacto y Soporte

- Canal de comunicación oficial: [Slack/Discord - Por definir]
- Correo de coordinación académica: [Por definir]
- Horario de consultas: [Por definir]

---

## 🚀 Notas Finales

Este curso está diseñado para ser **práctico, incremental y colaborativo**. Cada clase construye sobre la anterior, por lo que es fundamental:

1. **Asistir a todas las clases** y completar las tareas
2. **Preguntar activamente** cuando algo no esté claro
3. **Experimentar** más allá de los requisitos mínimos
4. **Documentar** decisiones y aprendizajes
5. **Compartir** conocimiento con compañeros

> **Consejo:** Empezar simple y agregar complejidad gradualmente. Un chatbot básico que funciona bien es mejor que uno complejo que falla.

---

**Última actualización:** 4 de noviembre 2025
**Versión:** 1.0
