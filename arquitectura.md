# Arquitectura

Las piezas del proyecto, cómo se conectan y dónde vive cada una. El porqué de cada elección va en `decisiones.md`; lo que está hecho, en `estado.yaml`.

## Las piezas

| Pieza | Tecnología | Dónde vive | Sesión |
|---|---|---|---|
| Página y app | HTML, CSS y JavaScript en un archivo, publicado en Vercel | `apps/[tu-proyecto]/web/` | 1 y 2 |
| Datos y login | Supabase: tablas, usuarios y seguridad a nivel de fila (RLS) | Proyecto de Supabase; SQL en `apps/[tu-proyecto]/sql/` | 2 |
| Modelo | Python (scikit-learn), servido como API en Render | `apps/[tu-proyecto]/api/` | 3 |
| Servidor MCP | [por decidir en la sesión 4] | `apps/[tu-proyecto]/mcp/` | 4 |
| Agente | [por decidir en la sesión 5] | `apps/[tu-proyecto]/agente/` | 5 y 6 |

## Cómo se conectan

```
navegador ──> web/ en Vercel ──> Supabase (tablas y login)
                    │
                    └──> modelo en Render (sesión 3)
asistente de IA ──> servidor MCP ──> Supabase y modelo (sesión 4)
agente programado ──> MCP ──> aviso por Telegram (sesiones 5 y 6)
```

[Ajusta el dibujo a tu proyecto.]

## Pieza actual: la app con login (S2)

- **Tablas y columnas:** [tu tabla de datos, con su clave primaria, y la tabla de lo que guarda cada usuario.]
- **Pantallas:** [lista con filtros, entrar o crear cuenta, lo guardado.]
- **Quién entra:** [cualquiera con email y contraseña, o solo algunas personas.]
- **Qué guarda cada usuario:** [favoritos, notas, alertas...]
- **Seguridad (RLS), en una línea:** [por ejemplo, "los datos los lee todo el mundo; lo guardado, solo su dueño".]
