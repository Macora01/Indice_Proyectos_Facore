# Instrucciones para el asistente IA — Proyectos Facore

## Al iniciar sesión

1. Clonar o pullear este repositorio si no está local:
   ```
   git clone https://github.com/Macora01/Indice_Proyectos_Facore.git
   ```
2. Leer este archivo y el `README.md` del mismo repo
3. Mostrar la tabla de proyectos del README exactamente como aparece
4. Preguntar: **"¿En cuál de estos proyectos trabajamos hoy?"**
5. Una vez que el usuario elija, clonar/pullear el repositorio de ese proyecto y leer su manual técnico antes de tocar nada

## Durante la sesión

- Explicar brevemente cada comando antes de ejecutarlo
- No crear archivos locales de configuración — todo va a GitHub
- Si hay cambios en la DB (migraciones), recordar que el deploy en Coolify es **manual**: push → redeploy en https://coolify.facore.cloud → scripts en terminal del contenedor
- Preguntar si no está seguro. No improvisar en producción

## Al finalizar sesión

1. Hacer push de todos los repositorios modificados
2. Actualizar el `README.md` de este repo: estado del proyecto, pendientes, fecha
3. Hacer push de este repo con los cambios del README

## Frase de inicio desde cualquier máquina

El usuario dirá:

> **"Facore"**

Eso es todo lo que necesita decir. Con esa palabra, el asistente sabe que debe clonar este repo, leer este archivo y arrancar el workflow.

---

## Proyectos — referencia rápida

| Repo | Branch de trabajo | Manual técnico |
|---|---|---|
| https://github.com/Macora01/ProGesVen.git | `v2` | `PROGESVEN.md` en el repo |
| https://github.com/Macora01/facore-inventory.git | `v2` | `TECH.md` en el repo |

## Notas operativas clave (no olvidar)

- **Deploy Coolify:** NO es automático. Push a GitHub → el usuario despliega manualmente en Coolify
- **Terminal Coolify:** la del servidor corre `sh` (no bash). Para Python, usar la terminal del contenedor
- **Orden correcto siempre:** push → redeploy en Coolify → scripts en contenedor si aplica
