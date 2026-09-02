# Tu primer agente de IA — versión Gemini

Código de apoyo para la sección de **«Construyendo un agente desde cero»**
de la presentación *Agentes, prompts y RAG*.

Es un agente de IA funcional simple implementando solo memoria, herramientas y un bucle.

## Requisitos

- **Python 3.10 o superior** (obligatorio: `google-genai` no existe para 3.9 ni anteriores)
- Una llave de la API de Gemini (gratuita): https://aistudio.google.com/apikey


## Instalación

### Opción A — con conda (recomendada)

Es la ruta más limpia en Windows: evita los conflictos de PATH entre varias
instalaciones de Python.

```bash
conda create -n agente python=3.10 -y
conda activate agente
pip install -r requirements.txt
```

### Opción B — con venv

Necesitas que el `python` que uses sea 3.10 o superior. Si tienes varias
versiones instaladas en Windows, el lanzador `py` te deja elegir:

```bash
py -3.10 -m venv .venv        # Windows
python3 -m venv .venv         # macOS / Linux

.venv\Scripts\activate        # Windows
source .venv/bin/activate     # macOS / Linux

python -m pip install --upgrade pip
pip install -r requirements.txt
```

### La llave

Copia `.env.example` a `.env` y pon ahí tu llave:

```
GEMINI_API_KEY=xxxxxxxxxxxxxxxxxxxx
```

## Ejecución

```bash
python main.py
```

Probado con Python 3.10 (conda) y `google-genai` 2.19.0.

Cosas que puedes pedirle:

- `¿Qué archivos hay en esta carpeta?`
- `Lee el archivo main.py y explícame qué hace en dos frases.`
- `Crea un archivo notas.txt con una lista de los temas de la clase.`
- `En notas.txt cambia "RAG" por "Generación aumentada por recuperación".`

Escribe `salir` para terminar.

## Problemas comunes

### `ERROR: Could not find a version that satisfies the requirement google-genai`

Comprueba primero:

```bash
python --version
```

**Si es 3.9 o menor**, lo más rápido es crear un entorno de conda con una versión
compatible (no hace falta desinstalar nada):

```bash
conda create -n agente python=3.10 -y
conda activate agente
pip install -r requirements.txt
```


## Archivos

| Archivo            | Qué contiene                                                         |
|--------------------|----------------------------------------------------------------------|
| `agent.py`         | Memoria, declaración e implementación de las herramientas del Agente |
| `main.py`          | Cliente de Gemini                                                    |
| `requirements.txt` | Dependencias                                                         |
| `.env.example`     | Plantilla para tu key                                                |

## Créditos

Basado en *How to Build an Agent* de Thorsten Ball. 
La versión original usa la API de OpenAI; aquí se portó a la API de Gemini para poder probar de forma gratuita.
