# Talavera Dolores · Tienda móvil con realidad aumentada en Flutter y TDD

**Materia:** Desarrollo de Aplicaciones Móviles
**Alumno:** González López Yael Isaac
**Fecha:** 20 de noviembre de 2026

## Descripción

Tienda móvil de artesanías de Dolores Hidalgo (talavera, dulces, textiles y decoración) con catálogo, carrito, pagos, perfil de usuario y la opción "Ver en tu espacio", que muestra el producto en 3D y con realidad aumentada a tamaño real. El dinero se maneja en centavos enteros con IVA incluido, cupones y envío gratis desde $800. Los pagos usan una pasarela simulada con validación de tarjeta (Luhn), idempotencia para nunca cobrar dos veces y revalidación de precios. Las cuentas usan contraseñas con sal y hash, mensajes genéricos, bloqueo tras 5 intentos y el token de sesión en almacenamiento seguro. Todo se desarrolló con TDD en capas: dominio, datos y presentación.

> La pasarela de pagos y el servidor de cuentas son simulados: la app no procesa dinero real.

## Estructura del proyecto

<!-- PEGA AQUÍ LA CAPTURA -->

## Pruebas de casos (éxito y fallo)

## Pruebas del dominio (24) · test/dominio_test.dart

Pruebas: dinero (formato, IVA incluido y redondeo), producto (modelo 3D solo por https), carrito (subtotal, existencias, límite de 10, envío gratis, cupones, restaurar y guardar), validadores (correo, contraseña, código postal y teléfono) y tarjeta (Luhn, marcas, vigencia, CVV y que nunca se imprima el número completo).

### Éxito (todas en verde)

<!-- PEGA AQUÍ LA CAPTURA -->

### Fallo (IVA incluido de 116.00 es 16.00)

<!-- PEGA AQUÍ LA CAPTURA -->

## Pruebas de servicios (22) · test/servicios_test.dart

Pruebas: pasarela simulada e idempotencia, checkout (compra exitosa, rechazo sin tocar inventario, precio que cambió, Luhn inválido, carrito vacío y dirección inválida), bloqueo de intentos y cuentas (registro, correo duplicado, contraseña débil, login, error genérico, bloqueo, sesión y perfil).

### Éxito (todas en verde)

<!-- PEGA AQUÍ LA CAPTURA -->

### Fallo (IDEMPOTENCIA: misma clave dos veces cobra una sola vez)

<!-- PEGA AQUÍ LA CAPTURA -->

## Pruebas de ViewModels (14) · test/viewmodels_test.dart

Pruebas: catálogo con filtros y búsqueda, carrito que persiste y muestra errores, sesión con registro, login genérico y favoritos, y checkout por pasos con clave de idempotencia y protección contra doble toque.

### Éxito (todas en verde)

<!-- PEGA AQUÍ LA CAPTURA -->

### Fallo (filtra por categoría, texto y AR combinados)

<!-- PEGA AQUÍ LA CAPTURA -->

## Todas las pruebas en verde (60)

<!-- PEGA AQUÍ LA CAPTURA -->

## Evidencia de la aplicación

### Catálogo

<!-- PEGA AQUÍ LA CAPTURA -->

### Ver en tu espacio (modelo 3D / realidad aumentada)

<!-- PEGA AQUÍ LA CAPTURA -->

### Carrito con cupón y envío

<!-- PEGA AQUÍ LA CAPTURA -->

### Pago exitoso

<!-- PEGA AQUÍ LA CAPTURA -->
