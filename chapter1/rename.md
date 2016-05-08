
# rename()

Renombrar una variable en un data frame es sorprendentemente en __R__ muy difícil de realizar. La función __rename()__ esta diseñada para hacer este proceso de una forma más fácil.  

Echemos un vistazo a los nombres de las variables en el data frame __storms__:


```r
> names(storms)
```

```
[1] "storm"    "wind"     "pressure" "date"    
```

Para cambiar los nombres de las variables en el data frame __storms__ a castellano, podriamos hacerlo de la forma siguiente:  


```r
> rename(storms, tormenta = storm, viento = wind, presion = pressure, fecha = date )
```

```
Source: local data frame [6 x 4]

  tormenta viento presion      fecha
     (chr)  (int)   (int)     (date)
1  Alberto    110    1007 2000-08-03
2     Alex     45    1009 1998-07-27
3  Allison     65    1005 1995-06-03
4      Ana     40    1013 1997-06-30
5   Arlene     50    1010 1999-06-11
6   Arthur     45    1010 1996-06-17
```


