# analisis-compras-hospital-publico-power-bi
## Introduccion
Se realiza un Analisis en power bi derivado de proyecto analisis de hospital publico, el cual previamente se extrajo de datasets de mercado publico por medio de Rstudio, se limpio y se crearon mediciones en google sheets y tableau. Este proyecto continua con una limpieza mas exaustiva de datos junto con normalizacion de datos y creacion de un modelo de datos que ayuda a crear visualizaciones, formar relaciones y crear tablas que organizen de fomra clara los datos, ademas de preparar el dataset para futuros analisis al incluir codigos de tipo de compra, con la intencion de escalarlo a licitaciones publicas u otros segun necesidad.



-- PODRIA SEPARAR LOS ANALISIS POR SECCIONES SEGUN MIS PANELES, POR LO QUE VOY A CREAR CATEGORIAS Y VOY A EMPEZAR A COMPARAR Y VER PATRONES, ME INTERESAN VARIAS COMPARATIVAS ENTRE ORDENES TOTALES EN EL AÑO, JUNTO CON PATRONES DE COMPRAS DE STOCK CRITICO EN EL AÑO, COMPRAS ALTERNATIVAS Y FALTA CENABAST, ESO PUEDE REVELAR SI ES QUE LO ESCLAREZCO BIEN, SI HAY UN PATRON EN LA REALIZACION DE LAS ORDENES DE COMPRA JUNTO CON LA DEMANDA Y FALTA DE STOCK, PUEDO JUSTIFICAR SI EL CUMULO DE ESTAS CATEGORIAS AFECTA DE GRAN MEDIDA A LAS ORDENES ANUALES
Recalcar que las unidades que estan ahi algunas son ampollas y otras son clasificadas como unidad y se cambiaron por ser mismo producto, tambien que se creo una columna de clasificacion de ordenes y se creo una de tipo de orden para identificar todas las de compra agil.
Aclarar que compra alternativa no es categoria sino condicion y que tambien existe COMPRA ALTERNATIVA FALTA CENABAST. Explicar por que compra alternativa, stock critico y falta cenabast son condiciones. (sirve para separar lo que en realidad quiero saber y buscar dentro de mis areas que yo mismo designe)--

Dentro del calculo del total de gasto en medicamento dentro de farmacia ambulatoria posee 3 ordenes con nombre de otras areas, COMPRA ALTERNATIVA y FALTA CENABAST, se consideran parte de farmacia ambulatoria si lo dice explicitamente el nombre:
<img width="1416" height="147" alt="image" src="https://github.com/user-attachments/assets/4800edd0-27ef-4986-9e2b-765804d943c5" />

## Farmacia Ambulatoria

Seegun lo comprendido del analisis, farmacia ambulatoria posee bastante prevalencia al juntarse las ordenes de estos 2 años y comparar la cantidad de ordenes con las otras areas, siendo frecuentemente el area con mas ordenes. Al observar esta frecuencia, llama la atencion que abril, junio, julio y septiembre juntan una gran cantidad de ordenes. Por lo que se puede suponer de esto, es de que farmacia ambulatoria tiende a realizar pedidos con mayor frecuencia en estos meses.
<img width="1447" height="336" alt="image" src="https://github.com/user-attachments/assets/f207c1fc-1427-43f2-a61a-6a7ac032107e" />

Segun la cantidad de ordenes realizadas en el periodo 2024-2025, se observa que el año 2025 el mes con la mayor cantidad de ordenes realizadas en el hospital es abril, liderando con 21 ordenes, 8 de las cuales son de farmacia ambulatoria y 7 provenientes de FALTA CENABAST, se nota que coincidentemente tambien es el mes con el gasto mas alto en medicamentos de estos 2 años, con $19.708.868.

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




