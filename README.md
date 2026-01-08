 # analisis-compras-hospital-publico-power-bi
## Introduccion
Se realiza un Analisis en power bi derivado de proyecto analisis de hospital publico, el cual previamente se extrajo de datasets de mercado publico por medio de Rstudio, se limpio y se crearon mediciones en google sheets y tableau. Este proyecto continua con una limpieza mas exaustiva de datos junto con normalizacion de datos y creacion de un modelo de datos que ayuda a crear visualizaciones, formar relaciones y crear tablas que organizen de fomra clara los datos, ademas de preparar el dataset para futuros analisis al incluir codigos de tipo de compra, con la intencion de escalarlo a licitaciones publicas u otros segun necesidad.

Es muy posible que FARMACIA DU pueda significar DOSIS UNITARIA, se procede a normalizar en la tabla, conservando la columna original para futuras referencias

-- PODRIA SEPARAR LOS ANALISIS POR SECCIONES SEGUN MIS PANELES, POR LO QUE VOY A CREAR CATEGORIAS Y VOY A EMPEZAR A COMPARAR Y VER PATRONES, ME INTERESAN VARIAS COMPARATIVAS ENTRE ORDENES TOTALES EN EL AÑO, JUNTO CON PATRONES DE COMPRAS DE STOCK CRITICO EN EL AÑO, COMPRAS ALTERNATIVAS Y FALTA CENABAST, ESO PUEDE REVELAR SI ES QUE LO ESCLAREZCO BIEN, SI HAY UN PATRON EN LA REALIZACION DE LAS ORDENES DE COMPRA JUNTO CON LA DEMANDA Y FALTA DE STOCK, PUEDO JUSTIFICAR SI EL CUMULO DE ESTAS CATEGORIAS AFECTA DE GRAN MEDIDA A LAS ORDENES ANUALES
Recalcar que las unidades que estan ahi algunas son ampollas y otras son clasificadas como unidad y se cambiaron por ser mismo producto, tambien que se creo una columna de clasificacion de ordenes y se creo una de tipo de orden para identificar todas las de compra agil.
Aclarar que compra alternativa no es categoria sino condicion y que tambien existe COMPRA ALTERNATIVA FALTA CENABAST. Explicar por que compra alternativa, stock critico y falta cenabast son condiciones. (sirve para separar lo que en realidad quiero saber y buscar dentro de mis areas que yo mismo designe)--

Dentro del calculo del total de gasto en medicamento dentro de farmacia ambulatoria posee 3 ordenes con nombre de otras areas, COMPRA ALTERNATIVA y FALTA CENABAST, se consideran parte de farmacia ambulatoria si lo dice explicitamente el nombre:
<img width="1416" height="147" alt="image" src="https://github.com/user-attachments/assets/4800edd0-27ef-4986-9e2b-765804d943c5" />

## Farmacia Ambulatoria

Seegun lo comprendido del analisis, farmacia ambulatoria posee bastante prevalencia al juntarse las ordenes de estos 2 años y comparar la cantidad de ordenes con las otras areas, siendo frecuentemente el area con mas ordenes. Al observar esta frecuencia, llama la atencion que abril, junio, julio y septiembre juntan una gran cantidad de ordenes. Por lo que se puede suponer de esto, es de que farmacia ambulatoria tiende a realizar pedidos con mayor frecuencia en estos meses.
<img width="1447" height="336" alt="image" src="https://github.com/user-attachments/assets/f207c1fc-1427-43f2-a61a-6a7ac032107e" />

Segun la cantidad de ordenes realizadas en el periodo 2024-2025, se observa que el año 2025 el mes con la mayor cantidad de ordenes realizadas en el hospital es abril, liderando con 21 ordenes, 8 de las cuales son de farmacia ambulatoria y 7 provenientes de FALTA CENABAST, se nota que coincidentemente tambien es el mes con el gasto mas alto en medicamentos de estos 2 años, con $19.708.868.
### COMPARATIVA 2024-2025
Es importante entender que el aumento en las metricas de ordenes de farmacia y FALTA CENABAST incrementaron el año 2025, el mas notorio es FARMACIA AMBULATORIA con 27 ordenes el año 2024 a 43 ordenes el 2025, siendo un aumento del 59,2% de las ordenes comparadas al año pasado.

<img width="1249" height="627" alt="image" src="https://github.com/user-attachments/assets/e6edf708-23ec-4228-8fd3-3e886f1f94b4" />

Se ve que la cantidad de ordenes en el año 2024 son mucho menores a comparacion al año siguiente, siendo mucho mas frecuentes al tercer cuarto del año 2024, se nota que la frecuencia tiende a disminuir el primer cuarto y el ultimo cuarto

<img width="674" height="387" alt="image" src="https://github.com/user-attachments/assets/2aaf8596-a730-4229-9ad7-564d4022ad6f" />

Algo peculiar es que en el año 2024, existen periodos muertos donde no existen pedidos de farmacia ambulatoria, dentro del primer cuarto serian los meses de febrero, marzo y abril 
<img width="1462" height="324" alt="image" src="https://github.com/user-attachments/assets/3e58727a-8f55-4146-a8e5-1b0dd25d312e" />
Julio es el mes con mas gastos con $11.769.100, tambien el area de farmacia ambulatoria lidera en ordenes realizadas este mes, siendo 6.
<img width="1212" height="634" alt="image" src="https://github.com/user-attachments/assets/a8c9e5e5-8c09-4bc4-bddc-4a91402d7c41" />

la orden mas costosa es FARMACIA AMBULATORIA JULIO / BUDESONIDA FORMOTEROL FUMARATO 160/4,5 MCG	con	$1,940,831.
<img width="875" height="360" alt="image" src="https://github.com/user-attachments/assets/1609216f-4421-4861-a3be-8b2983d92c93" />

Si se compara con el monto gastado, el 2025 presenta un aumento general del gasto en medicamentos y que es mayormente proporcional a la cantidad de ordenes realizadas

<<img width="1351" height="395" alt="image" src="https://github.com/user-attachments/assets/5039ce5c-8227-46fe-9abd-5eed461725f1" />

En total el valor que la farmacia ambulatoria acumula es de $9.123.456 donde el producto con el valor mas alto pertenece a la orden URGENTE FARMACIA AMBULATORIA ABRIL / RH-DORNASA-ALFA SOL. INHALACION 2,5 MG 2,5 ML AMP con $4.355.400.

<img width="701" height="298" alt="image" src="https://github.com/user-attachments/assets/43ec5cd4-2f46-4903-8ccd-834d2d8271fa" />


## Compra Alternativa
La condicion compra alternativa puede existir junto al nombre del area de la orden(Ej:COMPRA ALTERNATIVA FARMACIA AMBULATORIA), por lo que el analisis es basado en todas las ordenes que tengan el atributo "compra alternativa".
Existe 48 ordenes que tienen esta clasificacion, en el año 2024 existen 26 ordenes realizadas y el 2025 llegan solamente a 22, lo cual no tiene una variacion significativa.
En total, FALTA CENABAST acumula 21 ordenes totales con esta caracteristica, seguido de farmacia ambulatoria con 20
<img width="1116" height="623" alt="image" src="https://github.com/user-attachments/assets/221108cd-c6a0-4223-9cf2-df6d115f3cf0" />

### COMPARATIVA 2024-2025
Hay algo crucial que destacar, y es que el gasto de compra alternativa es bajo ($9.909.880)comparado con el año siguiente, que asciende a $23.210.177, lo cual indica un crecimiento de 134% a partir del valor original

<img width="929" height="503" alt="image" src="https://github.com/user-attachments/assets/a5a895a4-3001-4641-bcc9-a5d807d491ed" />

<img width="918" height="507" alt="image" src="https://github.com/user-attachments/assets/3c7d7f29-a94b-4db8-83d0-71eff27a546e" />

En 2024 la mayor participacion en ordenes es por FALTA CENABAST con 13 ordenes y un gasto total de $4.420.553, siguiendo farmacia ambulatoria con 9 ordenes y $3.605.081. Estas areas equivalen al 80,9% del valor total de compra alternativa.
Pasando al 2025 ocurre un cambio en el area con mas ordenes, dominando farmacia ambulatoria con 11 ordenes y un gasto de $10.483.591 es de destacar que el aumento del gasto del año pasado al 2025 es de 190%; y cambiando con FALTA CENABAST con 8 ordenes y un gasto de $8.883.124, significando un aumento del 100%. Segun el porcentaje que equivalen estas 2 areas en el total de compra alternativa, tienen una proporcion de 83,4%, significando que la proporcion que contribuye al valor aumento en un 2,5%.

El mes con mayor costo del 2024, coincidentemente es el de mayor orden, el cual es agosto, la orden de mayor gasto en agosto es COMPRA ALTERNATIVA FALTA CENABAST JULIO / ATORVASTATINA 40 MG CM	con $664,734.

<img width="939" height="500" alt="image" src="https://github.com/user-attachments/assets/7356d8be-ec2b-431e-b0a2-6e3375cbc529" />

Farmacia ambulatoria tiene su mes de mayor costo en mayo, pero el mes con mas ordenes es en noviembre y su orden de mayor gasto es COMPRA ALTERNATIVA FARMACIA AMBULATORIA JULIO / TIAMINA CLORHIDRATO 10 MG CM	$1,042,440

<img width="1124" height="631" alt="image" src="https://github.com/user-attachments/assets/281f6875-57cf-4da6-a38e-eae1f54933ac" />

En el año 2025, farmacia ambulatoria tiene su mes de mas alta frecuencia en abril y julio, ambos con 2 ordenes al mes pero ocurriendo la mayor cantidad de gasto en julio, la orden de mayor gasto es COMPRA ALTERNATIVA FALTA CENABAST FARMACIA AMBULATORIA JUNIO / LEVETIRACETAM 1000 MG CM con	$2,145,641

<img width="474" height="178" alt="image" src="https://github.com/user-attachments/assets/72ea7698-db02-4989-86d6-751f2d0a5ba0" />



