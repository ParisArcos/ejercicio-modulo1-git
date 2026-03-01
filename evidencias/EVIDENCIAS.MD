# Evidencias — Módulo 1: Versionado de Código y Colaboración

**Repositorio (GitHub):** https://github.com/ParisArcos/ejercicio-modulo1-git.git
**Autor:** Paris Arcos Martin
**Fecha:** 2026-03-01

---

## 1) Creación del repositorio y primer commit

- Se inicializó el repositorio local con `main` y se creó el fichero `README.md` con nombre y fecha.
- Se realizó el primer commit y se publicó en GitHub.

**Commit (initial):** `4e28c8db3300a2b22db297c8de07bfcd2d08defa`  
**Rama:** `main`

---

## 2) Protección de la rama `main`

Se configuró protección de rama en GitHub para `main` con estas reglas:

- **Require a pull request before merging** (obliga a PR para cambios en `main`)

**Por qué es recomendable:**

- Evita cambios directos sin revisión y reduce errores en la rama principal.
- Asegura trazabilidad (cada cambio pasa por PR con historial y contexto).
- Permite aplicar controles de calidad (reviews, checks de CI, etc.).

---

## 3) `.gitignore` + evidencia

Se creó la rama `feature/gitignore` y se añadió `.gitignore` con:

- `*.log` para excluir archivos de logs generados automáticamente.
- `__pycache__/` para excluir cachés/artefactos locales de Python.

**Evidencia:**

- Se generó `prueba.log` localmente y se comprobó con `git status` que NO aparece como archivo a commitear.
- Archivo de evidencia: `evidencias/gitignore-status.txt`

**PR:** `feature/gitignore -> main` (mergeado)

---

## 4) Creación de ramas de funcionalidad

Se crearon dos ramas de trabajo sin merge inmediato:

- `feature/suma`: añade `suma(a, b)` a `operations.py`
- `feature/resta`: añade `resta(a, b)` a `operations.py`

Ambas ramas se subieron a GitHub y se abrieron PRs contra `main` (sin merge inicial).

---

## 5) Conflicto y resolución

### Cómo se provocó el conflicto

1. Se mergeó primero el PR de `feature/suma` a `main`.
2. Luego, en local, desde `feature/resta` se ejecutó `git merge main`.
3. Se produjo un conflicto en `operations.py` porque ambas ramas modificaban el mismo fichero (y la misma zona lógica).

### Cómo se resolvió

Se editó `operations.py` para conservar el resultado final correcto:

def info():
return "Operaciones básicas"

def suma(a, b):
return a + b

def resta(a, b):
return a - b

### Evidencia

1. Historial exportado: evidencias/git-log.txt
2. En ese log se puede ver:

- El merge previo de feature/suma a main
- El commit de resolución del conflicto en feature/resta
- El estado final con ambas funcionalidades integradas

---

## 6) Automatización con GitHub Actions

### Workflow manual + badge

1. Se creó la rama feature/ci y se añadió un workflow manual:

- Archivo: .github/workflows/demo.yml
- Evento: workflow_dispatch
- Input: full_name
- Job imprime el valor por consola (output del workflow)

2. Se añadió un badge en README.md apuntando al workflow.

### Ejecución:

- Se ejecutó desde la pestaña Actions con full_name = "Paris Arcos Martín".

### Evidencia:

- Salida del workflow guardada en: evidencias/action-output.txt

## 7) Evidencias

En la carpeta evidencias/ existen:

- EVIDENCIAS.md (este documento)
- gitignore-status.txt (evidencia de .gitignore)
- git-log.txt (evidencia de resolución de conflicto)
- action-output.txt (evidencia de ejecución de GitHub Actions)
- carpeta img con screenshots de todos los pasos
