# ¿Que es AgentHub?

Es una plataforma SaaS donde las empresas pueden alquilar agentes de IA — asistentes inteligentes preconfigurados que pueden equiparse con distintas skills (habilidades como navegar por la web, leer documentos o gestionar calendarios) y desplegarse para tareas de negocio específicas

## Stack 

- HTML semantico (section, table, nav, header, main)
- Tailwind v4.3 via CDN
- JavaScript Vanilla

## Restricciones

- Sin framework
- Sin backend ni conexiones a API
- Sin archivos CSS externos ni estilos inline
- Todos los datos hardcodeados

--- 

## Secciones del panel

### 1. Dashboard

1. Cuatro tarjetas de métricas en grid responsive 2×2: ingresos totales (este mes), pérdidas por descuentos/cupones, agentes activos y agentes fallando. Cada tarjeta muestra un icono, una etiqueta descriptiva y un valor numérico hardcodeado.
2. Cada tarjeta usa un color de acento distinto según el tipo de métrica (verde para ingresos, rojo para pérdidas, azul para activos, amarillo para fallando) y una sombra sutil.
3. Debajo de las tarjetas, un div de ancho completo con borde discontinuo (dashed) y una etiqueta centrada "Gráfico de actividad semanal" como placeholder.

### 2. Gestión de usuarios

1. Tabla con 5 filas de usuarios hardcodeados. Columnas: nombre, email, plan (Free/Pro/Enterprise) y badge de estado (activo/suspendido) con color según estado.
2. Cada fila tiene un botón ⋮ que abre un dropdown con dos opciones: "Ver detalle" y "Eliminar".
3. "Ver detalle" abre un modal overlay con el registro completo del usuario (nombre, email, plan, estado, fecha de registro). El modal se cierra con botón X y con clic en el backdrop.

### 3. Gestión de agentes

1. Listado de al menos 4 agentes. Cada entrada muestra: nombre del agente, propietario, badge de estado (activo/inactivo/fallando con colores verde/gris/rojo) y un control expandible para skills.
2. Las skills de cada agente están colapsadas por defecto. Al hacer clic en el control expandible, se revelan con transición suave (max-height + transition). Un segundo clic las colapsa.
3. Cada agente tiene un dropdown ⋮ con "Configurar" y "Eliminar". "Configurar" abre un modal con el prompt de sistema del agente dentro de un textarea editable.

### 4. Skills

1. Catálogo de al menos 4 skills. Cada una muestra: nombre, descripción breve y contador de agentes que la tienen habilitada.
2. En la parte superior de la sección, un párrafo breve explica qué es una "skill" en el contexto de AgentHub (capacidad que se adjunta a un agente para ampliar lo que puede hacer).
3. Cada skill tiene un dropdown ⋮ con "Ver detalle" (abre modal con descripción completa y lista de agentes asociados) y "Eliminar".

### 5. Contrataciones de agentes

1. Tabla con al menos 4 contratos. Columnas: cliente, agente alquilado, skills contratadas (como badges), fecha inicio, fecha fin e importe total pagado.
2. Cada fila tiene un dropdown ⋮. "Ver detalle" abre un modal con el desglose completo: datos del cliente, agente, lista de skills contratadas con precio individual de cada una y el total.
3. Los contratos pasados y activos se distinguen visualmente con un badge de estado (activo/finalizado).

### 6. Log de errores

1. Al menos 6 entradas de error hardcodeadas. Cada una muestra: timestamp, nombre del agente, badge de tipo de error con color según gravedad (crítico=rojo, advertencia=amarillo, info=azul) y descripción breve.
2. Cada entrada tiene un dropdown ⋮ con "Ver detalle" (abre modal con la traza completa del error) y "Marcar como resuelto".
3. Las entradas marcadas como resueltas cambian visualmente (opacidad reducida o tachado) para distinguirlas de las pendientes.

---

## Inventario de componentes reutilizables

- **Sidebar**: navegación lateral persistente con enlaces a las 6 secciones e indicador visual de sección activa.
- **Dropdown de acciones (⋮)**: menú desplegable posicionado junto al botón, se cierra al hacer clic fuera.
- **Modal**: overlay centrado con fondo oscuro semitransparente, botón X de cierre, se cierra también al hacer clic en el backdrop.
- **Badge de estado**: etiqueta pequeña con color según valor (activo/inactivo/fallando, crítico/advertencia/info).
- **Tarjeta de métrica**: contenedor con icono, etiqueta, valor y color de acento.
- **Lista colapsable de skills**: contenedor con transición de altura para mostrar/ocultar contenido.
- **Toggle dark mode**: botón en la barra superior que alterna la clase `dark` en el elemento raíz y persiste el estado entre secciones.

---

## Criterios de aceptación

1. Las 6 secciones son accesibles desde la sidebar y se muestran correctamente.
2. El toggle dark/light cambia todo el panel y el estado persiste al navegar entre secciones.
3. Todos los dropdowns ⋮ se abren al hacer clic y se cierran al hacer clic fuera.
4. "Ver detalle" abre un modal en al menos 4 secciones distintas.
5. Los modales se cierran con el botón X y con clic en el backdrop.
6. Las skills de los agentes están colapsadas por defecto y se expanden/colapsan con transición visible.
7. Los datos hardcodeados son consistentes entre secciones (un agente que aparece en Gestión de agentes también aparece en Contrataciones y Log de errores con el mismo nombre).
8. El HTML usa etiquetas semánticas: section, table, nav, header, main.
9. El layout es usable en viewports de escritorio y tablet.
10. No se usan estilos inline ni archivos CSS externos — solo clases de Tailwind.