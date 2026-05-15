# Evidencia del uso de IA - HighSport Inventario

## ¿Qué herramienta usamos?
Usamos Claude de Anthropic como asistente durante todo el desarrollo del proyecto.

---

## Prompts que usamos

El primero que le mandamos fue algo así:

> "Actúa como un desarrollador senior y estudiante de Programación Orientada a
> Objetos. Necesito construir un proyecto académico en Java con Spring Boot para
> segundo semestre, con enfoque en POO aplicada y API REST simple."

Después le compartimos el repositorio del frontend que ya teníamos hecho y le
explicamos que era un sistema de gestión de inventario para una marca de ropa
deportiva llamada HighSport.

Cuando ya teníamos los requisitos del profesor se los pasamos completos y le
preguntamos cómo estructurar el proyecto correctamente según lo que pedía.

---

## ¿Qué generó la IA?

La IA nos ayudó a generar la estructura base del proyecto — los paquetes, las
clases del modelo, los DTOs, los repositorios, los servicios, los controladores
y el manejador de excepciones. También nos explicó cada parte del código mientras
lo íbamos construyendo para que pudiéramos entenderlo.

---

## ¿Qué corregimos o ajustamos nosotros?

Hubo un error importante al principio — la IA arrancó usando JPA, Hibernate y
base de datos H2, que eran cosas que el profesor prohibía explícitamente. Cuando
le mostramos los requisitos reales del proyecto, nos ayudó a replantear todo desde
cero usando Map en memoria como pedía el enunciado.

También tuvimos que corregir un error en la clase Producto donde el nombre del
archivo tenía la p en minúscula y Java exige que coincida exactamente con el
nombre de la clase.

Durante las pruebas en Postman verificamos que todos los endpoints respondieran
correctamente — tanto los casos exitosos como los errores 400 y 404.

---

## ¿Qué aprendimos en el proceso?

Entendimos cómo funciona la arquitectura por capas y por qué es importante separar
responsabilidades. También aprendimos para qué sirven los DTOs, cómo funciona la
inyección de dependencias en Spring y por qué nunca se deben exponer los modelos
directamente en la API.

La IA fue una herramienta de apoyo pero cada parte del código la revisamos y la
entendemos — eso es lo que vamos a demostrar en la sustentación.