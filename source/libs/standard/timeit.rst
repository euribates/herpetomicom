timeit
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

El módulo ``timeit`` permite obtener una medida fiable de los los tiempos de ejecución
de un fragmento de código Python.

Vimos en su día que había dos formas de intercambiar
los valores de dos variables, usando una variable auxiliar
o usando el mecanismo de empaquetado de tuplas::

    >>> # Usando una variable auxiliar
    >>> a = 7; b = 12
    >>> temp = a; a = b; b = temp
    >>>
    >>> # Usando tuplas
    >>> a = 7; b = 12
    >>> a, b = b, a

Pero ¿cuál será más rápida? Usando el módulo ``timeit`` podemos
salir de dudas::

    >>> from timeit import Timer
    >>> Timer('t=a; a=b; b=t', 'a=7; b=12').timeit()
    0.0470120906829834
    >>> Timer('a,b = b,a', 'a=7; b=12').timeit()
    0.04259920120239258

El intercambio por medio de tuplas es -ligeramente- más rápido.
