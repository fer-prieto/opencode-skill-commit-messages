---
name: commit-personal
description: Usar siempre que se vaya a escribir un mensaje de commit en un repositorio que NO sea de la empresa. Genera mensajes Conventional Commits en español e impersonales. Activar ante "commit", "commitear", "git commit", "mensaje de commit", "guarda los cambios", "sube los cambios".
---

# Commits personales

Skill para construir el mensaje de commit en proyectos personales. No cubre ramas,
merges, releases ni resolución de conflictos: solo el mensaje.

Si el repositorio es de la empresa (rama con código `COD###`, `DEV_`, `DOC_`,
`release/` o `hotfix/`, o remoto en el host interno), no uses esta skill: usa
`commit-empresa`.

## Formato

```text
<tipo>: <descripción en español, impersonal, sin punto final>
```

## Tipos permitidos

`feat`, `fix`, `docs`, `style`, `test`, `perf`, `build`, `ci`, `chore`, `revert`

No existe `refactor` en esta convención.

## Reglas

1. Un commit = un cambio lógico. Si hay dos cambios distintos, dos commits.
2. Tipo en minúsculas. Descripción en minúsculas salvo nombres propios.
3. Descripción impersonal: `se agrega`, `se corrige`, `se elimina`, `se actualiza`.
   Nunca `agregué`, `agrega tú`, `agregado`.
4. Máximo 72 caracteres en el asunto. Sin punto final.
5. Cuerpo solo si hace falta explicar el porqué. Una línea en blanco después del asunto.
6. Cambio incompatible: `feat!:` o footer `BREAKING CHANGE: <qué se rompe>`.
7. Nunca uses `git commit --no-verify`.
8. No agregues firmas de IA ni `Co-Authored-By`.

## Ejemplos

```text
feat: se agrega validación de RUC en el formulario
fix: se corrige cálculo de totales con descuento
docs: se actualiza guía de instalación
chore: se actualiza versión de dependencias
test: se agregan casos borde del parser
feat!: se elimina el parámetro `legacy` de la API
```

Con cuerpo:

```text
fix: se corrige cálculo de totales con descuento

El descuento se aplicaba antes de sumar el impuesto, lo que producía
diferencias de centavos en facturas con más de diez ítems.
```
