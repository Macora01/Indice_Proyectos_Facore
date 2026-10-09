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
| 3 | SII Extractor | 🟡 En curso | [ver](https://github.com/Macora01/sii-extractor/blob/main/SII_EXTRACTOR.md) (repo privado, requiere login) | Rotar credenciales expuestas en el historial de git (clave de la BD y API key) |

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

---

*Última actualización: 2026-10-09*
