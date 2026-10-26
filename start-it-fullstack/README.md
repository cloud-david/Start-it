# Start-It — Full stack (Node.js + PostgreSQL)

Se conserva el diseño corporativo del `index.html` original. El servidor Express sirve la web y `/api/*` desde el mismo origen. PostgreSQL almacena un estado compartido con control de versiones para evitar sobrescrituras concurrentes. Los datos de ejemplo se crean únicamente si la tabla está vacía.

## Ejecutar

1. Node.js 20 o superior y PostgreSQL.
2. Define `DATABASE_URL` como variable de entorno. No guardes la contraseña en GitHub.
3. `npm install`
4. `npm start`
5. Visita `http://localhost:3000`.

Usuarios ficticios: `COL-001` / `ana@empresa.com` y `ADM-001` / `admin@empresa.com`.

## Render

**Importante:** el servicio existente `start-it-xali` es un **Static Site**. No es posible convertirlo directamente en un servicio web Node.js. Crea un nuevo **Web Service** conectado al repositorio actualizado, con `npm install`, `npm start` y `DATABASE_URL` apuntando a PostgreSQL. El archivo `render.yaml` sirve como referencia para un Blueprint nuevo, pero no reemplaza ni migra el servicio estático existente. El hostname `start-it-xali.onrender.com` sigue asociado al sitio estático mientras ese servicio exista; no prometemos conservarlo al crear otro servicio. Primero despliega y prueba la nueva URL; después planifica el cambio de URL/dominio.

## Notas de alcance y seguridad

- Demostración académica: ID y correo **no son autenticación segura para producción**. No cargar datos reales de personal ni información sensible.
- Cookies httpOnly de 8 horas, control de rol del lado servidor, rate limit y SQL parametrizado.
- La persistencia está en PostgreSQL. Para facilitar la migración del prototipo, los catálogos se guardan como un documento JSONB compartido, no en tablas relacionales independientes. Es una etapa intermedia; se recomienda normalizar el modelo antes de producción.
- El colaborador recibe solo sus datos, sin historial ni catálogos completos.
- No se integran tickets ni ServiceNow. Las URLs corporativas quedan por configurar.
- Las plantillas siguen siendo referencias de texto; no se incluyen archivos reales.
- No se ha ejecutado una suite automatizada de integración en este paquete. Probar CRUD, permisos, persistencia y concurrencia antes de publicar.
