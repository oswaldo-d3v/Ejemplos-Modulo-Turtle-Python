# Ejemplos de programas con modulo Turtle de Python 

Gráfica tortuga es un término usado en computación gráfica como  método para programar gráficos vectoriales usando un cursor relativo a  unas coordenadas cartesianas. Este archivo de código cuenta con varias funciones que generan varias figuras 8 en total, al iniciar la ejecución del archivo ``.py`` se solicitara que ingrese un numero, correspondiente a la figura que desea que se dibuje.

Figuras disponibles: Figura 1

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%201.PNG)

Figuras disponibles: Figura 2

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%202.PNG)

Figuras disponibles: Figura 3

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%203.PNG)

Figuras disponibles: Figura 4

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%204.PNG)

Figuras disponibles: Figura 5

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%205.PNG)

Figuras disponibles: Figura 6

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%206.PNG)

Figuras disponibles: Figura 7

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%207.PNG)

Figuras disponibles: Figura 8

![](https://github.com/oswaldo-d3v/Ejemplos-Modulo-Turtle-Python/blob/master/Figura%208.PNG)

**Código fuente del archivo:**

```Python
import turtle as t

t.setup(500, 500)

def dibujar_circulo(px, py, radio):
    t.penup()
    t.setposition(px, py)
    t.setheading(270)
    t.forward(radio)
    t.setheading(0)
    t.pendown()
    t.circle(radio)


def dibujar_figura(px, py, radio, n):
    gradros = 360 / n
    angulo_inicial = 0
    for figura in range(0, n):
        t.penup()
        t.setposition(px, py)
        t.setheading(angulo_inicial)
        t.forward(radio)
        t.pendown()
        for i in range(0, 4):
            t.setheading(t.heading() - 180)
            t.circle(radio, 90)
        angulo_inicial += gradros

def curvas_beziers(px, py, longitud, angulo_inicial, angulo):
    t.penup()
    t.setposition(px, py)
    t.setheading(angulo_inicial)
    t.pendown()
    t.forward(longitud)
    fina_x = t.pos()
    t.penup()
    t.setposition(px, py)
    t.setheading(angulo + angulo_inicial)
    t.pendown()
    t.forward(longitud)
    fina_y = t.pos()

    distancia = longitud / 10
    punto_de_partida_x = px
    punto_de_partida_y = py

    punto_de_llegada_x = fina_x[0]
    punto_de_llegada_y = fina_x[1]

    for i in range(0, 10):
        t.penup()
        t.setposition(punto_de_partida_x, punto_de_partida_y)
        t.setheading(angulo + angulo_inicial)
        t.forward(distancia)
        punto_de_partida_x, punto_de_partida_y = t.pos()
        t.pendown()
        t.goto(punto_de_llegada_x, punto_de_llegada_y)
        t.penup()
        t.setheading(angulo_inicial - 180)
        t.forward(distancia)
        punto_de_llegada_x, punto_de_llegada_y = t.pos()


def generar_figuras(px, py, longitud, n_cuervas, angulo_inicial):
    angulo = 360 / n_cuervas
    angulo_inicial = angulo_inicial
    for figura in range(0, n_cuervas):
        curvas_beziers(px, py, longitud, angulo_inicial, angulo)
        angulo_inicial += angulo


def figura_uno():
    dibujar_circulo(0, 0, 200)
    dibujar_figura(0, 0, 200, 25)

def figura_dos():
    curvas_beziers(-200, 0, 200, 0, 90)
    curvas_beziers(0, 200, 200, 180, 90)
    curvas_beziers(0, 200, 200, 270, 90)
    curvas_beziers(200, 0, 200, 90, 90)
    curvas_beziers(-200, 0, 200, 270, 90)
    curvas_beziers(0, -200, 200, 90, 90)
    curvas_beziers(0, -200, 200, 0, 90)
    curvas_beziers(200, 0, 200, 180, 90)

def figura_tres():
    curvas_beziers(-200, -200, 200, 0, 90)
    curvas_beziers(200, -200, 200, 90, 90)
    curvas_beziers(200, 200, 200, 180, 90)
    curvas_beziers(-200, 200, 200, -90, 90)

def figura_cuatro():
    curvas_beziers(-200, -100, 200, 0, 60)
    curvas_beziers(200, -100, 200, 120, 60)
    t.setposition(-200, -100)
    t.setheading(60)
    t.forward(400)
    cordenada_x, cordenada_y = t.pos()
    curvas_beziers(cordenada_x, cordenada_y, 200, 240, 60)

def figura_sinco():
    generar_figuras(0, 0, 200, 4, 0)
    generar_figuras(0, 0, 200, 4, 30)
    generar_figuras(0, 0, 200, 4, 60)

def iniciar():
    entrada = t.numinput('Selecciona una figura', 'Selecciona una figura 1... 8: ', 1, 1, 8)
    if entrada == 1:
        figura_uno()
    elif entrada == 2:
        figura_dos()
    elif entrada == 3:
        figura_tres()
    elif entrada == 4:
        figura_cuatro()
    elif entrada == 5:
        figura_sinco()
    elif entrada == 6:
        generar_figuras(0, 0, 200, 3, 30)
    elif entrada == 7:
        generar_figuras(0, 0, 200, 4, 0)
    elif entrada == 8:
        generar_figuras(0, 0, 200, 12, 0)

t.speed(150)
iniciar()

t.done()
t.byte()

```

