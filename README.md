```
@startuml
left to right direction
actor Cliente as C
actor "Sistema Bancario" as SB

package "Cajero Automático" {
    usecase "Validarse en el sistema" as UC1
    usecase "Sacar dinero" as UC2
    usecase "Realizar transferencia" as UC3
    usecase "Realizar ingreso" as UC4
}

C --> UC1 : "Inicia sesión"
UC1 --> UC2 : "Tras validarse"
UC1 --> UC3 : "Tras validarse"
UC1 --> UC4 : "Tras validarse"
UC2 .> SB : "Verificar saldo y límite diario"
@enduml
```

**Descripción del Caso de Uso: "Sacar dinero"**

**1. Nombre del Caso de Uso:**  
Sacar dinero

**2. Actor(es) Principal(es):**  
Cliente

**3. Actor(es) Secundario(s):**  
Sistema Bancario

**4. Descripción:**  
Este caso de uso permite al Cliente retirar una cantidad específica de dinero de su cuenta a través del cajero automático, asegurando que la cantidad solicitada no exceda ni el saldo disponible ni el límite diario permitido.

**5. Precondiciones:**  
- El Cliente debe haberse validado en el sistema (caso de uso "Validarse en el sistema").
- El cajero automático debe estar operativo y contar con suficiente efectivo.

**6. Postcondiciones:**  
- Si la transacción es exitosa, el monto retirado se deduce del saldo de la cuenta del Cliente y se actualiza el límite diario de retiro.
- El Cliente recibe el monto solicitado en efectivo.

**7. Flujo Básico de Eventos:**
1. El Cliente selecciona la opción "Sacar dinero" en la interfaz del cajero automático.
2. El sistema solicita al Cliente que ingrese el monto deseado para retirar.
3. El Cliente ingresa la cantidad deseada.
4. El sistema verifica que la cantidad ingresada no exceda el saldo disponible en la cuenta del Cliente.
5. El sistema verifica que la cantidad ingresada no exceda el límite diario de retiro establecido para el Cliente.
6. Si ambas verificaciones son satisfactorias, el sistema dispensa el efectivo solicitado.
7. El sistema actualiza el saldo de la cuenta del Cliente y el límite diario de retiro.
8. El sistema ofrece la opción de imprimir un recibo de la transacción.
9. El Cliente finaliza la operación y retira su tarjeta.

**8. Flujos Alternativos:**

- **A1: Saldo insuficiente**
  1. En el paso 4 del Flujo Básico, si la cantidad ingresada excede el saldo disponible:
     - El sistema muestra un mensaje indicando que el saldo es insuficiente para completar la transacción.
     - El sistema solicita al Cliente que ingrese una nueva cantidad o cancele la operación.
     - El Cliente puede:
       - Ingresar una nueva cantidad (el flujo regresa al paso 3 del Flujo Básico).
       - Cancelar la operación, en cuyo caso el caso de uso finaliza.

- **A2: Límite diario excedido**
  1. En el paso 5 del Flujo Básico, si la cantidad ingresada excede el límite diario de retiro:
     - El sistema muestra un mensaje indicando que la cantidad excede el límite diario permitido.
     - El sistema solicita al Cliente que ingrese una nueva cantidad o cancele la operación.
     - El Cliente puede:
       - Ingresar una nueva cantidad (el flujo regresa al paso 3 del Flujo Básico).
       - Cancelar la operación, en cuyo caso el caso de uso finaliza.

**9. Requisitos Especiales:**
- El sistema debe procesar la transacción en un tiempo razonable (por ejemplo, menos de 30 segundos).
- La interfaz del cajero automático debe ser intuitiva y fácil de usar.

**10. Suposiciones:**
- Se asume que el Cliente conoce su saldo aproximado y su límite diario de retiro.
- Se asume que el cajero automático está conectado en tiempo real al Sistema Bancario para verificar saldos y límites.

**11. Puntos de Extensión:**
- Este caso de uso puede extenderse para incluir funcionalidades como:
  - Selección de denominaciones específicas de billetes.
  - Opción de solicitar un recibo electrónico en lugar de uno impreso.

**Importancia de los Diagramas de Casos de Uso**

Los diagramas de casos de uso son herramientas fundamentales en el análisis y diseño de sistemas por varias razones:

- **Claridad en los Requisitos:** Permiten capturar y comunicar de manera clara las funcionalidades que el sistema debe ofrecer desde la perspectiva del usuario, asegurando que todos los involucrados tengan una comprensión común de los requisitos.

- **Identificación de Actores y Sus Interacciones:** Ayudan a identificar quiénes interactuarán con el sistema (actores) y cómo lo harán, facilitando la comprensión de las relaciones entre los usuarios y el sistema.

- **Base para el Diseño y Desarrollo:** Proporcionan una base sólida para el diseño detallado del sistema, guiando a los desarrolladores en la implementación de las funcionalidades requeridas.

- **Gestión del Alcance:** Ayudan a definir los límites del sistema y a gestionar el alcance del proyecto, identificando qué funcionalidades están dentro y fuera del mismo.

- **Facilitación de Pruebas:** Sirven como referencia para el diseño de casos de prueba, asegurando que todas las funcionalidades descritas sean verificadas durante el proceso de pruebas.

En resumen, los diagramas de casos de uso aportan una visión clara y estructurada de cómo debe comportarse el sistema desde la perspectiva del usuario, lo que facilita la comunicación entre los diferentes actores involucrados en el desarrollo y asegura que el producto final cumpla con las expectativas y necesidades de los usuarios.
