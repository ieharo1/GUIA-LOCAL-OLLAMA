# Ollama Local LLM Guide 🚀

curl http://localhost:11434/api/generate
 -d '{
"model": "llama3",
"prompt": "Explica qué es una arquitectura escalable"
}'


---

## 🐍 Integración con Python



import requests

url = "http://localhost:11434/api/generate
"

payload = {
"model": "llama3",
"prompt": "Genera un resumen técnico sobre microservicios",
"stream": False
}

response = requests.post(url, json=payload)

print(response.json()["response"])


---

## 🔐 Seguridad

- Ejecutar detrás de firewall
- No exponer el puerto 11434 públicamente
- Usar reverse proxy con autenticación si es necesario
- Implementar rate limiting en producción

---

## 📊 Modelos Recomendados

| Modelo     | Uso Ideal |
|------------|-----------|
| llama3     | General purpose |
| mistral    | Rápido y liviano |
| codellama  | Generación de código |
| phi        | Entornos con pocos recursos |
| gemma      | Alternativa ligera |

---

## 🧠 Casos de Uso Empresarial

- Asistente interno de documentación
- Generación automática de reportes
- Chat interno sobre bases de datos
- Clasificación de tickets
- Análisis de logs

---

## 🚀 Integración con n8n

1. Crear HTTP Request Node
2. Método: POST
3. URL: http://localhost:11434/api/generate
4. Body JSON
5. Procesar respuesta

Permite automatizaciones completamente locales.

---

## 🏎 Optimización

- Usar modelos cuantizados (q4, q8)
- Ajustar temperatura y top_p
- Desactivar stream si no se necesita
- Limitar tokens máximos

---

## 📈 Escalabilidad

Para producción:

- Dockerizar Ollama
- Usar balanceador interno
- Implementar colas (Redis)
- Separar procesamiento por microservicio

---

## 🐳 Docker



docker run -d -p 11434:11434 ollama/ollama


---

## 🛡 Ventajas frente a APIs externas

- 0 costo por token
- Datos no salen de la empresa
- Control total del modelo
- Sin límites de uso

---

## 📚 Recursos

- https://ollama.com
- https://github.com/ollama/ollama

---

## 🤝 Contribuciones

Pull requests son bienvenidos.
Si el proyecto te aporta valor, considera darle ⭐

---

## 📄 Licencia

MIT — contribuciones bienvenidas 🚀

---

## 💻 Creado Por

🧑‍💻 Isaac Haro

Ingeniero en Sistemas · Full Stack · Automatización · Data

Isaac Esteban Haro Torres
- 📧 zackharo1@gmail.com
- 📱 098805517
- 💻 [GitHub](https://github.com/ieharo1)
- 🌐 [Portafolio](https://ieharo1.github.io/portafolio-isaac.haro/)
