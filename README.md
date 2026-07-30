# 👩‍💻 Portfolio Estefanía Canales

> Portfolio personal de **Estefanía Canales, Full Stack Developer**, desarrollado con Vue.js. Presenta mis proyectos, mi stack técnico completo (frontend y backend) y mi experiencia profesional.

---

## 📋 Descripción del Proyecto

**Portfolio Estefanía Canales** es una aplicación web completa que presenta mi perfil profesional como Full Stack Developer, los proyectos que he desarrollado (frontend con Vue/React y proyectos full stack con Laravel), mis habilidades técnicas y profesionales, y un sistema de contacto integrado.

### ✨ Características Principales

- **Diseño responsive** adaptado a todos los dispositivos
- **Tema claro y oscuro** con cambio dinámico
- **Sistema de contacto** integrado con Netlify Forms
- **Galería interactiva** de proyectos con enlaces directos
- **Barras de habilidades animadas** con porcentajes
- **Navegación fluida** entre secciones
- **Soporte multiidioma** (Español/Inglés)
- **Animaciones de entrada** con AOS (Animate On Scroll)
- **Efectos hover** en botones y elementos interactivos
- **SEO optimizado** con meta tags y Open Graph
- **Accesibilidad mejorada** con ARIA labels y navegación por teclado

## 🛠️ Tecnologías Utilizadas

Este portfolio se construye con Vue.js, pero muestra y da soporte a mi trabajo como **Full Stack Developer**. La sección "Habilidades" de la propia web incluye barras con el stack real: HTML & CSS (90%), JavaScript (85%), Vue.js / React (75%), PHP/Laravel (75%), Node.js (70%), C# (65%), Python (65%) y Java (65%).

- **Frontend (este proyecto)**: Vue.js 3, Vite, CSS3 (temas claro/oscuro, responsive)
- **Frontend (otros proyectos enlazados)**: React, JavaScript
- **Backend / Full Stack**: PHP/Laravel, Node.js, Java, C#, Python
- **Bases de datos**: MySQL, PostgreSQL
- **Librerías**: Font Awesome (iconos, vía CDN), AOS - Animate On Scroll (vía CDN)
- **Formularios**: Integración con Netlify Forms
- **Despliegue**: Netlify
- **Control de versiones**: Git

## 📦 Requisitos Previos

- Node.js 18+
- npm o yarn
- Git

## 📁 Estructura del Proyecto

```
src/
├── App.vue              # Componente único: layout, secciones, estado y traducciones (es/en)
├── main.js              # Punto de entrada (monta App.vue en #app)
└── css/
    └── styles.css       # Estilos principales (temas claro/oscuro, responsive)

public/
├── favicon.ico
└── images/              # Imágenes del portfolio
    ├── background-day.png
    ├── background-night.png
    ├── estefania.png
    └── img01.png - img06.png
```

No hay carpeta `components/` ni router: es una single-page app con navegación por anclas (`#inicio`, `#sobremi`, `#portfolio`, `#skills`, `#contacto`), toda contenida en `App.vue`. Font Awesome y AOS se cargan por CDN en `index.html`, no como dependencias npm.

## 🚀 Instalación y Ejecución

### 1. Clonar el repositorio
```bash
git clone [URL_DEL_REPOSITORIO]
cd portfolio-estefaniacanales
```

### 2. Instalar dependencias
```bash
npm install
```

### 3. Ejecutar en modo desarrollo
```bash
npm run dev
```

### 4. Construir para producción
```bash
npm run build
```

### 5. Probar build localmente
```bash
npm run preview
```

## 🌐 Despliegue en Netlify

El proyecto está configurado para despliegue automático en Netlify:

1. **Conectar repositorio** a Netlify
2. **Configuración automática**:
   - Build command: `npm run build`
   - Publish directory: `dist`
   - Node version: 18
3. **Despliegue automático** en cada push a main

## 🔧 Configuración

- **Netlify Forms**: El formulario de contacto se envía por `fetch` (sin recargar la página) y muestra un mensaje de éxito/error inline. Incluye un formulario estático oculto en `index.html` (mismos campos y `name="contact"`) para que el bot de build de Netlify lo detecte; sin ese formulario oculto, Netlify no registra el nombre del formulario y los envíos no llegan.
  - ⚠️ **Pendiente manual en el panel de Netlify**: para recibir un email por cada envío, ve a *Site settings → Forms → Form notifications → Add notification → Email notification* y añade tu correo. Esto no se puede configurar desde el código.
- **Temas**: Sistema de temas claro/oscuro, con la preferencia guardada y restaurada desde localStorage (por defecto: oscuro)
- **Idiomas**: Soporte para español e inglés, con la preferencia guardada y restaurada desde localStorage (por defecto: español)
- **Responsive Design**: Breakpoints optimizados para móviles y desktop
- **Animaciones**: Efectos CSS para barras de habilidades y hover
- **SEO**: Meta tags, Open Graph y Twitter Cards configurados
- **Accesibilidad**: ARIA labels, roles semánticos y navegación por teclado
- **AOS**: Biblioteca de animaciones de entrada configurada

## 📱 Secciones del Portfolio

1. **Inicio**: Presentación personal con enlaces sociales
2. **Sobre Mí**: Información personal e intereses
3. **Portfolio**: Galería de proyectos desarrollados
4. **Habilidades**: Barras de progreso técnicas y profesionales
5. **Contacto**: Formulario de contacto e información de ubicación

---

**Desarrollado por**: Estefanía Canales  
**Fecha**: 15/07/2025