# Desarrollo para Dispositivos Inteligentes

Proyecto desarrollado con **FastAPI** y **SQLModel** para la creación de una API REST enfocada en la gestión de usuarios.

## Descripción

La aplicación permite realizar operaciones CRUD sobre usuarios, incluyendo:

* Crear usuarios.
* Consultar todos los usuarios.
* Consultar un usuario por su ID.
* Actualizar información de usuarios.
* Eliminar usuarios.
* Validar los datos recibidos mediante esquemas.
* Proteger las contraseñas utilizando **Argon2**.
* Configurar **CORS** para permitir la comunicación con aplicaciones externas.

## Tecnologías utilizadas

* Python
* FastAPI
* SQLModel
* Pydantic
* SQLite
* Passlib
* Argon2
* Docker

## Estructura del proyecto

```text
ClaseCuatro/
│
├── api/
│   └── v1/
│       └── user_api.py
│
├── core/
│   ├── cors.py
│   └── security.py
│
├── db/
│   └── database.py
│
├── models/
│   └── user_model.py
│
├── schemas/
│   └── user_schemas.py
│
├── docker-compose.yml
├── main.py
├── diegodb.db
└── .gitignore
```

## Funcionalidades principales

### Crear usuario

Permite registrar un nuevo usuario mediante una solicitud `POST`.

Antes de guardar la información se verifica que el correo y el nombre de usuario no estén registrados. La contraseña se almacena utilizando un hash generado con Argon2.

### Consultar usuarios

La API permite obtener:

* Todos los usuarios mediante `GET`.
* Un usuario específico mediante su ID.

### Actualizar usuario

Permite modificar los datos de un usuario existente mediante `PUT`.

### Eliminar usuario

Permite eliminar un usuario mediante `DELETE`.

## Rutas principales

| Método | Ruta                      | Función                       |
| ------ | ------------------------- | ----------------------------- |
| GET    | `/`                       | Mensaje de bienvenida         |
| GET    | `/health`                 | Verificar el estado de la API |
| POST   | `/api/v1/users/`          | Crear usuario                 |
| GET    | `/api/v1/users/`          | Obtener usuarios              |
| GET    | `/api/v1/users/{user_id}` | Obtener usuario por ID        |
| PUT    | `/api/v1/users/{user_id}` | Actualizar usuario            |
| DELETE | `/api/v1/users/{user_id}` | Eliminar usuario              |

## Documentación de la API

FastAPI genera automáticamente una interfaz de documentación mediante Swagger.

Con el proyecto ejecutándose, se puede acceder a:

```text
http://127.0.0.1:8000/docs
```

Desde esta página se pueden consultar y probar las diferentes rutas de la API.

## Ejecución del proyecto

Primero se deben instalar las dependencias necesarias:

```bash
pip install "fastapi[standard]"
pip install sqlmodel
pip install passlib[argon2]
```

Después se puede iniciar el servidor con:

```bash
uv run fastapi dev
```

La API estará disponible en:

```text
http://127.0.0.1:8000
```

## Seguridad

Las contraseñas no se almacenan directamente en la base de datos. Antes de guardarlas, se utiliza **Argon2** para generar un hash, permitiendo proteger la información de los usuarios.

## Autor

**Diegoxd1y3**

Proyecto realizado como parte de la materia **Desarrollo para Dispositivos Inteligentes**.
