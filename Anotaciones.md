### Ejercicio Boletas De Loteria 🌟

```java
public static boolean comprobarNumeros(int x, int y, int n, int[][] numeros)
    {
        for(int i = 0;i <= y;i++)
        {
            if(numeros[x][i] == n)
                {
                    return true;
                }
        }
        return false;
    }

    public static int[][] loteria(int t1, int t2)
    {
        int [][] numeros = new int[t1][t2];
        for(int i = 0;i < t1;i++)
        {
            for (int j = 0;j < t2;j++)
            {
                if(i == 0 && j == 0)
                {
                    numeros[i][j] = (int)(Math.random()* 50)+1;
                }
                else
                {
                    boolean repetido = true;
                    while(repetido)
                    {
                        int numero = (int)(Math.random()* 50)+1;
                        repetido = comprobarNumeros(i,j,numero,numeros);
                        if(repetido == false)
                        {
                            numeros[i][j] = numero;
                        }
                    }
                }            
            }
        }
        return numeros;
    }
```
- 1. Dar formato correpondiente al lenguaje, los bloques en java no se trabajan con los corchetes abajo. Puedes usar tu propio estilo correspondiente a las reglas de estilo del lenguaje o usar las herramientas de auto formateo que trae cada IDE.

---
- 2. El nombre de las varibles debe ser lo mas claro posible lo mismo aplica para el nombre de los metodos, los cuales deben describir la accion realizada. No es malo usar nombres largos para las variables y los metodos con tal sean lo mas explicativas posibles.
---
- 3. Usar programacion modular,  prefireblemente cada metodo debe tener maximo 20 lineas de codigo, si un componente sobre pasa este limite, posiblemente debe refactorizarse en otra funcion.
Cada funcion debe obedecer a hacer solo lo que se le pide y nada mas, si crees que un elemento de la funcion no obedece a lo que se describe en su nombre, posiblemente deba refactorizarse.
---
- 4. Evitar el uso el if else, preferiblemente usar operaciones ternarias, o si es posible que le mismo valor de comparacion de el valor vedadero o falso.
---
- 5. Tener en cuenta siempre las excepciones con el bloque try catch.
---
- 6. Uso de cometarios, solo cuando lo veas necesario. El codigo debe explicarse por si solo, el cometario debe obedecer a la pregunta del ¿que hace ? y no el ¿como lo hace ? 
---
## Codigo de ejemplo 🐱

```java
    public static int obtenerNumeroAleatorio() {
        // Nota: Expresion para obtener un numero aleatorio en un rango de 1 a 50
        return (int) (Math.random() * 50) + 1;
    }

    public static boolean validarNumerosRepetidos(int[][] arrDeBoletos, int posicionDelBoleto, int posicionDelDigito,
            int numeroAleatorio) {
        boolean validoRepetido = false;
        for (int i = 0; i < posicionDelDigito; i++) {
            validoRepetido = arrDeBoletos[posicionDelBoleto][i] == numeroAleatorio;
            if (validoRepetido) break;
        }
        return validoRepetido;
    }

    public static int[][] crearBoletoDeLoteria(int cantidadDeBoletos, int cantidadDigitosDelBoleto) {
        int[][] arrDeBoletos = new int[cantidadDeBoletos][cantidadDigitosDelBoleto];
        for (int psBoleto = 0; psBoleto < cantidadDeBoletos; psBoleto++) {
            for (int psDigito = 0; psDigito < cantidadDigitosDelBoleto; psDigito++) {
                int numeroAleatorio = obtenerNumeroAleatorio();
                boolean esRepetido = validarNumerosRepetidos(arrDeBoletos, psBoleto, psDigito, numeroAleatorio);
                while (esRepetido) {
                    numeroAleatorio = obtenerNumeroAleatorio();
                    esRepetido = validarNumerosRepetidos(arrDeBoletos, psBoleto, psDigito, numeroAleatorio);
                }
                arrDeBoletos[psBoleto][psDigito] = numeroAleatorio;
            }
        }
        return arrDeBoletos;
    }
```
## Como yo lo hubiera resuelto 👀

```java
    public static void createTicket(int numberOfTick, int numberOfDgt) {
        Set<Integer> setOfTickets       = null;
        List<Set<Integer>> lstOfTickets = new ArrayList<>();

        for (int i = 0; i < numberOfTick; i++) {
            setOfTickets = new HashSet<>();
            while (setOfTickets.size() < numberOfDgt) {
                int randomNumber = (int) (1 + (Math.random() * 50));
                setOfTickets.add(randomNumber);
            }
            lstOfTickets.add(setOfTickets);
        }
        lstOfTickets.forEach(System.out::println);
    }
```
