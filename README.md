# opencode-skill-commit-messages

Skill de [OpenCode](https://opencode.ai) para escribir mensajes de commit en
proyectos personales: Conventional Commits en español, impersonales y con un
cambio lógico por commit.

No cubre ramas, merges, releases ni resolución de conflictos. Si el repositorio es
de la empresa (ramas con código `COD###`, `DEV_`, `DOC_`, `release/` o `hotfix/`,
o remoto en un host interno), esta skill no aplica.

## Instalación

```bash
mkdir -p ~/.config/opencode/skills
git clone https://github.com/TUUSUARIO/opencode-skill-commit-messages.git \
  ~/.config/opencode/skills/commit-personal
```

OpenCode descubre automáticamente `~/.config/opencode/skills`, así que no hace
falta tocar `opencode.json`. Si la skill no aparece en la lista, ejecuta `/reload`
en la sesión.

Para un solo proyecto, clónalo dentro de `.opencode/skills/` del repo.

## Formato

```text
<tipo>: <descripción en español, impersonal, sin punto final>
```

Tipos permitidos: `feat`, `fix`, `docs`, `style`, `test`, `perf`, `build`, `ci`,
`chore`, `revert`. No existe `refactor` en esta convención.

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

## Uso

Invócala explícitamente:

```text
Usa commit-personal. Haz commit de los cambios.
```

O simplemente pide "haz commit" / "guarda los cambios" en un repo personal y la
skill se activa sola.

## Estructura

```text
.
├── SKILL.md
├── README.md
└── LICENSE
```

## Licencia

GNU General Public License v3.0. Ver [LICENSE](LICENSE).
