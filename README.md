<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

# Premium Inmuebles - Inmobiliaria

Aplicación web para gestión y portal de una inmobiliaria, desarrollada con las últimas tecnologías del ecosistema moderno de Laravel.

## Tecnologías Utilizadas

- **Backend**: [Laravel 12](https://laravel.com/docs)
- **Frontend**: [Vue.js 3](https://vuejs.org/) (Composition API) junto a [Inertia.js V2](https://inertiajs.com/)
- **Diseño UI**: [Tailwind CSS v4](https://tailwindcss.com/)
- **Iconos**: [Lucide Vue Next](https://lucide.dev/)
- **Autenticación**: [Laravel Fortify](https://laravel.com/docs/fortify)

## Características Principales

- **Landing Page Moderna**: Diseño premium enfocado en tres áreas principales (Vivienda Nueva, Vivienda Usada, Compra de Cartera) usando Tailwind CSS con soporte responsive y Dark Mode.
- **SSR & SPA Hybrid**: Beneficios de carga rápida y SEO (Server-Side Rendering) a través de Inertia V2.
- **Estudio de Cartera Intuitivo**: Optimizado para captar Leads que desean reestructurar sus opciones de crédito.

## Instalación y Configuración (Entorno Local)

Este proyecto está diseñado para funcionar nativamente bajo entorno Laragon (Windows) o Laravel Valet / Herd. 

1. **Clonar repositorio**
   ```bash
   git clone https://github.com/lfiquitiva80/premium-inmobiliaria.git
   cd premium-inmobiliaria
   ```

2. **Instalar Dependencias Backend**
   ```bash
   composer install
   ```

3. **Configurar el Entorno**
   ```bash
   copy .env.example .env
   php artisan key:generate
   ```

   Recuerda configurar las credenciales de base de datos en el archivo `.env`.

4. **Instalar Dependencias Frontend y Compilar**
   ```bash
   npm install
   npm run build
   ```
   *(También puedes utilizar `npm run dev` para levantar el servidor de desarrollo de Vite con Hot Module Replacement).*

## Módulos y Próximos Desarrollos Planeados

- [x] Interfaz de Landing Page principal (`resources/js/pages/Welcome.vue`).
- [ ] Panel de control (Dashboard) para crear, editar o eliminar inventario inmobiliario.
- [ ] Listado de catálogo de propiedades abierto al público.
- [ ] Formularios de captación de Leads para Compra de Cartera, directamente vinculados a base de datos (con posible envío de Mail/Notificación).

---

© 2026 Premium Inmuebles. Todos los derechos reservados.
