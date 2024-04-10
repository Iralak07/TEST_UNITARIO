# test en python 

### Pruebas manuales y pruebas automatizadas

Las pruebas automatizadas son la ejecución del plan de pruebas (las partes de la aplicación que desea probar, el orden en el que desea probarlas y las respuestas esperadas) mediante un script en lugar de un humano. Python ya viene con un conjunto de herramientas y bibliotecas para ayudarte a crear pruebas automatizadas para tu aplicación

Las pruebas manuales son tests ejecutados manualmente por una persona, probando diferentes combinaciones y viendo que el comportamiento del código es el esperado. Sin duda los has realizado alguna vez.


### Pruebas automatizadas

Python nos ofrece herramientas que nos permiten escribir tests que son ejecutados automáticamente, y que si fallan darán un error, alertando al programador de que ha “roto” algo. Podemos hacer esto con assert, donde identificamos dos partes claramente:

- Por un lado tenemos la llamada a la función que queremos testear, que devuelve un resultado.
- Por otro lado tenemos el resultado esperado, que comparamos con el resultado devuelto por la función. Si no es igual, se lanza un error.

Supongamos que tenemos una función simple llamada sumar que toma dos números como entrada y devuelve su suma. Queremos escribir una prueba automatizada para esta funcion.

    def sumar(a, b):
      return a + b

Escribiríamos una prueba automatizada para esta función utilizando la declaración assert:

    def test_sumar():
      # Llamamos a la función sumar con dos números y comprobamos si el resultado es el esperado.
      resultado = sumar(3, 5)
      assert resultado == 8, "La suma de 3 y 5 debería ser 8"
  
      # Probamos con otro par de números
      resultado = sumar(-1, 1)
      assert resultado == 0, "La suma de -1 y 1 debería ser 0"
  
      # Probamos con números decimales
      resultado = sumar(2.5, 3.5)
      assert resultado == 6.0, "La suma de 2.5 y 3.5 debería ser 6.0"
  
      # Probamos con números negativos
      resultado = sumar(-10, -5)
      assert resultado == -15, "La suma de -10 y -5 debería ser -15"
  
      print("Todas las pruebas han pasado correctamente")
      
    test_sumar()

### Tests Unitarios 

Concepto:
Los test unitarios, también conocidos como pruebas unitarias, son un tipo de prueba en el desarrollo de software donde se prueban las unidades más pequeñas y aisladas de código, típicamente funciones, métodos o clases, de manera individual. El objetivo principal de las pruebas unitarias es asegurarse de que cada unidad de código funcione correctamente de forma independiente, según lo diseñado.

##### Ejemplos en Python:

Prueba de una función simple:  Supongamos que tenemos una función simple llamada doble que toma un número como entrada y devuelve su doble. Aquí está la función:

    def doble(numero):
        return numero * 2
    
Ahora, escribamos una prueba unitaria para esta función usando el módulo unittest de Python:

    import unittest
    
    def doble(numero):
        return numero * 2
    
    class TestDoble(unittest.TestCase):
        def test_doble(self):
            self.assertEqual(doble(2), 4)
            self.assertEqual(doble(5), 10)
            self.assertEqual(doble(0), 0)
    
    if __name__ == '__main__':
        unittest.main()

        
Prueba de un método de una clase: Supongamos que tenemos una clase llamada Calculadora con un método sumar que toma dos números como entrada y devuelve su suma. Aquí está la clase:

    class Calculadora:
        def sumar(self, a, b):
            return a + b
            
Ahora, escribamos una prueba unitaria para el método sumar usando unittest:

    import unittest
    from calculadora import Calculadora
    
    class TestCalculadora(unittest.TestCase):
        def test_sumar(self):
            calc = Calculadora()
            self.assertEqual(calc.sumar(3, 5), 8)
            self.assertEqual(calc.sumar(-1, 1), 0)
            self.assertEqual(calc.sumar(2.5, 3.5), 6.0)
    
    if __name__ == '__main__':
        unittest.main()

Si ejecutamos el código anterior, obtendremos el siguiente resultado. Esta es una de las ventajas de unittest, ya que nos muestra información sobre los tests ejecutados, el tiempo que ha tardado y los resultados. Por otro lado, usando -v podemos obtener más información sobre cada test ejecutado con su resultado individualmente. Si tenemos gran cantidad de tests suele ser recomendable usarla, ya que será más fácil localizar los tests que han fallado.

    $ python -m unittest -v tests

En cada test ejecutamos las comprobaciones necesarias, usando assertEqual en vez de assert, pero su comportamiento es totalmente análogo.







Algunas pautas para recordar: 
- Debe probar todos los aspectos de su propio código, pero no las bibliotecas o funcionalidades proporcionadas como parte de Python o Django.
- Una es nombrar el módulo de prueba comenzándolo con test_ y terminarlo con el nombre del módulo que se está probando.
- No se debe incluir una cadena de caracteres de documentación para el método.
- Se debe usar un comentario (como # Tests function returns only True or False) para proporcionar documentación para los métodos de prueba.
- Añada una prueba explícita para cualquier error descubierto para el código probado. Esto asegurará que el error no vuelva a aparecer si el código se cambia en el futuro.
- Asegúrese de limpiar después de sus pruebas (así como cerrar y eliminar todos los archivos temporales).
- Importe la menor cantidad de módulos posible y hágalo lo antes posible.
- Intente maximizar la reutilización del código.

#### Prueba de caja blanca

La prueba de caja blanca, también conocida como prueba de caja de cristal o prueba estructural, es un enfoque de prueba en el que los casos de prueba se diseñan en función del conocimiento interno de la lógica y estructura del código que se está probando. Esto implica examinar el código fuente y las estructuras de control de flujo para diseñar casos de prueba que cubran todas las rutas posibles a través del código.

#### Prueba de caja negra

La prueba de caja negra es una técnica de prueba de software en la que se evalúa el funcionamiento de un sistema o componente sin conocer su estructura interna o lógica. En lugar de ello, se prueban las entradas y salidas del sistema, así como su comportamiento esperado, con base en las especificaciones externas.




