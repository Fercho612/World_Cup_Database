# Base de Datos del Mundial

Base de datos PostgreSQL con los partidos de los Mundiales de fútbol 2014 y 2018, cargada desde un CSV con un script de Bash y consultada con SQL.

Proyecto de la certificación **Relational Database** de [freeCodeCamp](https://www.freecodecamp.org/).

## Qué hace

- `insert_data.sh` lee `games.csv`, inserta cada equipo una sola vez y carga todos los partidos con sus goles.
- `queries.sh` responde preguntas sobre los datos: total y promedio de goles, partido con más goles, campeón de 2018, equipos de octavos de 2014, campeones por año, entre otras.

## Tecnologías

PostgreSQL · Bash · SQL

## Modelo de datos

| Tabla | Columnas principales |
| --- | --- |
| `teams` | `team_id`, `name` |
| `games` | `game_id`, `year`, `round`, `winner_id` → `teams`, `opponent_id` → `teams`, `winner_goals`, `opponent_goals` |

## Cómo ejecutarlo

Requisitos: PostgreSQL y una terminal Bash.

```bash
# 1. Crear la base con los datos ya cargados
psql -U postgres < worldcup.sql

# 2. Correr las consultas
chmod +x queries.sh
./queries.sh
```

Los scripts se conectan con el usuario `freecodecamp`; si usás otro, cambiá la variable `PSQL` al comienzo de cada script.

Para recargar los datos desde cero con `insert_data.sh` hace falta el archivo `games.csv` del proyecto de freeCodeCamp.

## Lo que aprendí

- Diseñar tablas relacionadas con claves primarias y foráneas.
- Cargar datos desde CSV con un bucle de Bash evitando duplicados.
- Consultas con `JOIN`, `SUM`, `AVG`, `ROUND`, `MAX`, `COUNT`, `DISTINCT`, `LIKE` y `ORDER BY`.
