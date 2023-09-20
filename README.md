
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

```g = 60 + r - b ```


# Pintar círculos en las posiciones del píxel más claro y oscuro de la imagen 

Para buscar los pixeles más oscuros y claros primero convertir la imagen a escala gris.
Con esto buscamos el pixel con mayor valor para identificar el pixel mas claro y de menor valor para el mas oscuro.
Con estas dos posiciones dibujamos círculos alrededor de estos.

```
grey_frame = cv2.cvtColor(frame.copy(), cv2.COLOR_BGR2GRAY)

darkest_pixels = np.min(grey_frame)
pos = np.where(grey_frame == darkest_pixels)

cv2.circle(frame, (pos[1][0], pos[0][0]), 10, (0,0,255), -1)
```

Para identificar el cuadrado 8x8 más oscuro del imagen seguimos un procedimiento similar.
Iteramos por todos los cuadrados del imagen minimizando o maximizando la intensidad media de estas.

Una vez que se ha hallado el cuadrado mas oscuro y claro pintamos círculos sobre estos.

```
for y in range(0, grey_frame.shape[0] - 7):
    for x in range(0, grey_frame.shape[1] - 7):
        square = grey_frame[y:y+8, x:x+8]
        average_intensity = np.mean(square)

        if average_intensity < min_average:
            min_average = average_intensity
            min_pos = (x,y)
            darkest_square = square

        if average_intensity > max_average:
            max_average = average_intensity
            lightest_square = square
            max_pos = (x, y)
```


# Propuesta Pop Art

Para la propuesta pop art se convirtió la entrada de video en celdas.
Cada otra celda se invierte utilizando `cv2.flip()`. 
Con esto se consigue un efecto similar a la de un caleidoscopio.

