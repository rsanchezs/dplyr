
# El paquete dplyr

El paquete __dplyr__ fue desarrollado por Hadley Wickham de RStudio y es un versión optimizada de su paquete __plyr__. El paquete __dplyr__ no proporciona ninguna nueva funcionalidad a __R__ per se, en el sentido que todo aquello que podemos hacer con __dplyr__ lo podríamos hacer con la sintaxis básica de __R__.

Una importante contribución del paquete __dplyr__ es que proporciona una "gramática" (particularmente verbos) para la manipulación y operaciones con data frames. Con esta gramática podemos comunicar mediante nuestro código que es lo que estamos haciendo en los data frames a otras personas (asumiendo que conozcan la gramática). Esto es muy útil, ya que proporciona una abstracción que anteriormente no existía. Por último, cabe destacar que las funciones del paquete __dplyr__ son muy rápidas, puesto que están implementadas con el lenguaje C++.

# La grámatica de dplyr

Algunas de los principales "verbos" del paquete __dplyr__ son:

+ ___select___: devuelve un conjunto de columnas
+ ___filter___: devuelve un conjunto de filas según una o varias condiciones lógicas
+ ___arrange___: reordena filas de un data frame
+ ___rename___: renombra variables en una data frame
+ ___mutate___: añade nuevas variables/columnas o transforma variables existentes
+ ___summarise/summarize___: genera resúmenes estadísticos de diferentes variables en el data frame, posiblemente con _strata_
+ ___%>%__ : el operador "pipe"  es usado para conectar múltiples acciones en una única "pipeline" (tubería)

# Argumentos comúnes en las funciones dplyr

Todas las funciones que discutiremos en este capítulo tienen en común una serie de argumentos. En particular,

1. El primer argumento es el data frame
2. Los otros argumentos describen que hacer con el data frame especificado en el primer argumento, podemos referirnos a las columnas en el data frame directamente sin utilizar el operador $, es decir sólo con el nombre de la columna/variable.
3. El valor de retorno es un nuevo data frame.
4.  Los data frames deben estar bien organizados/estructurados, es decir debe existir una observación por columna y, cada columna representar una variable, medida o característica de esa observación. Para ello, es muy útil es uso del paquete __tidy__. (lo veremos en capítulos posteriores).

# Instalación del paquete __dplyr__

Podemos instalar el paquete desde CRAN o desde GitHub.

```
## Instalación desde CRAN
install.packages("dplyr")

```

```
## Instalación desde GitHub
library(devtools)
install_github("hadley/dplyr")

```
Después de la instalación es importante que lo carguemos en nuestra sesión __R__ :


```r
library(dplyr)
```


Es posible que cuando carguemos el paquete nos aparezcan una serie de _warnings_, esto es debido que el paquete tiene funciones con el mismo nombre que en otros paquetes. Por el momento haremos caso omiso  a estos avisos.

Recomendamos consultar la documentación de las funciones:


```r
?select
?filter
?arrange
?mutate
?summarise
?group_by
```











