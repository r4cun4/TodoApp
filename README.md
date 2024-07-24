# ToDo App

Este es el proyecto final de un curso de Udemy que realicé, el cual es una aplicación fullstack para la gestión de tareas (ToDo List).

**Autor del curso**: [Eric Roby](https://www.udemy.com/course/fastapi-the-complete-course/)

## Tecnologías Utilizadas

- **Frontend**: Jinja2
- **Seguridad y Autenticación**: OAuth2
- **Hashing de Contraseñas**: Bcrypt
- **Base de Datos**: SQLite3
- **Generación de JWT**: JOSE
- **Backend**: FastAPI

## Descripción

La aplicación de ToDo List permite a los usuarios registrarse y gestionar sus propias tareas. Incluye funcionalidades como:

- Registro y autenticación de usuarios.
- Creación, edición y eliminación de tareas.
- Edición de contraseñas.
- Visualización de las tareas específicas de cada usuario.

## Instalación

1. Clona este repositorio:
    ```sh
    git clone <URL_DEL_REPOSITORIO>
    ```
2. Navega al directorio del proyecto:
    ```sh
    cd <NOMBRE_DEL_DIRECTORIO>
    ```
3. Crea y activa un entorno virtual:
    ```sh
    python -m venv venv
    source venv/bin/activate # En Windows usa `venv\Scripts\activate`
    ```
4. Instala las dependencias:
    ```sh
    pip install -r requirements.txt
    ```
5. Ejecuta la aplicación:
    ```sh
    uvicorn main:app --reload
    ```

## Uso

Una vez que la aplicación está en funcionamiento, puedes acceder a ella en `http://127.0.0.1:8000`.

### Endpoints

- **/register**: Registro de nuevos usuarios.
- **/login**: Autenticación de usuarios existentes.
- **/todos**: CRUD de tareas (requiere autenticación).
  - **GET /todos**: Obtiene todas las tareas del usuario autenticado.
  - **POST /todos**: Crea una nueva tarea.
  - **PUT /todos/{id}**: Actualiza una tarea existente.
  - **DELETE /todos/{id}**: Elimina una tarea.

### Ejemplo de Uso

1. **Registro de Usuario**:

    Envía una solicitud POST a `/register` con el siguiente cuerpo:
    ```json
    {
        "username": "nuevo_usuario",
        "password": "password123"
    }
    ```

2. **Inicio de Sesión**:

    Envía una solicitud POST a `/login` con el siguiente cuerpo:
    ```json
    {
        "username": "nuevo_usuario",
        "password": "password123"
    }
    ```

    La respuesta incluirá un token JWT que debes usar para autenticarte en los endpoints protegidos.

3. **Gestión de Tareas**:

    Envía una solicitud GET a `/todos` para obtener las tareas, usando el token JWT en los encabezados de autorización:
    ```sh
    Authorization: Bearer <token>
    ```

## Contribución

Si deseas contribuir a este proyecto, por favor, sigue estos pasos:

1. Haz un fork del repositorio.
2. Crea una nueva rama (`git checkout -b feature/nueva-funcionalidad`).
3. Realiza los cambios necesarios y haz commit (`git commit -am 'Añade nueva funcionalidad'`).
4. Empuja los cambios a la rama (`git push origin feature/nueva-funcionalidad`).
5. Abre un Pull Request.
