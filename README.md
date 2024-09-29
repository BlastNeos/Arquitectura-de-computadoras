# Arquitectura-de-computadoras
Repositorio de arquitectura de computadoras - 2024 

Descripción
Este repositorio contiene la implementación de una Unidad Aritmético-Lógica (ALU) de 32 bits en Verilog, junto con un módulo principal (Top_ALU) que conecta las entradas y salidas de la ALU. La ALU es capaz de realizar operaciones aritméticas y lógicas comunes basadas en un código de operación (opcode) de 6 bits.

Características
La ALU implementada soporta las siguientes operaciones:

Estructura del proyecto
ALU.v: Implementación de la ALU de 32 bits. El código está parametrizado, permitiendo ajustar el tamaño de las entradas (N, por defecto 32 bits). El módulo recibe dos entradas de datos (A, B), un opcode de 6 bits, y entrega un result y un indicador zero.

Top_ALU.v: Módulo superior que conecta la ALU y define las entradas/salidas para la interfaz con el resto del sistema.

Entradas y salidas de la ALU
Entradas:
A [N-1:0]: Primer operando.
B [N-1:0]: Segundo operando.
opcode [5:0]: Código de operación que define qué operación realizar.
Salidas:
result [N-1:0]: Resultado de la operación seleccionada.
zero: Bandera que indica si el resultado es 0.
Operaciones soportadas
La ALU decodifica el opcode de la siguiente manera:

Opcode	Operación	Descripción
100000	ADD	A + B
100010	SUB	A - B
100100	AND	A & B
100101	OR	A | B
100110	XOR	A ^ B
000011	SRA	A >>> B
000010	SRL	A >> B
100111	NOR	~(A | B)
Si el opcode no coincide con ninguno de los anteriores, el resultado será 0 por defecto.

Simulación y pruebas
Para verificar el correcto funcionamiento de la ALU, se pueden crear archivos de prueba (testbenches) que suministren diversas combinaciones de entradas y opcode a la ALU, y verifiquen el valor de salida (result) y la señal de zero.

Testbench
El archivo ALU_tb.v proporciona un testbench para la ALU, que genera entradas aleatorias y verifica automáticamente el resultado de las operaciones. El testbench ejecuta 10 iteraciones de pruebas, donde genera valores aleatorios para las entradas A, B, y opcode, y verifica que el resultado de la operación sea correcto.

Descripción del Testbench
Entradas: Se generan aleatoriamente valores para las entradas A, B, y opcode.
Verificación automática: Después de cada operación, el testbench compara el resultado obtenido con el esperado y muestra un mensaje de error si los resultados no coinciden.
Repeticiones: El ciclo repeat (10) ejecuta 10 iteraciones con valores aleatorios.
Cómo ejecutar el Testbench
