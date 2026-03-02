# Guía Profesional de Ollama Local
[![Docker Ready](https://img.shields.io/badge/Docker-Ready-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Ollama](https://img.shields.io/badge/Ollama-Local%20LLM-black)](https://ollama.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Idioma: Español](https://img.shields.io/badge/Idioma-Espa%C3%B1ol-blue)](#)
[![Status: Production Ready](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)](#)

Guía técnica para ejecutar LLMs 100% locales con Ollama usando Docker, orientada a proyectos serios de portafolio y automatización.

## Objetivos

- Correr modelos open-source sin depender de APIs externas.
- Mantener privacidad de datos en infraestructura local.
- Estandarizar despliegue con Docker Compose.
- Facilitar integración con scripts, backends y n8n.

## Casos de uso

- Asistente interno de documentación.
- Generación de respuestas técnicas offline.
- Análisis de logs y clasificación de tickets.
- Prototipos RAG y agentes locales.

## Stack

- Ollama
- Docker / Docker Compose
- REST API local en `http://localhost:11434`

## Estructura

```text
.
├── docker-compose.yml
├── .env.example
└── README.md
```

## Requisitos

- Docker Desktop o Docker Engine + Compose
- Recomendado: 16 GB RAM mínimo
- Opcional: GPU NVIDIA + NVIDIA Container Toolkit

## 1) Configurar puerto

```bash
cp .env.example .env
```

Ajusta si hace falta:

```env
OLLAMA_PORT=11434
```

## 2) Levantar Ollama (CPU)

```bash
docker compose up -d ollama
```

Ver logs:

```bash
docker compose logs -f ollama
```

## 3) Levantar Ollama (GPU opcional)

```bash
docker compose --profile gpu up -d ollama-gpu
```

Usa este modo solo si tienes runtime NVIDIA configurado.

## 4) Descargar modelos dentro del contenedor

```bash
docker compose exec ollama ollama pull llama3
```

Si usas GPU service:

```bash
docker compose exec ollama-gpu ollama pull llama3
```

## 5) Probar generación por API

```bash
curl http://localhost:11434/api/generate \
  -d '{"model":"llama3","prompt":"Explica arquitectura hexagonal","stream":false}'
```

## 6) Integración con Python

```python
import requests

url = "http://localhost:11434/api/generate"
payload = {
    "model": "llama3",
    "prompt": "Resume ventajas de microservicios",
    "stream": False,
}

response = requests.post(url, json=payload, timeout=120)
response.raise_for_status()
print(response.json()["response"])
```

## Seguridad

- No expongas `11434` en internet sin proxy y autenticación.
- Aísla la red en entornos corporativos.
- Añade rate limiting si atiendes múltiples clientes.

## Solución de problemas

- El contenedor no responde: revisa `docker compose logs`.
- Modelo no encontrado: ejecuta `ollama pull <modelo>`.
- Rendimiento bajo: usa modelos cuantizados (`q4`, `q8`) o activa GPU.

---

## 👨‍💻 Desarrollado por Isaac Esteban Haro Torres

**Ingeniero en Sistemas · Full Stack · Automatización · Data**

- 📧 Email: zackharo1@gmail.com
- 📱 WhatsApp: 098805517
- 💻 GitHub: https://github.com/ieharo1
- 🌐 Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

---

© 2026 Isaac Esteban Haro Torres - Todos los derechos reservados.

