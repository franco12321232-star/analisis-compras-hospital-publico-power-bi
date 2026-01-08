 # analisis-compras-hospital-publico-power-bi
## Introduccion
Se realiza un Analisis en power bi derivado de proyecto analisis de hospital publico, el cual previamente se extrajo de datasets de mercado publico por medio de Rstudio, se limpio y se crearon mediciones en google sheets y tableau. Este proyecto continua con una limpieza mas exhaustiva de datos junto con normalizacion y creacion de un modelo de datos que ayuda a crear visualizaciones, formar relaciones y crear tablas que organizen de fomra clara las observaciones, ademas de preparar el dataset para futuros analisis al incluir codigos de tipo de compra, con la intencion de escalarlo a licitaciones publicas u otros segun necesidad.

## Añcamce
Se utiliza un dataset parcialmente limpio que contiene observaciones de 2 años(2024-2025) de actos de ordenes de compra por parte del hospital Dr.Lautaro Navarro.
No es posible estimar tiempo de recepcion de los medicamentos con los datos proporcionados en el dataset, en las descripciones solo se comentan estimados por parte de los proveedores y no es un dato confiable, ademas de no haber una fecha explicita que refiera recepcion. Solo existen fechas de emision de ordenes de compra y fechas de emision de cotizaciones; tambien se despreciara las cotizaciones y solo se consideraran datos del acto de orden de compra.

## Limpieza y normalizacion de datos 
Se crea una clasificacion por palabras clave(FARMACIA AMBULATORIA, FALTA CENABAST, FARMACIA DOSIS UNITARIA, COMITÉ FARMACIA, NO CLASIFICADO, ETC), para explorar en detalle como se elaboro el codigo consultar **codigo clasifiacion area.txt**

Es muy posible que FARMACIA DU pueda significar DOSIS UNITARIA, se procede a normalizar en la tabla, conservando la columna original para futuras referencias
<img width="1178" height="208" alt="image" src="https://github.com/user-attachments/assets/aaab9fb3-2e59-4aa7-b4e3-b15b3ccedb83" />

Dentro del calculo del total de gasto en medicamento dentro de farmacia ambulatoria posee 3 ordenes con nombre de otras areas, COMPRA ALTERNATIVA y FALTA CENABAST, se consideran parte de farmacia ambulatoria si lo dice explicitamente el nombre:

<img width="1416" height="147" alt="image" src="https://github.com/user-attachments/assets/4800edd0-27ef-4986-9e2b-765804d943c5" />

## Creacion del modelo de datos
Se procede a crear tablas a partir de documento excel **consolidar_para _csv_2024-2025**, se limpian datos nulos (sin valores) y se realizn las limpiezas mencionadas en la categoria *Limpieza y normalizacion de datos*

<img width="1919" height="1076" alt="image" src="https://github.com/user-attachments/assets/7d04e3dc-72bc-49d8-b943-d3ce69815189" />

se crea la tabla normalizado para poder crear columnas que normalizen, corrijan errores en textos, se creen codigos para poder formar las tablas necesarias para crear el modelo de datos y asi poder integrar time intelligence para realizar analisis en el periodo a estudiar.

<img width="1514" height="674" alt="image" src="https://github.com/user-attachments/assets/c7baaced-491f-4be6-a1be-7afeb1e55851" />
<img width="723" height="685" alt="image" src="https://github.com/user-attachments/assets/9df00420-bb0e-4cbd-8b15-e39254c248cf" />

Se crean columnas con valores booleanos representados como "SI" o "NO", con el objetivo de clasificar las ordenes de area por estado de compra alternativa, falta cenabast o stock critico. Es de necesidad aclarar que falta cenabast es tanto un atributo de un area como tambien un area, la forma en que se diferenció es por la clasificacion de las areas como se habia mencionado anteriormente, el orden en que se realizó la clasificacion es crucial por el hecho de que un valor como FALTA CENABAST FARMACIA AMBULATORIA es clasificado como FARMACIA AMBULATORIA por la razon de que el comando que lo clasifica como tal está primero en la lista de ejecucion, por lo que todos los que incluyan esa combinacion van a ser considerados FARMACIA AMBULATORIA, todos los que digan FALTA CENABAST sin ningun otro nombre seran considerados como tal, sucediendo lo mismo con stock critico y compra alternativa.

<img width="636" height="715" alt="image" src="https://github.com/user-attachments/assets/46caf5c7-8d93-42cc-b918-2b9f0cee9863" />

Como se vio anteriormente, se crearon tablas que resumen y mantienen codigos y productos unicos, lo que facilita el orden, limpieza, llamada de datos y la trazabilidad de los datos

<img width="349" height="278" alt="image" src="https://github.com/user-attachments/assets/bc2473be-340e-4322-8429-af6a375a622c" />

Luego de creada las tablas se crean las relaciones en estrella en torno a la tabla de hechos, la cual representa a todos los eventos de compra y contiene todos los montos y claves secundarias, esta posee una clave unica de compra para identificar los eventos de adquisicion. Se crea la tabla **tabla** que contiene todas las columnas que nos ayudaran a medir en el tiempo los datos que se van a analizar.

Una vez realizada las relaciones se procede a crear las visualizaciones y a proceder con un analisis mas profundo de los datos

<img width="1057" height="645" alt="image" src="https://github.com/user-attachments/assets/777d0665-504a-4470-8741-718f21e2be5d" />

## Farmacia Ambulatoria

### Vista general de los datos
En general se puede deducir que existe un crecimiento del gasto en las areas de FARMACIA AMBULATORIA y FALTA CENABAST, con variaciones de gasto comparada con el año pasado bastante notorias y un aumento en el % de participacion en el gasto total, ambos juntos representando al 48,72% del gasto total de estos 2 años.
Cabe recalcar que cenabast tiene un aumento fuerte del 200%(YoY), ademas de aumentar su % de participacion en el gasto total de un 4,40% a un 13,22%, siendo el aumento de un 8,82%.
Farmacia ambulatoria tiene un aumento del 74% (YoY) y un aumento en % de participacion en el gasto total de 11,32% a 19,77%, el aumento es de 8,5%

<img width="1326" height="330" alt="image" src="https://github.com/user-attachments/assets/8296e874-6095-4d5b-ae41-ea13b5854e32" />

Se busca la orden con mayor gasto con impuesto en farmacia ambulatoria:
<img width="685" height="447" alt="image" src="https://github.com/user-attachments/assets/e5473b22-1d1c-4531-9f00-38ef373ac7e5" />

Al buscar en la tabla con drilldown, aparecen todas las instancias de venta del mismo producto:

<img width="1255" height="210" alt="image" src="https://github.com/user-attachments/assets/f318d34c-9412-4c1a-b04e-b27547d1cbd8" />


Se realiza una metrica donde se busca las ordenes con mayor cantidad de productos que se adquieren, usando como condicion que sean arriba de 5000 unidades y que pertenezcan a farmacia ambulatoria, se debe dejar claro que las formas farmaceuticas no se definen y solo se considera la adquisicion de la unidad en si.

<img width="752" height="440" alt="image" src="https://github.com/user-attachments/assets/df606596-42ce-4fb0-aa1c-6125122dbd7b" />


Segun lo comprendido del analisis, farmacia ambulatoria es bastante prevalente en lo que respecta a la frecuencia de ordenes de compra, al observar los datos de estos 2 años y comparar la cantidad de ordenes con las otras areas, se comprueba que es el area que tiene mas ordenes en total, llegando a 70. Al observar esta frecuencia, llama la atencion que abril, junio, julio y septiembre juntan una gran cantidad de ordenes. Por lo que se puede suponer problemas de stock frecuente en estos periodos.

<img width="1447" height="336" alt="image" src="https://github.com/user-attachments/assets/f207c1fc-1427-43f2-a61a-6a7ac032107e" />

Segun la cantidad de ordenes realizadas en el periodo 2024-2025, se identifica el mes con la mayor cantidad de ordenes realizadas en el hospital de todo el periodo, siendo abril del 2025 liderando con 21 ordenes, 8 de las cuales son de farmacia ambulatoria y 7 provenientes de FALTA CENABAST, se nota que coincidentemente tambien es el mes con el gasto mas alto en medicamentos de estos 2 años, con $19.708.868.
### COMPARATIVA 2024-2025
Es importante entender que el aumento en las metricas de ordenes de farmacia y FALTA CENABAST incrementaron el año 2025, el mas notorio es FARMACIA AMBULATORIA con 27 ordenes el año 2024 a 43 ordenes el 2025, siendo un aumento del 59,2%(YoY).

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
Hay algo crucial que destacar, y es que el gasto de compra alternativa es bajo ($9.909.880)comparado con el año siguiente, que asciende a $23.210.177, lo cual indica un crecimiento de 134%(YoY) a partir del valor original. 
El analisis realizado indica una variedad de precios de ordenes mucho mayores dentro de FALTA CENABAST en el 2025 con un promedio de $1.110.390 a comparacion de farmacia ambulatoria con $828.473

<img width="929" height="503" alt="image" src="https://github.com/user-attachments/assets/a5a895a4-3001-4641-bcc9-a5d807d491ed" />
<img width="918" height="507" alt="image" src="https://github.com/user-attachments/assets/3c7d7f29-a94b-4db8-83d0-71eff27a546e" />

En 2024 la mayor cantidad en ordenes es FALTA CENABAST con 13 ordenes y con un gasto total de $4.420.553, siguiendo farmacia ambulatoria con 9 ordenes y $3.605.081. Estas areas equivalen al 80,9% del % de participacion total de gasto de compra alternativa.
Pasando al 2025 ocurre un cambio en el area con mas ordenes, dominando farmacia ambulatoria con 11 ordenes y un gasto de $10.483.591 es de destacar que el aumento del gasto del año pasado al 2025 es de 190%(YoY); y cambiando con FALTA CENABAST con 8 ordenes y un gasto de $8.883.124, significando un aumento del 100%(YoY). Segun el porcentaje que equivalen estas 2 areas, tienen % de participacion en el gasto total de compra alternativa de un 83,4%, significando que la proporcion que contribuye al valor aumentó en un 2,5%.

El mes con mayor costo del 2024, coincidentemente es el de mayor orden, el cual es agosto, la orden de mayor gasto en agosto es COMPRA ALTERNATIVA FALTA CENABAST JULIO / ATORVASTATINA 40 MG CM	con $664,734.

<img width="939" height="500" alt="image" src="https://github.com/user-attachments/assets/7356d8be-ec2b-431e-b0a2-6e3375cbc529" />
<img width="473" height="312" alt="image" src="https://github.com/user-attachments/assets/b9fe41c5-141e-49b9-b464-716174ee127b" />

Farmacia ambulatoria tiene su mes de mayor costo en mayo, pero el mes con mas ordenes es en noviembre y su orden de mayor gasto es COMPRA ALTERNATIVA FARMACIA AMBULATORIA JULIO / TIAMINA CLORHIDRATO 10 MG CM	$1,042,440
<img width="1189" height="625" alt="image" src="https://github.com/user-attachments/assets/b8264dd4-71a2-4434-867b-dc6cb9726efb" />
<img width="463" height="187" alt="image" src="https://github.com/user-attachments/assets/26d7ae7a-33f7-484e-839c-9780d77ede09" />

En el año 2025, farmacia ambulatoria tiene su mes de mas alta frecuencia en abril y julio, ambos con 2 ordenes al mes pero ocurriendo la mayor cantidad de gasto en julio, la orden de mayor gasto es COMPRA ALTERNATIVA FALTA CENABAST FARMACIA AMBULATORIA JUNIO / LEVETIRACETAM 1000 MG CM con	$2,145,641

<img width="1130" height="633" alt="image" src="https://github.com/user-attachments/assets/73afd23a-29a6-4b1e-82b4-d663720c6767" />
<img width="474" height="178" alt="image" src="https://github.com/user-attachments/assets/72ea7698-db02-4989-86d6-751f2d0a5ba0" />

El mes con mas gasto en FALTA CENABAST es en agosto y el que tiene mas ordenes es en abril. La orden de mayor coste es COMPRA ALTERNATIVA FALTA CENABAST MAYO Y JUNIO / LACTULOSA 65-66 1000 ML	$3,448,620	$3,448,620

<img width="1157" height="640" alt="image" src="https://github.com/user-attachments/assets/1430ee10-34e6-461b-8943-c18a132cea2a" />

<img width="586" height="191" alt="image" src="https://github.com/user-attachments/assets/ab0f7196-b516-4edb-ab66-9d3c9964188c" />

## CONCLUSION

Se desprende de esto que el 2025 se incurrio en gastos mayores en areas como FARMACIA AMBULATORIA, CENABAST y COMPRA ALTERNATIVA, mostrando aumentos en la cantidad de ordenes realizadas como en montos gastados de manera proporcional en forma general, demostrando una mayor dependencia de las compras agiles para suplir envios faltantes a farmacia, se hace notar que los periodos donde hay mas ordenes concentradas de farmacia ambulatoria son a mitades de año, e incluso el aumento de ordenes de forma anormal por parte de COMPRA ALTERNATIVA FALTA CENABAST el mes de agosto 2024 puede traducirse en quiebres fuertes que podria ser importante explorar por presencia de de otros periodos donde se repita el mismo patron, ademas de ahondar en proveedores que usualmente participan en suplir al hospital en caso de quiebres, con el proposito de reducir dependencia de un proveedor. Existe una presencia alta de ordenes CENABAST que mayormente se encuentran en abril, junio y agosto   lo que puede significar problemas en lo que respecta a prevision frente a la disponibilidad y rapidez de respuesta de parte de CENABAST en esos meses, por lo que puede ser que posiblemente existan problemas de logistica relacionados con CENABAST, y seria una opcion investigar con datasets de CENABAST para diagnosticar problemas en distribucion y tiempo de demora.

