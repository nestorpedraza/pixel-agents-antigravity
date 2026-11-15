## Graphify Knowledge Graph + Estándar de Documentación (`graphify-out/`)

Este monorepo (`c:\react-native`) mantiene un grafo de conocimiento arquitectónico y de producto en `graphify-out/` que conecta los 4 sistemas (`node-backend-supabase-buskdos`, `appbuskdos`, `landing-page-buskdos`, `buskdos-admin`) y las reglas oficiales de negocio (`REGLAS_NEGOCIO_PRECIOS_BUSKDOS.txt`, `MATRIZ_PERMISOS_ROLES.md`, `AUDITORIA_NOTIFICACIONES_Y_MENSAJES.md`, `DEPLOY_HETZNER_STAGE_PROD.md`, `PROMPT_DOCUMENTACION.md`).

### 1. Estándar Obligatorio al Documentar Módulos (5 Secciones de Negocio y Producto)
Cada vez que generes o actualices páginas de módulos en la Wiki (`graphify-out/wiki/`) o en la bóveda de Obsidian (`graphify-out/obsidian-vault/_COMMUNITY_*.md`), sigue estrictamente la estructura definida en [`PROMPT_DOCUMENTACION.md`](file:///c:/react-native/PROMPT_DOCUMENTACION.md):
1. **Descripción General (Propósito de Producto)**: Qué hace el módulo en términos de producto y qué valor entrega.
2. **Casos de Uso / Dónde se utiliza (Ubicación y Entornos)**: En qué pantallas, flujos y proyectos (`appbuskdos`, `landing-page-buskdos`, `node-backend-supabase-buskdos`, `buskdos-admin`) está activo.
3. **Reglas de Negocio**: Condiciones comerciales (Plan Free vs. Pro, tarifas escalonadas), validaciones de dominio e invariantes operativas.
4. **Roles y Permisos Involucrados**: Qué roles participan en cliente/backend (`USER`, `ORG_OWNER`, `ORG_ADMIN`, `ORG_ANALYST`, `STORE_MANAGER`, `STORE_STAFF` en BD) o en `buskdos-admin` (`admin` / `staff` de Supabase Auth vía conexión directa a BD por Air-Gap) y qué pueden hacer según `MATRIZ_PERMISOS_ROLES.md`.
5. **Dependencias y Relaciones entre Sistemas**: Cómo se comunican los 4 sistemas (diagrama Mermaid, endpoints REST/WebSocket, tablas PostgreSQL y comunidades conectadas), dejando la tabla técnica de archivos/símbolos como referencia al final.

### 2. Consulta del Grafo (AI-First)
1. **Punto de entrada humano y de agente**:
   - Lee [`00_ARQUITECTURA_Y_REGLAS_BUSKDOS.md`](file:///c:/react-native/graphify-out/obsidian-vault/00_ARQUITECTURA_Y_REGLAS_BUSKDOS.md) o [`wiki/index.md`](file:///c:/react-native/graphify-out/wiki/index.md) para entender el mapa completo del ecosistema.
2. **Usa las herramientas MCP de `graphify` primero**:
   - Invoca el servidor MCP `graphify` pasando `project_path: "c:/react-native"`:
     - `query_graph`, `get_node`, `get_neighbors`, `shortest_path`, `get_community`, `god_nodes`, `graph_stats`.

### 3. Mantenimiento y Exclusión de Ruido (`.graphifyignore`)
- Nunca indexar archivos `.md` internos de reglas/skills de agentes ni plantillas demo (`buskdos-admin/template-components/`), que ya están excluidos en [`.graphifyignore`](file:///c:/react-native/.graphifyignore).
