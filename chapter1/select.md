
# select()

Para los ejemplos en este capítulo utilizaremos un conjunto de datos relacionados con los vuelos en el año 2013 en la ciudad de Chicago.


```r
> install.packages("nycflights13")
```

```
Installing package into 'C:/Users/Drube/Documents/R/win-library/3.2'
(as 'lib' is unspecified)
```

```
package 'nycflights13' successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Users\Drube\AppData\Local\Temp\Rtmpe0iD2t\downloaded_packages
```

Para importar el conjunto de datos del paquete __nycflights13__ en __R__:


```r
> library(nycflights13) ##Cargamos la libreria
> data(package = "nycflights13") ##Importamos los datos en R
```

Si queremos trabajar con un conjunto de datos del paquete tendremos que cargarlo en el entorno __R__. Por ejemplo, si queremos trabajar con el data frame __planes__:


```r
> data("planes")
```
A continuación podemos realizar un examen preliminar del data frame:


```r
> str(planes) ##Muestra la estrutura del data frame
```

```
Classes 'tbl_df', 'tbl' and 'data.frame':	3322 obs. of  9 variables:
 $ tailnum     : chr  "N10156" "N102UW" "N103US" "N104UW" ...
 $ year        : int  2004 1998 1999 1999 2002 1999 1999 1999 1999 1999 ...
 $ type        : chr  "Fixed wing multi engine" "Fixed wing multi engine" "Fixed wing multi engine" "Fixed wing multi engine" ...
 $ manufacturer: chr  "EMBRAER" "AIRBUS INDUSTRIE" "AIRBUS INDUSTRIE" "AIRBUS INDUSTRIE" ...
 $ model       : chr  "EMB-145XR" "A320-214" "A320-214" "A320-214" ...
 $ engines     : int  2 2 2 2 2 2 2 2 2 2 ...
 $ seats       : int  55 182 182 182 55 182 182 182 182 182 ...
 $ speed       : int  NA NA NA NA NA NA NA NA NA NA ...
 $ engine      : chr  "Turbo-fan" "Turbo-fan" "Turbo-fan" "Turbo-fan" ...
```

```r
> dim(planes) ## n x m
```

```
[1] 3322    9
```

```r
> names(planes) ##nombre de las variables
```

```
[1] "tailnum"      "year"         "type"         "manufacturer"
[5] "model"        "engines"      "seats"        "speed"       
[9] "engine"      
```

```r
> ?planes ##documentación del data frame
```

La función ___select()___ sirve para seleccionar una o varias columnas del data frame.


```r
> select(planes, tailnum, year,type)
```

```
Source: local data frame [3,322 x 3]

   tailnum  year                    type
     (chr) (int)                   (chr)
1   N10156  2004 Fixed wing multi engine
2   N102UW  1998 Fixed wing multi engine
3   N103US  1999 Fixed wing multi engine
4   N104UW  1999 Fixed wing multi engine
5   N10575  2002 Fixed wing multi engine
6   N105UW  1999 Fixed wing multi engine
7   N107US  1999 Fixed wing multi engine
8   N108UW  1999 Fixed wing multi engine
9   N109UW  1999 Fixed wing multi engine
10  N110UW  1999 Fixed wing multi engine
..     ...   ...                     ...
```

Podemos utilizar la notación __:__ para seleccionar un rango de columnas:


```r
> select(planes, tailnum:type)
```

```
Source: local data frame [3,322 x 3]

   tailnum  year                    type
     (chr) (int)                   (chr)
1   N10156  2004 Fixed wing multi engine
2   N102UW  1998 Fixed wing multi engine
3   N103US  1999 Fixed wing multi engine
4   N104UW  1999 Fixed wing multi engine
5   N10575  2002 Fixed wing multi engine
6   N105UW  1999 Fixed wing multi engine
7   N107US  1999 Fixed wing multi engine
8   N108UW  1999 Fixed wing multi engine
9   N109UW  1999 Fixed wing multi engine
10  N110UW  1999 Fixed wing multi engine
..     ...   ...                     ...
```
Podemos excluir una o varias columnas en nuestra selección del siguiente modo:


```r
> select(planes, -tailnum)
```

```
Source: local data frame [3,322 x 8]

    year                    type     manufacturer     model engines seats
   (int)                   (chr)            (chr)     (chr)   (int) (int)
1   2004 Fixed wing multi engine          EMBRAER EMB-145XR       2    55
2   1998 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
3   1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
4   1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
5   2002 Fixed wing multi engine          EMBRAER EMB-145LR       2    55
6   1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
7   1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
8   1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
9   1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
10  1999 Fixed wing multi engine AIRBUS INDUSTRIE  A320-214       2   182
..   ...                     ...              ...       ...     ...   ...
Variables not shown: speed (int), engine (chr)
```

```r
> select(planes, -(tailnum:type))
```

```
Source: local data frame [3,322 x 6]

       manufacturer     model engines seats speed    engine
              (chr)     (chr)   (int) (int) (int)     (chr)
1           EMBRAER EMB-145XR       2    55    NA Turbo-fan
2  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
3  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
4  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
5           EMBRAER EMB-145LR       2    55    NA Turbo-fan
6  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
7  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
8  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
9  AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
10 AIRBUS INDUSTRIE  A320-214       2   182    NA Turbo-fan
..              ...       ...     ...   ...   ...       ...
```

La función __select()__ nos permite seleccionar un conjunto de columnas/variables según un patrón con la siguiente sintaxis:


```r
> select(planes, starts_with("m"))
```

```
Source: local data frame [3,322 x 2]

       manufacturer     model
              (chr)     (chr)
1           EMBRAER EMB-145XR
2  AIRBUS INDUSTRIE  A320-214
3  AIRBUS INDUSTRIE  A320-214
4  AIRBUS INDUSTRIE  A320-214
5           EMBRAER EMB-145LR
6  AIRBUS INDUSTRIE  A320-214
7  AIRBUS INDUSTRIE  A320-214
8  AIRBUS INDUSTRIE  A320-214
9  AIRBUS INDUSTRIE  A320-214
10 AIRBUS INDUSTRIE  A320-214
..              ...       ...
```

```r
> select(planes, ends_with("e"))
```

```
Source: local data frame [3,322 x 2]

                      type    engine
                     (chr)     (chr)
1  Fixed wing multi engine Turbo-fan
2  Fixed wing multi engine Turbo-fan
3  Fixed wing multi engine Turbo-fan
4  Fixed wing multi engine Turbo-fan
5  Fixed wing multi engine Turbo-fan
6  Fixed wing multi engine Turbo-fan
7  Fixed wing multi engine Turbo-fan
8  Fixed wing multi engine Turbo-fan
9  Fixed wing multi engine Turbo-fan
10 Fixed wing multi engine Turbo-fan
..                     ...       ...
```

A continuación mostramos un conjunto de funciones para __select__ que nos serán muy útiles:


+ __-__ : Selecciona todas las variables excepto
+ __:__ : Selecciona un rango
+ __contains()__ : Selecciona variables cuyo nombre contiene la cadena de texto
+ __ends_with()__: Selecciona variables cuyo nombre termina con la cadena de caracteres
+ __everything()__ : Selecciona todas las columnas
+ __matches()__: Selecciona las variables cuyos nombres coinciden con una expresión regular
+ __num_range()__: Selecciona las variables por posición
+ __one_of()__: Selecciona variables cuyos nombres están en un grupo de nombres
+ __start_with()__: Selecciona variables cuyos nombres empiezan con la cadena de caracteres.


