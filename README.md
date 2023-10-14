video de youtube: https://www.youtube.com/watch?v=ngriOXezr3A


# CoinChange
En el interfaz se encuentra las siguientes funciones: 

1. Importar las dependencias:
   - Importa el hook `useState` de React, que se utilizará para gestionar el estado de la aplicación.
   - También importa un archivo de estilo CSS llamado "App.css".

2. Definición del componente "App":
   - Crea una función llamada "App" que representa el componente principal de la aplicación.

3. Definición de estados:
   - Se definen cinco estados utilizando el hook `useState` para gestionar el estado de la aplicación. Los estados son `coins`, `coinsText`, `amount`, `coinChange`, y `totalCoins`. Cada uno almacena diferentes tipos de datos relacionados con la aplicación.

4. `handleCoinsChange`:
   - Es una función que toma un valor como argumento.
   - Normaliza el valor eliminando caracteres no numéricos y dividiéndolo por comas.
   - Luego, crea un conjunto (`Set`) de los valores únicos en el arreglo normalizado.
   - Convierte el conjunto en un arreglo y lo almacena en el estado `coins`.

5. `handleSubmit`:
   - Es una función que se llama cuando se envía el formulario.
   - Realiza una solicitud POST a "http://localhost:3000/coinchange" con los datos `coins` y `amount` en formato JSON.
   - Si la respuesta es exitosa, convierte la respuesta JSON en un objeto y actualiza los estados `totalCoins` y `coinChange` con los datos de la respuesta.

6. Renderizado del componente:
   - Renderiza un formulario que permite al usuario ingresar un monto y una lista de monedas disponibles.
   - Cuando se envía el formulario, se llama a la función `handleSubmit`.
   - Dependiendo de los valores de `totalCoins` y `coinChange`, se muestra el resultado en el componente.

7. Condiciones de visualización:
   - Si `totalCoins` es igual a -1, se muestra un mensaje indicando que no se puede dar cambio con las monedas disponibles.
   - Si `coinChange` contiene elementos, se muestra la lista de monedas necesarias para dar cambio, junto con la cantidad total de monedas requeridas.
  
En el api tenemos:

1. *Declaración de la función coinChange*:
   - La función `coinChange` toma dos argumentos: `coins`, que es un arreglo de valores de monedas disponibles, y `amount`, que es la cantidad de dinero que se quiere cambiar.

2. *Inicialización de arreglos dp y choice*:
   - `dp` es un arreglo de longitud `amount + 1` inicializado con valores infinitos. Este arreglo se utilizará para almacenar la cantidad mínima de monedas necesarias para hacer cambios para cantidades desde 0 hasta `amount`.
   - `choice` es otro arreglo de la misma longitud que se utiliza para rastrear la elección de monedas que se hace para llegar a la cantidad mínima de monedas.

3. *Bucle Anidado para Calcular Cambio*:
   - Se utiliza un bucle `for...of` para iterar a través de las monedas disponibles en `coins`.
   - Luego, se utiliza un segundo bucle `for` para iterar a través de las cantidades desde `coin` hasta `amount`.
   - Se verifica si es posible reducir la cantidad de monedas necesarias para llegar a `j` utilizando la moneda actual. Si es así, se actualiza `dp[j]` con el nuevo valor mínimo y se registra la elección en `choice[j]`.

4. *Verificación de Cambio Imposible*:
   - Después del bucle, se verifica si `dp[amount]` sigue siendo igual a infinito. Si es así, significa que no se puede dar cambio con las monedas disponibles, y se devuelve un objeto con un resultado de -1 y un objeto `coinsUsed` vacío.

5. *Retroceso para Encontrar las Monedas Utilizadas*:
   - Si es posible dar cambio, se realiza un retroceso desde `amount` hasta 0 utilizando el arreglo `choice` para determinar qué monedas se usaron y cuántas de cada una.
   - Se almacena esta información en el objeto `coinsUsed`.

6. *Retorno del Resultado*:
   - Finalmente, se devuelve un objeto con dos propiedades: `result` contiene la cantidad mínima de monedas necesarias para dar cambio, y `coinsUsed` contiene un objeto que enumera las monedas utilizadas y su cantidad.

7. *Exportación de la Función*:
   - La función `coinChange` se exporta para que pueda ser utilizada en otros archivos de JavaScript mediante `module.exports`.
