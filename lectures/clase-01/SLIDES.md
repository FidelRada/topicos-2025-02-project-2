# Slides · Clase 1 — Introducción a los LLM

---

## Slide 1 · Bienvenida
- **Curso:** Tópicos Avanzados — LLM Commerce
- **Tema:** ¿Qué es un LLM y cómo lo usaremos en el asistente de compras?

---

## Slide 2 · ¿Por qué LLM ahora?
- Clientes esperan experiencias conversacionales inmediatas.
- Los modelos actuales permiten prototipos útiles sin entrenar desde cero.
- Costos de cómputo accesibles (APIs en la nube u opciones locales).
- Integraciones rápidas con las herramientas que ya usamos (REST, SDKs).

---

## Slide 3 · LLM en una frase
- Modelo estadístico que predice la siguiente palabra dado el historial.
- Entrenado con grandes corpus de texto → aprende patrones y estilo.
- Responde en lenguaje natural, código o formatos estructurados.
- No “sabe” datos nuevos; necesita soporte externo para actualizaciones.

---

## Slide 4 · Elementos de un buen prompt
1. **Rol:** “Eres un asistente de compras de TechStore…”
2. **Contexto:** “Catálogo disponible: laptops, monitores…”
3. **Tarea:** “Recomienda opciones según las necesidades del cliente.”
4. **Formato:** “Responde en lista numerada con nombre, precio y motivo.”
- Ajusta una variable a la vez y documenta el cambio.

---

## Slide 5 · Límites y responsabilidad
- Puede inventar información plausible → valida antes de mostrar.
- No tiene memoria persistente sin que la implementemos.
- Respeta datos sensibles y oculta claves/API keys.
- Define reglas de interacción (qué puede y qué no puede prometer).

---

## Slide 6 · Opciones de modelo
- **OpenAI GPT-4o mini:** mejor calidad, requiere conexión y API key.
- **Ollama + Llama 3.1:** gratuito/local, mayor latencia y tuning manual.
- Recomendación: prepara ambos; usa OpenAI en producción, Ollama para pruebas sin costo.

---

## Slide 7 · Arquitectura mínima
```
Usuario → Frontend (React) → Backend (FastAPI/Nest) → LLM (API u Ollama)
                             ↳ Catálogo (JSON/DB) para enriquecer respuestas
```
- El backend decide cuándo llamar al modelo y cómo enriquecer la respuesta.

---

## Slide 8 · Discusión guiada
- ¿En qué escenarios un LLM aporta más valor que reglas tradicionales?
- ¿Qué riesgos deben mitigarse antes de lanzar un asistente de compras?
- ¿Qué métricas usarías para evaluar la calidad de las respuestas?

---

## Slide 9 · Lo que sigue
- Trae tu catálogo preliminar (aunque sea en spreadsheet) para la próxima clase.
- Elige proveedor a experimentar (OpenAI u Ollama) y revisa su SDK.
- Lee el abstract de RAG (Lewis et al., 2020) para conectar teoría con práctica.
