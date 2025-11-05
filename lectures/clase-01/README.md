# Clase 1 · Introducción a los LLM

## Propósito de la sesión
- Clarificar qué es un LLM y dónde encaja en soluciones reales.
- Montar el entorno mínimo para interactuar con un modelo.
- Practicar la formulación de prompts efectivos dentro del proyecto.

## Objetivos de aprendizaje
- Explicar con tus palabras qué problema resuelven los LLM y sus límites.
- Realizar una llamada a un modelo (OpenAI u Ollama) desde tu entorno local.
- Registrar un primer set de prompts reutilizables para el asistente de compras.

## Ruta rápida
| Momento | Qué haremos |
| --- | --- |
| Antes de la clase | Instala `node >= 20`, `python >= 3.10`, y crea una cuenta con API key (OpenAI) u Ollama local. |
| Durante la clase | Revisamos conceptos esenciales, configuramos el proyecto base y ejecutamos una primera consulta. |
| Después de la clase | Ajusta tus prompts iniciales y documenta lo aprendido en tu bitácora del curso. |

## Conceptos esenciales
**LLM (Large Language Model)**  
Modelo entrenado para predecir la siguiente palabra. Aprende patrones estadísticos del lenguaje y genera texto coherente dado un contexto.

**Prompt**  
Instrucción estructurada que guía la respuesta del modelo. Rol + tarea + contexto + formato.

**Limitaciones básicas**  
- No tiene memoria persistente sin soporte adicional.  
- Puede inventar datos (alucinaciones).  
- Su conocimiento se detiene en la fecha de entrenamiento.  
- Requiere revisión humana para decisiones críticas.  

**Uso responsable**  
Protege datos sensibles, comunícale al usuario que habla con IA, documenta cualquier decisión automatizada.

## Actividad guiada
1. Clona este repositorio y copia `.env.example` a `.env`.
2. Elige provider:
   - OpenAI → define `OPENAI_API_KEY`.
   - Ollama → asegúrate de tener `ollama run llama3.1`.
3. Ejecuta la plantilla de backend y prueba el endpoint `/chat`.
4. Ajusta el prompt base en `prompts/system.txt` (o el archivo equivalente) usando la sección “Prompts base” de la clase.
5. Registra el comando exitoso y la respuesta del modelo en tu bitácora.

## Tarea sugerida
- Documenta tres casos de uso del asistente (búsqueda, comparación, carrito).
- Itera tu prompt base y anota cómo cambia la respuesta.
- Instala o prepara los datos de productos que usarás en la siguiente sesión.

## Material de apoyo
- Brown et al. (2020) – *Language Models are Few-Shot Learners*.
- Anthropic Prompt Library – ejemplos de redacción por casos.
- Documentación oficial del provider que selecciones.

## Próxima sesión
Clase 2: Recuperación aumentada (RAG) y embeddings para dar respuestas basadas en catálogo.
