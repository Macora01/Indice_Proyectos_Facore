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
| 3 | SII Extractor | 🟡 En curso | [ver](https://raw.githubusercontent.com/Macora01/sii-extractor/main/SII_EXTRACTOR.md) | Actualización mensual automática (cron) |

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

*Última actualización: 2026-06-18*
