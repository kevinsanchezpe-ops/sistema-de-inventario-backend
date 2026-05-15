# HighSport - Sistema de Gestión de Inventario

Este proyecto es una API REST desarrollada en Java con Spring Boot para gestionar
el inventario de HighSport, una marca de ropa deportiva. Fue construido como proyecto
académico de segundo semestre con enfoque en Programación Orientada a Objetos y
arquitectura por capas.

---

## ¿Cómo ejecutar el proyecto?

Antes de arrancar asegúrate de tener instalado:
- Java 17 o superior
- Maven (viene incluido en el proyecto con mvnw)

Pasos para ejecutar:

1. Clona o descarga el proyecto
2. Abre una terminal en la carpeta raíz del proyecto
3. Ejecuta el siguiente comando:


En Windows:

mvnw.cmd spring-boot:run

4. Cuando veas en consola "Started InventarioApplication" el servidor está listo
5. La API queda disponible en http://localhost:8080

---

## Estructura del proyecto

El proyecto está organizado en capas con responsabilidades separadas:

- model → clases que representan las entidades del negocio
- dto → objetos de transferencia de datos (entrada y salida de la API)
- repository → acceso y almacenamiento de datos en memoria con Map
- service → lógica del negocio
- controller → endpoints HTTP
- exception → manejo centralizado de errores

---

## Endpoints disponibles

### Health

| Método | Endpoint  | Descripción                  |
|--------|-----------|------------------------------|
| GET    | /health   | Verifica que el servidor esté activo |

### Productos

| Método | Endpoint              | Descripción                  |
|--------|-----------------------|------------------------------|
| POST   | /api/productos        | Crear un nuevo producto      |
| GET    | /api/productos        | Listar todos los productos   |
| GET    | /api/productos/{id}   | Buscar un producto por ID    |
| PUT    | /api/productos/{id}   | Actualizar un producto       |
| DELETE | /api/productos/{id}   | Eliminar un producto         |

### Usuarios

| Método | Endpoint              | Descripción                  |
|--------|-----------------------|------------------------------|
| POST   | /api/usuarios         | Crear un nuevo usuario       |
| GET    | /api/usuarios         | Listar todos los usuarios    |
| GET    | /api/usuarios/{id}    | Buscar un usuario por ID     |
| PUT    | /api/usuarios/{id}    | Actualizar un usuario        |
| DELETE | /api/usuarios/{id}    | Eliminar un usuario          |

---

## Ejemplos de uso

### Crear un producto

Request:
POST /api/productos
Content-Type: application/json

{
"nombre": "Camiseta Dry Fit",
"categoria": "Camisetas",
"talla": "M",
"color": "Negro",
"precio": 49900,
"stock": 20
}

Response 201 Created:
{
"id": 1,
"nombre": "Camiseta Dry Fit",
"categoria": "Camisetas",
"talla": "M",
"color": "Negro",
"precio": 49900.0,
"stock": 20
}

---

### Crear un usuario

Request:
POST /api/usuarios
Content-Type: application/json

{
"nombre": "Kevin Sanchez",
"email": "kevin@highsport.com",
"password": "123456",
"rol": "ADMIN"
}

Response 201 Created:
{
"id": 1,
"nombre": "Kevin Sanchez",
"email": "kevin@highsport.com",
"rol": "ADMIN"
}

Nota: el password nunca aparece en la respuesta por seguridad.

---

### Respuesta de error 404

{
"timestamp": "2025-04-10T10:30:00",
"status": 404,
"error": "Not Found",
"mensaje": "Producto no encontrado con id: 5"
}

### Respuesta de error 400

{
"timestamp": "2025-04-10T10:30:00",
"status": 400,
"error": "Bad Request",
"mensaje": "El nombre es obligatorio"
}

---

## Decisiones técnicas

La persistencia se maneja con Map<Long, ...> en memoria, lo que significa que
los datos se reinician cada vez que el servidor se apaga. Esto fue una decisión
intencional para cumplir con los requisitos académicos del proyecto.

No se usó JPA ni Hibernate. Todo el acceso a datos es manual, lo que nos permitió
entender con más claridad cómo funciona cada capa del sistema.

Los DTOs separan el modelo interno del contrato de la API. Por ejemplo, el usuario
tiene password internamente pero ese campo nunca sale en ninguna respuesta.

---

## Evidencia del uso de IA

Durante el desarrollo se usó Claude (Anthropic) como asistente para:
- Proponer la estructura inicial del proyecto
- Generar el código base de cada capa
- Explicar cada decisión de diseño en tiempo real

El grupo revisó, entendió y en algunos casos ajustó el código generado.
Cada integrante está en capacidad de explicar el funcionamiento del sistema,
el flujo controller → service → repository, las validaciones y el manejo de errores.