## Operaciones de entrada y salida

Son bien conocidos como aquellos en donde hay un intercambio de información entre el usuario ***(una persona)*** y la máquina. En específico, 
la entrada es aquella donde por medio del teclado se comunica con el código, y la salida, es el valor que arroja el código, generalmente
a través de la pantalla, ya sea dentro de una pestaña de cmd o equivalente.
Dentro del código esto se ve reflejado a través de ciertas funciones, ya sea las básicas como **“scanf”** que es el método por el cual el código 
pide información al usuario, y ***“printf”** la cual semana el valor arrojado por el código. Otras funciones compuestas como ***“fgets”*** que cumple la 
función de entrada, sirve para opciones específicas, en este caso, de leer la cadena de caracteres del mismo código. Dicha función va acompañada
de un ***“sscaf”***. El cual trabaja con un tipo de datos llamado ***“char”*** que cumple la función de tomarla como una línea de caracteres. 

~~~
#include <stdio.h>
#include <math.h>

char espacio[1000];
float CX1; /*coordenada 1 X*/ 
float CY1; /*coordenada 1 Y*/ 
float CX2; /*coordenada 2 X*/ 
float CY2; /*coordenada 2 Y*/ 
float M; /*pendiente*/

int main(void) 
{
  printf("este codigo te dirá la pendiente de una linea dado 2 puntos de coordenadas X,Y\n");

  printf("escriba la primera coordenada en formato X,Y\n");
                                        /*aquí podemos ver la ejemplificación de la funcion fgets                */
                                        /*que tiene el formato de caracter que es "espacio", el estilo de entrada*/
                                        /*que tengo asignado en formato "(numero real),(numero real)"            */
                                        /*y asignando un amperson para declarar a su vez como valor numerico real*/
 fgets(espacio,sizeof(espacio),stdin); 
  sscanf(espacio,"%f,%f",&CX1,&CY1);

  printf("escriba la segunda coordenada en formato X,Y\n");
  fgets(espacio,sizeof(espacio),stdin);
  sscanf(espacio,"%f,%f",&CX2,&CY2);

  M=(CY2-CY1)/(CX2-CX1);

printf("tu pendiente es %.2f",M);
}
~~~





## Pointers

Los pointers como tal, es la asignación en un espacio de almacenamiento especifico, la cual podrá contener un dato X, que dependiendo de la implementación 
podrá ser o no modificable, por ejemplo, si queremos que sea un dato numérico, le podremos asignar asterisco al principio de su nombre, seguido de la propiedad 
entre comillas que queremos que tome (como por ejemplo ***(int,int)*** que da a entender que recibe dos valores numéricos y devuelve 1(el ***int*** original) ).
Uno de sus principales usos es para para asignar un valor en un espacio de memoria, y acceder a esos datos y en consecuencia usarlos para hacer diferentes funciones 

~~~
#include <stdio.h>


void funcion(int (*p)(int,int)); /*aquí se observa el uso de la funcion del pointer,la cual lleva un asteristo y detras se indica el uso*/
int suma(int a, int b); /*aquí se declara su el nombre de la funcion a utilizar y sus componentes*/
int resta(int a, int b);

int main(void) 
{
  funcion(suma); /*para la funcion principal se hace el uso de la funcion(nombrada así en el primer void*)
  funcion(resta);
  return 0;
}

int suma(int a, int b) /*aquí se declara la funcion suma como tal y sus componentes*/
{
  return a+b; /*y aquí la orden que resivirán sus datos para la devolucion de la orden*/
}
int resta(int a, int b)
{
  return a-b;
}

void funcion(int (*p)(int,int)) /*volviendo a la funcion "funcion" se declara la accion a tomar*/
{                   /*ya que están declaradas anteriormente solo necesitamos añadir los valores*/
  int x;            /*para cambiar de paramentro editable, asignamos una variable*/
  x = p(1, 2);      /*que va a tomar el la direccion del pointer y por tanto los valores asignados*/
  printf("%d\n",x); /*y solo tendremos que pedirle que imprima los valores de las funciones dadas*/
}
~~~
el resultado de la funcion anterior nos da esto
~~~
3
-1
~~~
esto es así porque x tiene multiples funciones, una suma y una resta respectivamente, y entonces su importancia es que podemos tomar 
las mismas variables dentro del pointer porque en sí el pointer no es más que la zona donde se almacenan dichos datos
los cuales podemos acceder a ellos mediante funciones y manejar distintas operaciones de ellos.

ARGC= es referido a la cantidad de argumentos dentro de la línea de comando principal “main” y es definido como un parámetro de este.
Su naturaleza es de valor número entero

ARGV=es referido como el valor que tiene el argumento de una cadena (generalmente del pointer “char” o caracter). La cantidad mínima 
de su valer siempre es 1, debido a que como está en la cadena principal, el primer valor es referido al nombre de la aplicación.

Estas funciones son útiles al momento de ejecutarlos desde CMD o alguno similar, ya que al ejecutarlos y añadir argumentos  dentro de esa acción, 
dichos elementos pueden interactuar con el código y así facilitar el manejo de datos.


