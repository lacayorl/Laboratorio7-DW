Inversiones en Energía, S.A. de C.V. presentó un muy buen año 2017 con
utilidades por encima del millon, en lo que lleva del 2018 presentarón
una disminución del 25% en su margen operativo, por lo que se realizó un
análisis para ver que está pasando y que es lo mejor que puede hacer la
Empresa para mejorar sus utilidades y operaciones.

## Situación 2017 y 2018

    vetnas <- data %>% 
      mutate(Mes = month(Fecha)) %>% 
      group_by(Mes) %>% 
      summarise(Ventas = sum(factura),
                Costo = sum(Costo))

    ggventas <- ggplot(vetnas,aes(x = Mes, y = Ventas))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      ggtitle("Ventas")+
      labs(x = "2017", y = "Q")+
      theme_minimal()
    ggventas

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-2-1.png)

    # Estado de resultados
    Factura <- sum(data$factura)
    Costo <- sum(data$Costo)
    Utilidad_Bruta <- Factura - Costo
    Margen_Bruto <- Utilidad_Bruta/Factura

    Margen_2018 <- Margen_Bruto/1.25
    Utilidad_2018 <- Margen_2018*Factura

    Factura

    ## [1] 36688096

    Costo

    ## [1] 28174019

    Utilidad_Bruta

    ## [1] 8514077

    Margen_Bruto

    ## [1] 0.2320665

    Utilidad_2018

    ## [1] 6811262

    Margen_2018

    ## [1] 0.1856532

En el 2017 la empresa presentó: \* Ingresos: Q36,688,096 \* Costos:
Q28,174,019 \* Utilidad Bruta: Q8,514,077 \* Margen Bruto: 23.20%

En el 2018 con la baja del 25% presentó: \* Utilidad Bruta: Q6,811,262
\* Margen Bruto: 18.56%

## Análisis de Pareto

    tabla_postes <- table(data$ID)
    Pareto_factura <- pareto.chart(tabla_postes,
                                    main = "Pareto de Factura")

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-4-1.png)

El 80% de la facturación esta compuesta por al rededor de 10 - 12 Postes
y unicamente 5 postes conforman el 50% de la facturación.

Análizando más adelante los postes, notamos que la mayoria de esos
postes se ecuentra en los intervalos de distancia de 30-45 y 75-120, los
primeros presentan una de las tarifas más bajas y el segundo una de las
más altas, por lo que en este 2018 algunos clientes pudieron no estar de
acuerdo con la tarifa más alta afectando a la facuración de la empresa.

Se recomienda cuidar las tarifas de esos dos rangos de distancia para
los postes que se atienden con mayor freciencia.

## Recorridos

    distanciasefectivas <- data %>% 
      group_by(Distancia) %>% 
      summarise(Costo = sum(Costo),
                Ingreso = sum(Ingreso),
                Viajes = n(),
                Relacion = round(Ingreso/Viajes,2))

    ggdistanciasingreso <- ggplot(distanciasefectivas,aes(x = reorder(Distancia, Ingreso), y = Ingreso))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=Ingreso), vjust=0.5, color="black", size=4)+
      ggtitle("Ingreso por Distancia")+
      labs(x = "Distancia", y = "Ingreso")+
      coord_flip()+
      theme_minimal()
    ggdistanciasingreso

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-5-1.png)

    ggdistanciasef <- ggplot(distanciasefectivas,aes(x = reorder(Distancia, Relacion), y = Relacion))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=Relacion), vjust=0.5, color="black", size=4)+
      ggtitle("Relacion por Distancia")+
      labs(x = "Distancia", y = "Relacion")+
      coord_flip()+
      theme_minimal()
    ggdistanciasef

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-5-2.png)

Como se comentaba anteriormente se recomienda cuidar las tarifas de esos
dos intervalos de distancia, ya que son en donde mayor volumen de postes
tenemos en el año, esto se puede hacer análizando los costos directos y
variablesd e cada servicio y unidad como veremos a continuación.

## Unidades Eficientes

    Vehiculos_eficientes <- data %>% 
      group_by(Tipov) %>%
      summarise(CostoDirecto = sum(Cst_Directo),
                CostoFijo = sum(Cst_Fijo),
                Factura = sum(factura),
                Ingreso = sum(Ingreso))

    ggdirectcost <- ggplot(Vehiculos_eficientes,aes(x = reorder(Tipov, CostoDirecto), y = CostoDirecto))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=CostoDirecto), vjust=0.5, color="black", size=4)+
      ggtitle("Costo Directo por Unidad")+
      labs(x = "Unidad", y = "Cst. Directo")+
      coord_flip()+
      theme_minimal()
    ggdirectcost

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-6-1.png)

    ggfijocost <- ggplot(Vehiculos_eficientes,aes(x = reorder(Tipov, CostoFijo), y = CostoFijo))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=CostoFijo), vjust=0.5, color="black", size=4)+
      ggtitle("Costo Fijo por Unidad")+
      labs(x = "Unidad", y = "Cst. Fijo")+
      coord_flip()+
      theme_minimal()
    ggfijocost

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-6-2.png)

    ggingreso <- ggplot(Vehiculos_eficientes,aes(x = reorder(Tipov, Ingreso), y = Ingreso))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=Ingreso), vjust=0.5, color="black", size=4)+
      ggtitle("Ingreso por Unidad")+
      labs(x = "Unidad", y = "Ingreso")+
      coord_flip()+
      theme_minimal()
    ggingreso

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-6-3.png)

Como podemos ver el mayor ingreso es de servicios realizados con
pickups, por el volumen y el balance entre sus costos e ingresos es que
supero por el doble a los ingresos con camión, para el cual se debería
análizar una reducción en el uso, ya que los camiones presentan costos
muy altos en comparación al uso e ingresos que presentan.

## Actividades

    actividadesef <- data %>% 
      group_by(Cod) %>% 
      summarise(costo = sum(Costo),
                Ingreso = sum(Ingreso),
                Cantidad = n(),
                relacion = sum(Ingreso)/Cantidad)
    ggactingreso <- ggplot(actividadesef,aes(x = reorder(Cod, Ingreso), y = Ingreso))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      ggtitle("Ingreso por Actividad")+
      labs(x = "Actividad", y = "Ingreso")+
      coord_flip()+
      theme_minimal()
    ggactingreso

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-7-1.png)

    ggactrel <- ggplot(actividadesef,aes(x = reorder(Cod, relacion), y = relacion))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      ggtitle("Relacion por Actividad")+
      labs(x = "Actividad", y = "Relacion")+
      coord_flip()+
      theme_minimal()
    ggactrel

![](Reporte-Laboratorio-7_files/figure-markdown_strict/unnamed-chunk-7-2.png)

Las actividades más costosas son las de repuestos y las revisiones como
es de esperarse son las actividades que más ingresos nos generan, e
incluso se puede intentar generar una mayor ganancia reduciendo los
costos en los que s eincurre cuando no son algún tipo de reparación o de
repuesto, ya que se podría utilizar motos.

## Conclusión

La empresa prestan muy buena capacidad para crecer y aumentar sus
ingresos, las recomendaciones fueron tomadas con el fin de minimizar
costos, para así no perder clientes y tambien una recomendación para el
crecimeinto es colocar sus centros de distribución más pequeños a otras
locaciones.
