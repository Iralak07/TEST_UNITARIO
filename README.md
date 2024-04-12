# Test en python 

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


#### Metodos utiles de unittest

El módulo unittest de Python proporciona varios métodos útiles que se utilizan comúnmente al escribir pruebas unitarias. Aquí hay una lista de algunos de los métodos más utilizados en unittest.TestCase, junto con su función y ejemplos:

Metodo: assertEqual()
Comprueba si a es igual a b.

    import unittest
    
    class TestAssertEqual(unittest.TestCase):
        def test_equal(self):
            self.assertEqual(2 + 2, 4)
            self.assertEqual("hello", "hello")
    
    if __name__ == '__main__':
        unittest.main()

Metodo: assertTrue(expr):
Función: Comprueba si la expresión expr es verdadera.

import unittest

    class TestAssertTrue(unittest.TestCase):
        def test_true(self):
            self.assertTrue(2 + 2 == 4)
            self.assertTrue(len([1, 2, 3]) == 3)
    
    if __name__ == '__main__':
        unittest.main()


Metodo: assertFalse(expr):
Función: Comprueba si la expresión expr es falsa.

    import unittest
    
    class TestAssertFalse(unittest.TestCase):
        def test_false(self):
            self.assertFalse(2 + 2 == 5)
            self.assertFalse(len([]) > 0)
    
    if __name__ == '__main__':
        unittest.main()

Metodo: assertRaises(exc, callable, *args, kwargs):
Función: Comprueba si callable(*args, **kwargs) levanta una excepción de tipo exc.
    

    import unittest
    
    def dividir(a, b):
        return a / b
    
    class TestAssertRaises(unittest.TestCase):
        def test_raises(self):
            self.assertRaises(ZeroDivisionError, dividir, 1, 0)
    
    if __name__ == '__main__':
        unittest.main()

Metodo: assertIn(a, b):
Función: Comprueba si a está en b.

    import unittest
    
    class TestAssertIn(unittest.TestCase):
        def test_in(self):
            self.assertIn(2, [1, 2, 3])
            self.assertIn('a', 'banana')
    
    if __name__ == '__main__':
        unittest.main()

Metodo: assertNotIn(a, b):
Función: Comprueba si a no está en b.
    
    import unittest
    
    class TestAssertNotIn(unittest.TestCase):
        def test_not_in(self):
            self.assertNotIn(4, [1, 2, 3])
            self.assertNotIn('x', 'banana')
    
    if __name__ == '__main__':
        unittest.main()


Algunas caracteristicas de unittest:

- accesorio de prueba: Un dispositivo de prueba representa la preparación necesaria para realizar uno o más pruebas y cualquier acción de limpieza asociada. Esto puede implicar, por ejemplo, crear bases de datos, directorios temporales o proxy o iniciar un servidor proceso.
- caso de prueba: Un caso de prueba es la unidad individual de prueba. Comprueba si hay un determinado respuesta a un conjunto particular de entradas. unittestproporciona una clase base, TestCase, que puede usarse para crear nuevos casos de prueba.


Algunas pautas importante para recordar: 

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

### Usando setUp y tearDown

Otra de las ventajas de usar unittest, es que nos ofrece la posibilidad de definir funciones comunes que son ejecutadas antes y después de cada test. Estos métodos son setUp() y tearDown().

    import unittest  # Importación del módulo unittest
    
    class MyTestCase1(unittest.TestCase):  # Definición de la clase de prueba MyTestCase1 que hereda de unittest.TestCase
    
        # Only use setUp() and tearDown() if necessary
        # Comentario sobre el uso de setUp() y tearDown() solamente si son necesarios
    
        def setUp(self):
            ...  # Código para ejecutar en preparación para las pruebas
            # Método setUp() para realizar configuraciones previas a las pruebas
    
        def tearDown(self):
            ...  # Código para ejecutar para limpiar después de las pruebas
            # Método tearDown() para realizar acciones de limpieza después de las pruebas
    
        def test_feature_one(self):
            # Test feature one.
            ...  # Código de prueba para la característica uno
            # Método de prueba para verificar una característica específica del código
    
        def test_feature_two(self):
            # Test feature two.
            ...  # Código de prueba para la característica dos
            # Método de prueba para verificar otra característica del código


### Organizando el código de prueba

- Componentes básicos de las pruebas unitarias: Se refiere a los elementos fundamentales que componen las pruebas unitarias. En este contexto, los casos de prueba son la piedra angular de las pruebas unitarias. Estos casos de prueba son escenarios específicos que se diseñan para verificar el comportamiento de una pequeña parte de código, como una función o un método de una clase.

- Casos de prueba representados por unittest.TestCase: En el módulo unittest de Python, los casos de prueba se representan mediante la clase TestCase. Cada instancia de TestCase es un caso de prueba individual que contiene métodos para configurar el entorno de prueba, ejecutar pruebas y realizar comprobaciones sobre los resultados esperados.

- Creación de casos de prueba propios: Para crear sus propios casos de prueba, debe escribir subclases de TestCase o usar FunctionTestCase. Esto significa que puede definir sus propias clases que hereden de TestCase y agregar métodos de prueba específicos para las partes de su código que desea probar. Alternativamente, puede utilizar FunctionTestCase para envolver funciones individuales como casos de prueba.


En el contexto de las pruebas unitarias, la subclase más básica de TestCase simplemente consiste en implementar un método de prueba. Estos métodos de prueba, identificados por su nombre que comienza con "test", están diseñados para ejecutar tareas específicas de prueba en el código que queremos evaluar. Cada uno de estos métodos de prueba se encarga de verificar un aspecto particular del comportamiento del código bajo prueba.

    import unittest
    
    class DefaultWidgetSizeTestCase(unittest.TestCase):
        def test_default_widget_size(self):
            widget = Widget('The widget')
            self.assertEqual(widget.size(), (50, 50))

Cuando escribimos pruebas, a menudo nos encontramos con que hay muchas configuraciones repetitivas que debemos hacer. Afortunadamente, podemos simplificar este proceso mediante el uso de un método llamado setUp(). Este método es implementado por nosotros y el marco de pruebas automáticamente lo llamará antes de ejecutar cada prueba que escribamos. Esto nos permite realizar configuraciones comunes necesarias para nuestras pruebas de manera eficiente y sin repetición en cada método de prueba individual.

    import unittest
    
    class WidgetTestCase(unittest.TestCase):
    
        # Método setUp para configurar el entorno de prueba
        def setUp(self):
            # Creación de una instancia de Widget con el nombre 'The widget'
            self.widget = Widget('The widget')
    
        # Primer método de prueba: Verifica el tamaño predeterminado del widget
        def test_default_widget_size(self):
            # Comprobación de que el tamaño del widget es (50,50) por defecto
            self.assertEqual(self.widget.size(), (50,50),
                             'incorrect default size')
    
        # Segundo método de prueba: Verifica la capacidad de redimensionar el widget
        def test_widget_resize(self):
            # Redimensionamiento del widget a (100,150)
            self.widget.resize(100,150)
            # Comprobación de que el tamaño del widget es (100,150) después de la redimensión
            self.assertEqual(self.widget.size(), (100,150),
                             'wrong size after resize') # en caso de que falle el test envia un mensaje de error!




