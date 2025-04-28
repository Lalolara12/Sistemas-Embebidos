# Sistemas-Embebidos
## Justificacion del proyecto

El presente proyecto tiene como objetivo desarrollar una máquina dispensadora de dulces controlada por un microcontrolador PIC16F877A. 
La máquina permitirá a los usuarios seleccionar, comprar y pagar diferentes tipos de dulces de manera automatizada. 
Además, se busca incentivar la compra recurrente mediante la implementación de un sistema de recompensas, donde los usuarios que realicen cinco compras válidas consecutivas recibirán un descuento.

La construcción de este proyecto tiene varias justificaciones:

- Aplicar conocimientos prácticos en programación de microcontroladores.
  
- Integrar hardware y software en un sistema funcional.
  
- Diseñar una interfaz de usuario simple y eficiente utilizando una pantalla LCD y botones de navegación.
  
- Promover el uso de simuladores como Proteus para validar diseños antes de construir el montaje físico.
  
- Familiarizarse con el flujo completo de un proyecto embebido: diseño, simulación, codificación, compilación y carga en hardware real.

Este proyecto no solo demuestra habilidades técnicas, sino que también sirve como base para aplicaciones comerciales reales, donde los sistemas automatizados de ventas están cada vez más presentes.

### REQUISITOS POR MÓDULO/COMPONENTE

1. Microcontrolador PIC16F877A
- Gestionar la lógica de navegación del menú de dulces.
- Recibir señales de entrada de los botones.
- Controlar la salida de LEDs y pantalla LCD.
- Almacenar y procesar la información de las compras.

2. Pantalla LCD 16x2
- Mostrar el nombre del dulce actualmente seleccionado.
- Mostrar la cantidad seleccionada.
- Mostrar el resumen de la compra al final (cantidad, tipo de dulce, precio total).
- Mostrar mensajes especiales (por ejemplo, "Ganaste descuento").

3. Botones
- Botón "Subir": Avanzar al siguiente producto en el menú o aumentar cantidad.
- Botón "Bajar": Retroceder al producto anterior o disminuir cantidad.
- Botón "Seleccionar": Confirmar la selección actual o añadir otro producto.
- Botón "Pagar": Finalizar la compra y mostrar resumen.

4. LEDs
- Encender el LED correspondiente cuando se presiona un botón.
- Mantener los LEDs apagados si no hay interacción.

5. Software (PICC Compiler y Proteus)
- El software debe ser capaz de compilar el código C y generar un archivo .hex compatible con el PIC.
- Proteus debe permitir simular el circuito para detectar errores antes de realizar el montaje físico.

6. Fuente de alimentación
- Proporcionar 5V estables para alimentar el PIC, la pantalla LCD, los LEDs y los botones.


### Hardware:

Uso eficiente de los recursos del PIC16F877A:

GPIO para LCD, botones y LEDs.

Temporizadores para retardos y debouncing.

UART configurada para monitoreo externo (opcional).

Circuito electrónico robusto con:

Protección de componentes (resistencias limitadoras).

Señal de reloj estable (cristal 4MHz + capacitores).

### Software:

Código modular y documentado en C, con:

Librerías personalizadas para LCD y botones.

Validación de entradas (ej.: cantidades > 0).

Estructuras de datos para gestión de compras.

# Componentes utilizados

### 1.1 Microcontrolador (PIC16F877A)

PIC16F877A (U1) - Cerebro del sistema. Controla LCD, botones y LEDs. Ejecuta la lógica de dispensación. - Todos los componentes se conectan a sus puertos.

Cristal (X1) - Proporciona señal de reloj a 4 MHz para sincronización. - Conectado a OSC1 y OSC2 (pines 13 y 14).

Capacitores (C1, C2) - Estabilizan la oscilación del cristal (22 pF cada uno). - En paralelo al cristal.

LEDs (D1-D4) - Indicadores visuales (ej.: selección, pago, descuento). - Conectados a PORTB (pines 33-40) con resistencias.

Resistencias (R3-R8) - Limitadoras de corriente (330Ω) para proteger LEDs y botones. - En serie con LEDs y botones.

LCD (LCD1) - Muestra menús y mensajes al usuario (16x2 caracteres). - Datos: PORTD (pines 19-26); Control: PORTE (pines 8-9).

Botones (BTN1-BTN4) - Entradas de usuario (avanzar, retroceder, seleccionar, pagar). - Conectados a PORTC (pines 15-18) con pull-down.

 ## El porqué del uso de estos componentes:

El PIC16F877A es viable porque: Tiene suficientes pines I/O para todos los componentes. Su memoria (8KB Flash, 368B RAM) soporta la lógica del programa. Los periféricos usados (GPIO, temporizadores) son adecuados para el proyecto.

### 1.2 Implementación del Sistema Embebido
  Tarea específica:
    Controlar la máquina dispensadora mediante: Lectura de botones (PORTC). Salida a LCD (PORTD + PORTE) y LEDs (PORTB)

### 1.3 Manejo de Periféricos

Periféricos de uso en el Proyecto:

Detalle Técnico
LCD 16x2 - Muestra: "Bienvenido", menú de dulces, cantidad seleccionada, factura.

Librería personalizada con funciones para inicialización y escritura.

Botones - Navegación en menús y confirmación de compras.

Debouncing por software (retardo de 50ms).

LEDs - Feedback visual: - D1: Selección activa. - D2: Pago exitoso. - D3: Descuento aplicado.

Controlados por PORTB (ej.: PORTB = 0x01 enciende D1).

## 1.4 Desarrollo de Software
### Se encuentra en un archivo dentro del github

## 1.5 Diagramas de flujo del funcionamiento del software

![deepseek_mermaid_20250428_78dd67](https://github.com/user-attachments/assets/900e6c83-d3d3-4a7d-bccf-6ca02448503a)
![deepseek_mermaid_20250428_3d063b](https://github.com/user-attachments/assets/eb423cd4-eacc-406e-8830-c379c1db392c)

## 1.4 Requisitos de Comunicación y Control
### 3.1 Comunicación de Datos
Implementación UART (Serial) 
Para Monitoreo Externo La comunicación UART permite monitorear en tiempo real las transacciones de la máquina dispensadora desde una PC, facilitando: Registro de ventas (backup), Depuración durante desarrollo, Integración con sistemas externos


# Diagrama de proteus

![WhatsApp Image 2025-04-24 at 7 30 06 PM](https://github.com/user-attachments/assets/6cb9c0ff-1d99-4728-ad44-e3df836167b1)


# Conclusión Final del Proyecto: Máquina Dispensadora de Dulces con PIC16F877A
Este proyecto representó un éxito rotundo en el desarrollo de un sistema embebido completo, demostrando la viabilidad técnica y práctica de implementar una máquina dispensadora automatizada utilizando el microcontrolador PIC16F877A. A lo largo del proceso, no solo se cumplieron todos los objetivos iniciales, sino que se superaron las expectativas en términos de funcionalidad, robustez y potencial de escalamiento.

El sistema desarrollado integra perfectamente componentes hardware y software para ofrecer una solución funcional y eficiente. La interfaz de usuario, compuesta por una pantalla LCD de 16x2 caracteres, cuatro botones táctiles y LEDs indicadores, proporciona una experiencia intuitiva y amigable para el usuario final. La lógica de control implementada permite gestionar de manera efectiva el proceso completo de selección de productos, configuración de cantidades y procesamiento de pagos, incluyendo un innovador sistema de descuentos automatizado.

Desde la perspectiva técnica, el proyecto demostró el dominio en el manejo de las capacidades del PIC16F877A, aprovechando al máximo sus recursos. Se implementó con éxito el control de periféricos mediante los puertos GPIO, se optimizó el uso de la memoria disponible y se estableció una comunicación serial UART para monitoreo externo. La solución adoptada para el debouncing de botones y la gestión de retardos mediante temporizadores internos resultó particularmente efectiva, garantizando un funcionamiento estable y confiable.
