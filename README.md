# Índice de Proyectos Facore

> **Instrucciones para el asistente IA:**
> Lee este archivo, muestra el listado de proyectos al usuario y pregunta:
> **"¿En cuál de estos proyectos trabajamos hoy?"**
> Una vez que el usuario elija, lee el `manual-tecnico.md` del proyecto correspondiente antes de empezar.

---

## Proyectos

| # | Proyecto | Estado | Manual Técnico | Pendiente crítico |
|---|---|---|---|---|
| 1 | ProGesVen v2 | 🟢 Estable | [ver](https://raw.githubusercontent.com/Macora01/ProGesVen/v2/docs/manual-tecnico.md) | Recuperar ventas recientes si Hostinger restaura contenedor v1 |
| 2 | facore-inventory v2 | 🟡 En curso | [ver](https://raw.githubusercontent.com/Macora01/facore-inventory/v2/TECH.md) | Cargar remanente PV-2025 y cambiar contraseña admin |
| 3 | SII Extractor | 🟡 En curso | [ver](https://github.com/Macora01/sii-extractor/blob/main/SII_EXTRACTOR.md) (repo privado, requiere login) | Alertas Discord del worker; apagar el cron del Mac tras la mensual de noviembre; validar monetización con pilotos |

---

## Estados

| Ícono | Significado |
|---|---|
| 🟢 | Estable — sin pendientes urgentes |
| 🟡 | En curso — trabajo activo |
| 🔴 | Bloqueado — esperando algo externo |
| ⚫ | Pausado — sin actividad reciente |
| ✅ | Terminado |

---

## Notas ProGesVen v2 (2026-06-18)

- BD PostgreSQL recreada en Coolify (host: `seyef4iwtgxtobwevyhfgvsp`)
- Datos migrados: 188 productos, 19 ubicaciones, 107 ventas históricas, 11 bazares, 10 puntos de venta
- Ventas recientes (posteriores a oct-2025) perdidas con contenedor v1 — pendiente consulta a Hostinger
- Dominio `ventas.facore.cl` apunta a v2 ✅

---

## Notas SII Extractor (2026-10-09)

- Acceso restringido por usuario (rol `propietario`) implementado el 2026-09-04
- Clave del usuario `mario` reseteada (las claves son hash bcrypt en `frontend/auth_config.yaml`; no se recuperan, solo se resetean). Guardarla en el gestor de claves
- Pin `pyarrow==25.0.1` en `frontend/requirements.txt`: `pyarrow 26.0.0` (publicado el 2026-10-09) rompía el login de `streamlit 1.35.0` al reconstruir la imagen. Las dependencias transitivas siguen sin fijar
- La base PostgreSQL (`xe4yydacmt34t6t1sn4411z8`) estaba detenida en Coolify: la API daba 500 y el frontend mostraba "Error conectando a la API". Se inició de nuevo; el volumen de datos se había conservado. Causa de la detención: desconocida
- Deploy del frontend (`e3t5e592xt26526v8gt3elnp`): manual en https://coolify.facore.cloud
- Cron mensual del Mac (launchd, día 6) fallaba en silencio desde agosto: usaba `/usr/bin/python3` (3.9, sin Playwright). Corregido en v01.02.04: `run_mensual.sh` elige el primer Python que tenga Playwright. Agosto y septiembre 2026 de Boa Ideia cargados a mano
- Prueba exitosa del extractor en el VPS: el SII acepta el ingreso desde el servidor (Chrome en contenedor `mcr.microsoft.com/playwright/python:v1.60.0-noble` + Xvfb). Base para un worker en Coolify que actualice datos desde la app sin depender del Mac
- **v02.01.01 publicada (2026-10-09):** interfaz rediseñada (Streamlit 1.65, tema sobrio, navegación nueva, Inicio/Consultas/Facturas), dependencias fijadas, y actualización de datos desde la app con un worker en el servidor (`sii-worker`, Coolify `ndti7fh34s5wr7xv4xpmdifp`) que además hace la mensual del día 6. Verificado con septiembre 2026 de Boa Ideia y María Cecilia
- Seguridad: `/facturas/*` respondía sin API key; corregido y desplegado (v01.02.05). Coolify clona el repo privado con la GitHub App `gith-macora01` en las tres apps
- **v02.02.01 publicada (2026-10-09):** fase 3 — usuarios en la base de datos (migrados con sus mismas claves), Mi cuenta (cada uno cambia su contraseña) y Administración rediseñada. Llave de la cookie rotada (COOKIE_KEY en Coolify). La API filtra el período con año y mes juntos
- **v02.02.02 publicada (2026-10-10):** API_KEY y clave de PostgreSQL rotadas (`ops/rotar_llaves.py`, lo corre Mario), sin secretos en el código, `auth_config.yaml` eliminado, errores 500 sin traceback. Verificado: llave vieja 401, API y base ok
- Análisis de monetización (ver manual): multiusuario en una sola instancia, VPS aparte para clientes de pago, validar con 3–5 pilotos antes de construir
- **Respaldos (2026-10-11):** la base no tenía ninguno; ahora diario 03:00 en Coolify (7 locales, verificado). Falta copia fuera del VPS
- Pendiente: copia externa de respaldos, alertas Discord del worker (necesita el webhook), desactivar el cron del Mac tras la mensual de noviembre

---

*Última actualización: 2026-10-11*
