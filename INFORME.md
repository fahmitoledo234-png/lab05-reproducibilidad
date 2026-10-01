# Taller Unidad 6 · Contenedores y reproducibilidad

**Estudiante:** Fahmit Toledo
**Repositorio:** https://github.com/fahmitoledo234-png/lab05-reproducibilidad

---

## Parte 1 · Reproducir

**Evidencia:** salida de `./reproducir.sh` y `docker images lab05-viajes`.

```
== Construcción de la imagen lab05-viajes:1.0 ==

== Corrida A ==
== Etapa 1. Generación de datos (50000 filas) ==
Filas generadas : 50000
Archivo         : datos/viajes.csv
SHA-256         : 5ddad64f85e081307de1dad5a52e10a40422c12749954716f607f3c6d15bc19e

== Etapa 2. Análisis y persistencia de salidas ==
      ciudad  n_viajes  distancia_media_km  duracion_media_min  tarifa_media_cop  tarifa_p50_cop
Barranquilla      6088                5.98               17.97          16419.30         14450.0
      Bogota     22462                5.99               18.00          16448.88         14339.0
 Bucaramanga      4055                5.94               17.79          16322.11         14270.0
        Cali      7445                5.90               17.70          16250.58         14180.0
    Medellin      9950                5.97               17.86          16396.02         14171.0

154b62824a5a7f02e37a5e7a0a93e46ddd0237f2d88a57a8048800650b15a59a  resumen_ciudad.parquet
0c598115bb5676dd920eb4ada9a1be22dc6509f79aad616d795a65e337bfbb4b  resumen_ciudad.csv
568842db5a3964bdf2714a947311d127a9e35722593c2f12cba9b2ced58e74b2  tarifa_media_ciudad.png

== Corrida B ==
== Etapa 1. Generación de datos (50000 filas) ==
Filas generadas : 50000
Archivo         : datos/viajes.csv
SHA-256         : 5ddad64f85e081307de1dad5a52e10a40422c12749954716f607f3c6d15bc19e

== Etapa 2. Análisis y persistencia de salidas ==
      ciudad  n_viajes  distancia_media_km  duracion_media_min  tarifa_media_cop  tarifa_p50_cop
Barranquilla      6088                5.98               17.97          16419.30         14450.0
      Bogota     22462                5.99               18.00          16448.88         14339.0
 Bucaramanga      4055                5.94               17.79          16322.11         14270.0
        Cali      7445                5.90               17.70          16250.58         14180.0
    Medellin      9950                5.97               17.86          16396.02         14171.0

154b62824a5a7f02e37a5e7a0a93e46ddd0237f2d88a57a8048800650b15a59a  resumen_ciudad.parquet
0c598115bb5676dd920eb4ada9a1be22dc6509f79aad616d795a65e337bfbb4b  resumen_ciudad.csv
568842db5a3964bdf2714a947311d127a9e35722593c2f12cba9b2ced58e74b2  tarifa_media_ciudad.png

== Verificación de reproducibilidad ==
IDENTICO  resumen_ciudad.csv
IDENTICO  resumen_ciudad.parquet
IDENTICO  tarifa_media_ciudad.png

Reproducción exacta: 3 de 3 salidas coinciden.
IMAGE              ID             DISK USAGE   CONTENT SIZE   EXTRA
lab05-viajes:1.0   1f893697f054        687MB          161MB        
IMAGE              ID             DISK USAGE   CONTENT SIZE   EXTRA
lab05-viajes:1.0   1f893697f054        687MB          161MB        
```
---

## Parte 2 · Modificar y versionar

**Cambios realizados:**
- Se agregó `tarifa_sd_cop=("tarifa_cop", "std")` en `src/analisis.py`.
- Se agregó `"Pereira"` con peso `0.05` en `src/generar_datos.py`.
- Se actualizó `reproducir.sh` para usar la imagen `lab05-viajes:1.1`.

**Evidencia:** (pegar aquí el contenido de `evidencia_parte2.txt`)]633;E;echo "";00aec9f1-9660-413a-a5aa-294b6fb49452]633;C
```
== Construcción de la imagen lab05-viajes:1.1 ==

== Corrida A ==
== Etapa 1. Generación de datos (50000 filas) ==
Filas generadas : 50000
Archivo         : datos/viajes.csv
SHA-256         : f3be1441539ca17baab5402f302485e799741ea4fd24960202317b4a98ce3efe

== Etapa 2. Análisis y persistencia de salidas ==
      ciudad  n_viajes  distancia_media_km  duracion_media_min  tarifa_media_cop  tarifa_p50_cop  tarifa_sd_cop
Barranquilla      5126                5.96               17.89          16367.81         14438.0        8867.54
      Bogota     22462                5.99               18.00          16448.88         14339.0        9188.16
 Bucaramanga      2485                5.96               17.90          16383.86         14252.0        9010.00
        Cali      7445                5.90               17.70          16250.58         14180.0        9101.52
    Medellin      9950                5.97               17.86          16396.02         14171.0        9218.13
     Pereira      2532                5.97               17.91          16402.67         14447.0        8934.61

1343a787d52fcff776f058ce3b7057e78eaf2d9ba1a931bd8e8f67847c01081f  resumen_ciudad.parquet
8160729ebe9c436dc295431cb93e1767ce3333521210ecac635c07efd52c5874  resumen_ciudad.csv
7a75390c4f5e44653226f7eea0c53b84238810163fa3c76420af63545870cab8  tarifa_media_ciudad.png

== Corrida B ==
== Etapa 1. Generación de datos (50000 filas) ==
Filas generadas : 50000
Archivo         : datos/viajes.csv
SHA-256         : f3be1441539ca17baab5402f302485e799741ea4fd24960202317b4a98ce3efe

== Etapa 2. Análisis y persistencia de salidas ==
      ciudad  n_viajes  distancia_media_km  duracion_media_min  tarifa_media_cop  tarifa_p50_cop  tarifa_sd_cop
Barranquilla      5126                5.96               17.89          16367.81         14438.0        8867.54
      Bogota     22462                5.99               18.00          16448.88         14339.0        9188.16
 Bucaramanga      2485                5.96               17.90          16383.86         14252.0        9010.00
        Cali      7445                5.90               17.70          16250.58         14180.0        9101.52
    Medellin      9950                5.97               17.86          16396.02         14171.0        9218.13
     Pereira      2532                5.97               17.91          16402.67         14447.0        8934.61

1343a787d52fcff776f058ce3b7057e78eaf2d9ba1a931bd8e8f67847c01081f  resumen_ciudad.parquet
8160729ebe9c436dc295431cb93e1767ce3333521210ecac635c07efd52c5874  resumen_ciudad.csv
7a75390c4f5e44653226f7eea0c53b84238810163fa3c76420af63545870cab8  tarifa_media_ciudad.png

== Verificación de reproducibilidad ==
IDENTICO  resumen_ciudad.csv
IDENTICO  resumen_ciudad.parquet
IDENTICO  tarifa_media_ciudad.png

Reproducción exacta: 3 de 3 salidas coinciden.
ciudad,n_viajes,distancia_media_km,duracion_media_min,tarifa_media_cop,tarifa_p50_cop,tarifa_sd_cop
Barranquilla,5126,5.96,17.89,16367.81,14438.0,8867.54
Bogota,22462,5.99,18.0,16448.88,14339.0,9188.16
Bucaramanga,2485,5.96,17.9,16383.86,14252.0,9010.0
Cali,7445,5.9,17.7,16250.58,14180.0,9101.52
Medellin,9950,5.97,17.86,16396.02,14171.0,9218.13
Pereira,2532,5.97,17.91,16402.67,14447.0,8934.61
ciudad,n_viajes,distancia_media_km,duracion_media_min,tarifa_media_cop,tarifa_p50_cop,tarifa_sd_cop
Barranquilla,5126,5.96,17.89,16367.81,14438.0,8867.54
Bogota,22462,5.99,18.0,16448.88,14339.0,9188.16
Bucaramanga,2485,5.96,17.9,16383.86,14252.0,9010.0
Cali,7445,5.9,17.7,16250.58,14180.0,9101.52
Medellin,9950,5.97,17.86,16396.02,14171.0,9218.13
Pereira,2532,5.97,17.91,16402.67,14447.0,8934.61
```
---

## Parte 3 · Romper y diagnosticar

### Experimento A · Cambiar la semilla

**Evidencia:**

```
DIFIERE   resumen_ciudad.csv
DIFIERE   resumen_ciudad.parquet
DIFIERE   tarifa_media_ciudad.png

Reproducción fallida: 0 de 3 salidas coinciden.
```

**Explicación:** Al cambiar la semilla de 20260917 a 20260918, el generador produce otra secuencia de números aleatorios. Los 50 000 viajes son distintos y por lo tanto las tres huellas (CSV, Parquet y PNG) cambian por completo. La semilla fija es lo que hace determinista la generación de datos.

### Experimento B · Quitar la versión fijada de numpy

**Evidencia:**

```
DIFIERE   resumen_ciudad.csv
DIFIERE   resumen_ciudad.parquet
DIFIERE   tarifa_media_ciudad.png

Reproducción fallida: 0 de 3 salidas coinciden.
```

**Explicación:** Al cambiar numpy==2.1.3 por numpy>=2.1, pip instala la versión más reciente disponible en el momento de construir. Hoy podría coincidir con 2.1.3 y las huellas salir idénticas, pero eso no está garantizado: en unos meses pip podría instalar 2.5 y las huellas diferirían. La versión fijada con == es lo que hace la reproducibilidad independiente del tiempo.
