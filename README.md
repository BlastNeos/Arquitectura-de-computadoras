# ALU en Verilog

## Descripción

Este repositorio contiene la implementación de una Unidad Aritmético-Lógica (ALU) de 32 bits en Verilog, junto con un módulo principal (`Top_ALU`) que conecta las entradas y salidas de la ALU. La ALU es capaz de realizar operaciones aritméticas y lógicas comunes basadas en un código de operación (opcode) de 6 bits.

## Características

La ALU implementada soporta las siguientes operaciones:

- Suma (ADD)
- Resta (SUB)
- Operación AND bit a bit
- Operación OR bit a bit
- Operación XOR bit a bit
- Shift aritmético a la derecha (SRA)
- Shift lógico a la derecha (SRL)
- Operación NOR bit a bit

Adicionalmente, la ALU incluye un indicador `zero` que se activa cuando el resultado de una operación es cero.

## Estructura del proyecto

1. **ALU.v**: Implementación de la ALU de 32 bits. El código está parametrizado, permitiendo ajustar el tamaño de las entradas. El módulo recibe dos entradas de datos (`A`, `B`), un `opcode` de 6 bits, y entrega un `result` y un indicador `zero`.

2. **Top_ALU.v**: Módulo superior que conecta la ALU y define las entradas/salidas para la interfaz con el resto del sistema.

## Entradas y salidas de la ALU

### Entradas:
- `A`: Primer operando.
- `B`: Segundo operando.
- `opcode`: Código de operación que define qué operación realizar.

### Salidas:
- `result`: Resultado de la operación seleccionada.
- `zero`: Bandera que indica si el resultado es 0.

## Simulación y pruebas

Para verificar el correcto funcionamiento de la ALU, se pueden crear archivos de prueba (testbenches) que suministren diversas combinaciones de entradas y opcode a la ALU, y verifiquen el valor de salida (`result`) y la señal de `zero`.

### Testbench

El testbench incluido genera entradas aleatorias y verifica automáticamente el resultado de las operaciones. Ejecuta varias iteraciones de pruebas, generando valores aleatorios para las entradas `A`, `B`, y `opcode`, y verifica que el resultado de la operación sea correcto.

### Descripción del Testbench

- **Entradas**: Se generan aleatoriamente valores para las entradas `A`, `B`, y `opcode`.
- **Verificación automática**: Después de cada operación, el testbench compara el resultado obtenido con el esperado y muestra un mensaje de error si los resultados no coinciden.
- **Repeticiones**: Se ejecutan varias iteraciones con valores aleatorios.
