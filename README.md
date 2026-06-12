# ⚡ Consultas Express

Aplicación web **zero-infrastructure** desarrollada como herramienta de soporte para la clasificación y gestión de consultas de clientes en pequeñas y medianas empresas (SMEs).

El sistema está diseñado como una aplicación completamente frontend basada en **HTML, CSS y JavaScript vanilla**, sin dependencias externas ni backend.

---

## Propósito del Sistema

La aplicación está orientada a optimizar flujos de atención al cliente reduciendo el tiempo dedicado a consultas repetitivas mediante:

* Clasificación automática de mensajes entrantes.
* Generación de respuestas basadas en plantillas.
* Asistencia al operador humano (human-in-the-loop).
* Eliminación de infraestructura backend o APIs externas.

---

## Arquitectura General

El proyecto sigue un modelo **zero-infrastructure SPA (Single Page Application)**.

```text id="axp0k2"
consultas-express/
│
├── index.html
├── data.json
├── informe-ejecutivo-consultas-express.html
├── Informe Ejecutivo Consultas Express.pdf
└── README.md
```

---

## Componentes del Sistema

### Núcleo de la Aplicación

Toda la lógica reside en:

```text id="m8xq91"
index.html
```

Este archivo contiene:

* Estructura HTML.
* Estilos CSS embebidos.
* Motor de clasificación.
* Controlador principal (`APP`).
* Renderizado de interfaz.
* Persistencia en localStorage.

---

### Datos Iniciales

```text id="d1kq77"
data.json
```

Contiene un conjunto de interacciones semilla utilizadas para inicializar el sistema en su primer uso.

---

### Documentación Ejecutiva

* Informe técnico en HTML.
* Versión PDF del análisis de impacto.

---

## Flujo de Ejecución

### Pipeline principal

```text id="f7k3lp"
Entrada del usuario
      ↓
Normalización del texto
      ↓
Clasificación por keywords ponderadas
      ↓
Asignación de categoría
      ↓
Generación de respuesta basada en plantilla
      ↓
Edición por operador humano
      ↓
Salida final
```

---

## Motor de Clasificación

### Enfoque

El sistema utiliza un **clasificador basado en palabras clave ponderadas**.

Características:

* Normalización de texto (minúsculas, eliminación de acentos).
* Matching por coincidencia de tokens.
* Asignación de score por categoría.
* Selección de categoría con mayor puntuación.

---

### Categorías Soportadas

El sistema clasifica consultas en dominios como:

* Precio
* Horarios
* Envíos
* Disponibilidad
* Información general
* Soporte
* Otros

---

### Generación de Respuestas

El motor incluye un sistema de plantillas dinámicas que permite:

* Inserción de valores numéricos extraídos del texto.
* Respuestas editables por el operador.
* Adaptación contextual de mensajes.

---

## Gestión de Estado

### Estado global

La aplicación utiliza un objeto central:

```javascript id="s9k2lx"
APP.state
```

Este estado:

* Almacena todas las consultas.
* Mantiene historial de interacciones.
* Se sincroniza con `localStorage`.

---

### Persistencia

No existe backend.

La persistencia se realiza mediante:

* `localStorage` del navegador.
* Serialización JSON del estado.

---

## Renderizado de UI

### Estrategia

Se utiliza un modelo de renderizado imperativo:

```javascript id="r3p9xw"
APP.renderAll()
```

Cada cambio en el estado provoca:

* Re-render completo de la interfaz.
* Actualización del DOM sin frameworks.

---

## Sistema de Datos

### Seed Data

```text id="c7l0pm"
data.json
```

Se utiliza para:

* Inicialización del sistema.
* Simulación de interacciones reales.
* Bootstrap de estado inicial.

---

### Exportación de Datos

El sistema permite exportar el estado completo en formato JSON para:

* Análisis externo.
* Auditoría.
* Backup manual.

---

## Sistema de Analítica

### KPIs Internos

El sistema calcula métricas como:

* Número de consultas procesadas.
* Distribución por categoría.
* Tendencias diarias de uso.

---

### Visualización

Incluye gráficos de:

* Distribución por categorías.
* Evolución temporal de consultas.

---

## Arquitectura de Datos

```text id="z1q9mn"
data.json → APP.state → APP.renderAll() → UI
```

---

## Diseño del Sistema

### Arquitectura Zero-Dependency

No requiere:

* Backend
* Base de datos externa
* Frameworks frontend
* APIs externas

---

### Tecnologías utilizadas

* HTML5
* CSS3 (estilo embebido)
* JavaScript ES6+
* localStorage API

---

## Interacción del Usuario

El sistema opera completamente en el navegador:

1. Entrada de texto.
2. Clasificación automática.
3. Generación de respuesta sugerida.
4. Edición manual.
5. Confirmación final.

---

## Ventajas de la Arquitectura

* Implementación extremadamente ligera.
* Despliegue instantáneo.
* Sin costes de infraestructura.
* Funcionamiento offline parcial.
* Alta velocidad de respuesta.
* Mantenimiento mínimo.
* Fácil extensibilidad del sistema de categorías.

---

## Mantenimiento

### Añadir nuevas categorías

Se realiza modificando el sistema de keywords dentro del motor de clasificación.

### Añadir nuevas plantillas

Se agregan en el módulo de respuestas dinámicas del controlador `APP`.

---

## Despliegue

Compatible con cualquier hosting estático:

* GitHub Pages
* Netlify
* Vercel
* Cloudflare Pages
* Servidores HTTP simples

---

## Licencia

Proyecto reutilizable como base para sistemas de clasificación de texto y herramientas internas de soporte sin infraestructura backend.
