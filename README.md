# Talavera Dolores · Tienda móvil con realidad aumentada en Flutter y TDD

**Materia:** Desarrollo de Aplicaciones Móviles
**Alumno:** González López Yael Isaac
**Fecha:** 20 de noviembre de 2026

## Descripción

Tienda móvil de artesanías de Dolores Hidalgo (talavera, dulces, textiles y decoración) con catálogo, carrito, pagos, perfil de usuario y la opción "Ver en tu espacio", que muestra el producto en 3D y con realidad aumentada a tamaño real. El dinero se maneja en centavos enteros con IVA incluido, cupones y envío gratis desde $800. Los pagos usan una pasarela simulada con validación de tarjeta (Luhn), idempotencia para nunca cobrar dos veces y revalidación de precios. Las cuentas usan contraseñas con sal y hash, mensajes genéricos, bloqueo tras 5 intentos y el token de sesión en almacenamiento seguro. Todo se desarrolló con TDD en capas: dominio, datos y presentación.

> La pasarela de pagos y el servidor de cuentas son simulados: la app no procesa dinero real.

## Estructura del proyecto

<img width="85" height="269" alt="image" src="https://github.com/user-attachments/assets/a8c0511b-49d7-4da2-9e72-13e0c09afc0c" />

## Pruebas de casos (éxito y fallo)

## Pruebas del dominio (24) · test/dominio_test.dart

Pruebas: dinero (formato, IVA incluido y redondeo), producto (modelo 3D solo por https), carrito (subtotal, existencias, límite de 10, envío gratis, cupones, restaurar y guardar), validadores (correo, contraseña, código postal y teléfono) y tarjeta (Luhn, marcas, vigencia, CVV y que nunca se imprima el número completo).

### Éxito (todas en verde)

<img width="402" height="439" alt="image" src="https://github.com/user-attachments/assets/1f0568bd-88c8-42e1-b550-a7942fab51e3" />

### Fallo (IVA incluido de 116.00 es 16.00)

<img width="402" height="429" alt="image" src="https://github.com/user-attachments/assets/41e0111a-5d42-445c-ad8f-872d38ce7532" />

## Pruebas de servicios (22) · test/servicios_test.dart

Pruebas: pasarela simulada e idempotencia, checkout (compra exitosa, rechazo sin tocar inventario, precio que cambió, Luhn inválido, carrito vacío y dirección inválida), bloqueo de intentos y cuentas (registro, correo duplicado, contraseña débil, login, error genérico, bloqueo, sesión y perfil).

### Éxito (todas en verde)

<img width="396" height="449" alt="image" src="https://github.com/user-attachments/assets/7b283cd7-32ee-46fd-b51c-133d9dee02ee" />

### Fallo (IDEMPOTENCIA: misma clave dos veces cobra una sola vez)

<img width="400" height="452" alt="image" src="https://github.com/user-attachments/assets/e8fa972b-eb82-4dbc-b928-499706bd17ad" />

## Pruebas de ViewModels (14) · test/viewmodels_test.dart

Pruebas: catálogo con filtros y búsqueda, carrito que persiste y muestra errores, sesión con registro, login genérico y favoritos, y checkout por pasos con clave de idempotencia y protección contra doble toque.

### Éxito (todas en verde)

<img width="401" height="414" alt="image" src="https://github.com/user-attachments/assets/b2d2197b-c621-4a29-ba7f-c517dfa24436" />

### Fallo (filtra por categoría, texto y AR combinados)

<img width="401" height="416" alt="image" src="https://github.com/user-attachments/assets/338268f9-212e-40fc-a55f-a7e0af33daf6" />

## Todas las pruebas en verde (60)

<img width="392" height="47" alt="image" src="https://github.com/user-attachments/assets/226eb2f5-4880-42f5-899b-5823f68a31f4" />

## Evidencia de la aplicación

### Catálogo

<img width="317" height="650" alt="WhatsApp Image 2026-11-20 at 12 45 30" src="https://github.com/user-attachments/assets/3e5b645b-c065-451f-b862-bb07a53744c1" />

### Ver en tu espacio (modelo 3D / realidad aumentada)

<img width="317" height="650" alt="WhatsApp Image 2026-11-20 at 12 45 30 (1)" src="https://github.com/user-attachments/assets/59b485dd-ed69-4957-aa0e-cb52ee6e2f76" />

### Carrito con cupón y envío

<img width="317" height="650" alt="WhatsApp Image 2026-11-20 at 12 45 30 (2)" src="https://github.com/user-attachments/assets/6de7eee6-1511-4e3a-9936-7054c49b0ace" />

### Pago exitoso

<img width="317" height="650" alt="WhatsApp Image 2026-11-20 at 12 45 30 (3)" src="https://github.com/user-attachments/assets/bb182323-b7d4-4342-aab8-0895bc938fe3" />
