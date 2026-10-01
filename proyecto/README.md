# Proyecto: Desempleo por ciudad en Colombia

## Pregunta de análisis

¿Cómo evoluciona la tasa de desempleo en las principales ciudades de Colombia entre 2019 y 2024, y qué ciudades muestran mayor volatilidad?

## Fuente de datos

- **Enlace:** https://microdatos.dane.gov.co/ (Gran Encuesta Integrada de Hogares, GEIH)
- **Licencia:** Datos abiertos del DANE, uso libre con atribución.
- **Variables a usar:**
  - Ciudad (dominio geográfico)
  - Periodo (mes/año)
  - Población en edad de trabajar (PET)
  - Fuerza de trabajo (FT)
  - Desocupados (DS)
  - Factor de expansión (FEX)

## Herramientas previstas

- **pandas** para la limpieza inicial y el cálculo ponderado.
- **PySpark** para procesar el volumen completo de microdatos.
- **matplotlib** para las gráficas de tendencia por ciudad.

## Cómo reproducir

```bash
docker build --tag proyecto:0.1 .
docker run --rm --volume "$(pwd)/salidas:/app/salidas" proyecto:0.1
```

Los resultados se escriben en `salidas/` y quedan versionados con la huella SHA-256.