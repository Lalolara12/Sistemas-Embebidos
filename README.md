# Sistemas-Embebidos

1. Requisitos Técnicos
2.   1.1 Microcontrolador (PIC16F877A)
3.   Componentes usados:
4.   Componente
5.   Función en el Proyecto
Conexión con PIC16F877A
PIC16F877A (U1) - Cerebro del sistema. Controla LCD, botones y LEDs. Ejecuta la lógica de dispensación. - Todos los componentes se conectan a sus puertos.
Cristal (X1) - Proporciona señal de reloj a 4 MHz para sincronización. - Conectado a OSC1 y OSC2 (pines 13 y 14).
Capacitores (C1, C2) - Estabilizan la oscilación del cristal (22 pF cada uno). - En paralelo al cristal.
Potenciómetro (RV1) - Ajusta el contraste de la LCD (no requiere programación). - Conectado al pin VEE de la LCD.
LEDs (D1-D4) - Indicadores visuales (ej.: selección, pago, descuento). - Conectados a PORTB (pines 33-40) con resistencias.
Resistencias (R3-R8) - Limitadoras de corriente (330Ω) para proteger LEDs y botones. - En serie con LEDs y botones.
LCD (LCD1) - Muestra menús y mensajes al usuario (16x2 caracteres). - Datos: PORTD (pines 19-26); Control: PORTE (pines 8-9).
Botones (BTN1-BTN4) - Entradas de usuario (avanzar, retroceder, seleccionar, pagar). - Conectados a PORTC (pines 15-18) con pull-down.

El porqué del uso de estos componentes:
El PIC16F877A es viable porque: Tiene suficientes pines I/O para todos los componentes. Su memoria (8KB Flash, 368B RAM) soporta la lógica del programa. Los periféricos usados (GPIO, temporizadores) son adecuados para el proyecto.

1.2 Implementación del Sistema Embebido
  Tarea específica:
    Controlar la máquina dispensadora mediante:
    Lectura de botones (PORTC).
    Salida a LCD (PORTD + PORTE) y LEDs (PORTB)

1.3 Manejo de Periféricos
  Periféricos utilizados y su implementación:

Periférico
Uso en el Proyecto
Detalle Técnico
LCD 16x2 - Muestra: "Bienvenido", menú de dulces, cantidad seleccionada, factura.
Librería personalizada con funciones para inicialización y escritura.
Botones - Navegación en menús y confirmación de compras.
Debouncing por software (retardo de 50ms).
LEDs - Feedback visual: - D1: Selección activa. - D2: Pago exitoso. - D3: Descuento aplicado.
Controlados por PORTB (ej.: PORTB = 0x01 enciende D1).

