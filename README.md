# U4S8 — García Vásquez Óscar

## Demo en vivo (producción)
https://u4s8-garcia-vasquez-oscar.onrender.com

## Qué hace este proyecto
Sistema web profesional desarrollado en Django para la gestión de servicios profesionales. Permite a los usuarios registrarse, iniciar sesión y gestionar exclusivamente sus propios servicios con un aislamiento estricto de datos. Incluye operaciones CRUD completas, filtrado por búsqueda en tiempo real y paginación de resultados. La interfaz está diseñada con Tailwind CSS para ofrecer una experiencia moderna, limpia y totalmente responsive.

## Stack técnico
Django + MySQL (Aiven) + Tailwind CSS + Render

## Cómo se prueba el aislamiento por usuario
El sistema implementa un control de acceso estricto mediante `@login_required` y filtrado por el propietario del registro (`propietario=request.user`). Para comprobarlo:
1. Regístrese con el usuario "Usuario A" y cree dos servicios (ej. "Servicio A1", "Servicio A2").
2. Cierre sesión e inicie sesión con el "Usuario B".
3. Al acceder al listado de servicios, comprobará que el "Usuario B" no visualiza los servicios del "Usuario A", garantizando la privacidad y el aislamiento de datos entre cuentas.

## Historial de unidades
- Unidad 1: portafolio estático con HTML5 + Tailwind
- Unidad 2: modelo Servicio migrado a MySQL, deploy dinámico en Render
- Unidad 3: CRUD completo con ModelForms + autenticación y sesiones
- Unidad 4: paginación, búsqueda, UI review y defensa final

## Instalación y Ejecución Local

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/garciavasquezdsm3/u4s8-garcia-vasquez-oscar.git
   cd u4s8-garcia-vasquez-oscar
   ```

2. **Crear y activar el entorno virtual:**
   ```bash
   python -m venv env
   # En Windows:
   env\Scripts\activate
   ```

3. **Instalar dependencias:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configurar las variables de entorno:**
   Crea un archivo `.env` en la raíz del proyecto basado en `.env.example`:
   ```env
   SECRET_KEY=tu-clave-secreta
   DEBUG=True
   ALLOWED_HOSTS=127.0.0.1,localhost
   CSRF_TRUSTED_ORIGINS=http://127.0.0.1:8000
   DB_NAME=defaultdb
   DB_USER=avnadmin
   DB_PASSWORD=tu-password-aiven
   DB_HOST=tu-host-aiven.aivencloud.com
   DB_PORT=28536
   ```

5. **Aplicar migraciones y ejecutar:**
   ```bash
   python manage.py migrate
   python manage.py runserver
   ```
   Abre en tu navegador: `http://127.0.0.1:8000/`

## Despliegue en Producción (Render)

* **Build Command:**
  ```bash
  pip install -r requirements.txt && python manage.py collectstatic --noinput && python manage.py migrate
  ```
* **Start Command:**
  ```bash
  gunicorn miproyecto.wsgi
  ```

## Autor
* **Óscar García Vásquez**
* DSM3
