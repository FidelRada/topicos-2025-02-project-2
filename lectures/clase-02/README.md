# Clase 2 · Backend Base y Primer Prompt

## Propósito de la sesión
- Consolidar la estructura del backend que servirá al proyecto completo.
- Integrar un LLM (OpenAI u Ollama) mediante un endpoint `/chat` mínimo.
- Practicar la instrumentación de prompts y la observación de respuestas.

## Objetivos de aprendizaje
- Configurar correctamente el entorno (`.env`, dependencias, llaves).
- Implementar un primer flujo request → LLM → response en el backend.
- Registrar las decisiones de prompt y resultados para iteraciones futuras.

## Agenda sugerida (100 min)
| Min | Actividad |
| --- | --- |
| 0-10 | Recordatorio de entregables de la clase 1 y contexto del proyecto |
| 10-25 | Tour por la estructura del backend (FastAPI/NestJS) |
| 25-55 | Demo guiada: creación de `/chat` y conexión con el proveedor LLM |
| 55-80 | Recorrido del repositorio de referencia y scripts disponibles |
| 80-95 | Discusión de hallazgos y ajustes recomendados |
| 95-100 | Explicación de la tarea para la clase 3 |

## Antes de empezar
- Tener instalado: `python >= 3.10` y/o `node >= 20`.
- Haber clonado el repositorio y creado el archivo `.env`.
- Confirmar que la API key está disponible (**OpenAI**) o que `ollama serve` corre localmente.
- Contar con el catálogo preliminar (aunque sea en borrador) para pruebas simples.

## Repaso rápido (5 min)
- ¿Qué definimos como objetivo para el chatbot? → Enfatizar catálogo + carrito.
- Recordar los 5 casos de uso documentados en la tarea.
- Preguntar: ¿qué dudas quedaron sobre prompts o arquitectura?

## Ruta técnica
### 1. Estructura base
- `/src` o `/app` con módulos: `config`, `routes`, `services`, `prompts`.
- Archivo `.env` con variables mínimas:
  - `LLM_PROVIDER=openai|ollama`
  - `OPENAI_API_KEY=` (si aplica)
  - `OLLAMA_MODEL=llama3.1` (sugerido)
  - `BASE_PROMPT_PATH=prompts/system.txt`

### 2. Primer endpoint `/chat`
#### Opción FastAPI (Python)
```python
# app/main.py
from fastapi import FastAPI
from pydantic import BaseModel
from services.llm import generate_response

app = FastAPI()

class ChatRequest(BaseModel):
    message: str

@app.post("/chat")
async def chat_endpoint(payload: ChatRequest):
    answer = await generate_response(payload.message)
    return {"reply": answer}
```

```python
# app/services/llm.py
import os
from openai import AsyncOpenAI

client = AsyncOpenAI(api_key=os.getenv("OPENAI_API_KEY"))
SYSTEM_PROMPT = Path("prompts/system.txt").read_text()

async def generate_response(user_message: str) -> str:
    completion = await client.chat.completions.create(
        model="gpt-4o-mini",
        messages=[
            {"role": "system", "content": SYSTEM_PROMPT},
            {"role": "user", "content": user_message},
        ],
        temperature=0.4,
    )
    return completion.choices[0].message.content
```

#### Opción NestJS (Node.js)
```typescript
// src/chat/chat.controller.ts
import { Body, Controller, Post } from '@nestjs/common';
import { ChatService } from './chat.service';

class ChatDto {
  message: string;
}

@Controller('chat')
export class ChatController {
  constructor(private readonly chatService: ChatService) {}

  @Post()
  async create(@Body() body: ChatDto) {
    const reply = await this.chatService.generate(body.message);
    return { reply };
  }
}
```

```typescript
// src/chat/chat.service.ts
import { Injectable } from '@nestjs/common';
import { OpenAI } from 'openai';
import * as fs from 'fs';

const systemPrompt = fs.readFileSync('prompts/system.txt', 'utf8');

@Injectable()
export class ChatService {
  private client = new OpenAI({ apiKey: process.env.OPENAI_API_KEY });

  async generate(message: string) {
    const completion = await this.client.chat.completions.create({
      model: 'gpt-4o-mini',
      messages: [
        { role: 'system', content: systemPrompt },
        { role: 'user', content: message },
      ],
      temperature: 0.4,
    });
    return completion.choices[0].message.content;
  }
}
```

> Tip: Para Ollama, reemplaza la llamada al SDK por un fetch/axios hacia `http://localhost:11434/api/chat`.

### 3. Logging básico
- Registrar cada petición/respuesta (mínimo timestamp, prompt enviado, respuesta).
- Evitar guardar API keys en logs.
- Útil para identificar prompts que necesitan ajuste.

> La práctica detallada queda documentada en el repositorio del curso; en clase se muestra la arquitectura y se resuelven dudas clave.

### 4. Checklist de salida de clase
- [ ] Backend corre localmente sin errores.
- [ ] Endpoint `/chat` responde con contenido del LLM.
- [ ] Prompt base está guardado en un archivo (no hardcodeado).
- [ ] Bitácora con al menos 3 consultas y observaciones.

## Tarea para Clase 3
- Documentar el flujo request/response con un diagrama sencillo.
- Afinar el prompt base (versión 2) y explicar por qué se modificó.
- Preparar script/notebook para generación de embeddings del catálogo (sin ejecutarlo).
- Listar preguntas pendientes sobre RAG para la siguiente clase.

## Recursos sugeridos
- [OpenAI Chat Completions](https://platform.openai.com/docs/guides/text-generation)
- [Ollama REST API](https://github.com/ollama/ollama/blob/main/docs/api.md#generate-a-chat-completion)
- [FastAPI Docs](https://fastapi.tiangolo.com/tutorial/)
- [NestJS Fundamentals](https://docs.nestjs.com/first-steps)
- [Twelve-Factor Config](https://12factor.net/config) para buenas prácticas con `.env`
