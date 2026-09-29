# Galarza_Mijail_EntregableFinal_ProgramacionIV[README.md](https://github.com/user-attachments/files/32781597/README.md)
# TechStore — Inventario de computadoras y periféricos con IA (Ollama)

Aplicación web en **Django** para administrar el inventario de una tienda de
computadoras y periféricos mediante CRUD, reportes predefinidos y un chat
respondido por un modelo de inteligencia artificial local (**Ollama**).

La IA responde **únicamente** con los datos reales del inventario registrado;
nunca inventa productos, precios ni cantidades.

## Requisitos

- Python 3.10+
- [Ollama](https://ollama.com) instalado y ejecutándose localmente
- Un modelo descargado, por ejemplo:

```bash
ollama pull qwen2.5:1.5b
```

## Instalación y ejecución

```bash
# 1. Crear el entorno virtual e instalar dependencias
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

# 2. Configurar variables de entorno (opcional)
cp .env.example .env

# 3. Aplicar migraciones y ejecutar el servidor
python manage.py migrate
python manage.py runserver
```

Abrir en el navegador: http://127.0.0.1:8000/

### Datos de ejemplo (opcional)

```bash
python manage.py seed_productos
```

Registra productos de muestra (computadoras y periféricos) para probar
reportes y el chat con la IA.

## Funcionalidades

| Área | Descripción |
| --- | --- |
| CRUD | Registrar, consultar, editar y desactivar (eliminación lógica) productos |
| Búsqueda | Por código, nombre y categoría |
| Stock | Aumentar/disminuir existencias; consultar agotados y stock bajo |
| Reportes | 8 reportes predefinidos con opción de explicación con IA |
| Chat IA | Preguntas en lenguaje natural respondidas por Ollama |
| Historial | Registro de preguntas y respuestas generadas |

## Configuración de Ollama

Las variables se leen desde `.env` (ver `.env.example`):

- `OLLAMA_URL` — API de generación de Ollama (default `http://localhost:11434/api/generate`)
- `OLLAMA_MODEL` — modelo local (default `qwen2.5:1.5b`)
- `OLLAMA_TIMEOUT` — segundos de espera (default `60`)

Si Ollama no está disponible, la aplicación muestra un mensaje de error claro
sin interrumpir el resto del sistema.

## Asistencia con IA en el desarrollo

Este proyecto se desarrolló con el apoyo de **opencode**, un asistente de
programación con IA integrado en la terminal, que colaboró en la
implementación del CRUD, la integración con Ollama, las pruebas, los scripts
de utilidad y la documentación. El detalle de sus aportes se encuentra en la
sección 15 del Informe del Proyecto.
