# AdoBot (documentación del repositorio)

> ⚠️ Este repositorio contiene componentes con capacidades invasivas.  
> Úsalo solo para análisis académico, seguridad defensiva y entornos controlados con autorización explícita.

## Descripción general

Este repositorio está dividido en dos partes principales:

- **`/android`**: código de la app Android.
- **`/server/adobot`**: backend en Python con:
  - API HTTP basada en Starlette.
  - Worker de Telegram para consultar estado y diagnóstico.

## Estructura principal

```text
AdoBot/
├── android/
└── server/
    └── adobot/
        ├── app/                  # API HTTP (Starlette)
        ├── adobot_telegram/      # Worker/comandos de Telegram
        ├── config/               # Plantillas de configuración
        ├── tests/                # Pruebas automatizadas
        ├── preflight.sh          # Validaciones previas
        ├── run_operational_gate.sh
        └── start.sh              # Inicio del servidor API
```

## Requisitos (backend)

- Python 3.11+ (recomendado)
- Entorno virtual (`.venv`)
- Dependencias en:
  - `/home/runner/work/AdoBot/AdoBot/server/adobot/requirements.txt`
  - `/home/runner/work/AdoBot/AdoBot/server/adobot/requirements-test.txt`

## Puesta en marcha del backend para análisis local

Desde `/home/runner/work/AdoBot/AdoBot/server/adobot`:

1. Crear y activar entorno virtual.
2. Instalar dependencias de `requirements.txt` y `requirements-test.txt`.
3. Crear `config/.env` tomando como base `config/.env.example`.
4. Ejecutar validación previa:
   - `./preflight.sh`
5. Ejecutar pruebas:
   - `python -m pytest -q tests`
6. Iniciar API local:
   - `./start.sh`

## Endpoints de la API local

Definidos en `/home/runner/work/AdoBot/AdoBot/server/adobot/app/main.py`:

- `GET /api`
- `GET /health`
- `GET /ready`
- `GET /info`
- `GET /diagnostics`

## Notas de seguridad

- Mantén el backend en entorno **aislado**.
- No expongas servicios a redes públicas sin controles estrictos.
- No uses este proyecto sobre dispositivos o cuentas de terceros sin consentimiento explícito.
