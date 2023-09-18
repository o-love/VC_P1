
# Tablero de ajedrez

Para crear el tablero primero se crea una imagen de fondo negro sobre la cuál se dibujará las celdas blancas.

Para dibujar las celdas blancas tenemos en cuanta que un tablero tiene ocho filas y ocho columnas con cuatro celdas de cada color.
Con esta información iteramos por todas las filas y dentro de cada una iteración iteramos por las cuatro celdas blancas de esta fila.
Una vez llegado a la posición de una celda blanca la dibujamos utilizando como su longitud un octavo del tablero total.

# Imagen al estilo Mondrian

Utilizando la modificación de plano visto en el último tarea modificamos imágenes se va rellenando el imagen tal que represente al estilo Mondrian.

```
color_img[95:145, 0:50, 0] = 180
color_img[95:145, 0:50, 1] = 200
```

# Resolver con las funciones de dibujo de OpenCV.

Utilizando las funciones de dibujo OpenCV se va creando lineas, rectángulos, ellipses y círculos tal que se crea un cuadro estilo Mondrian.

```
cv2.ellipse(color_img, (35, 160), (20, 30), 0, 0, 360, (0,255,0), -1)
```

# Modificar alguno de los planos de la imagen.

Para esta práctica modifique el plano verde tal que muestre la diferencia entre el plano rojo y el plano azul.
Así aparece mas claro esas areas que tienen mas rojo que azul y mas oscuro aquellos que tienen mas azul que rojo.

