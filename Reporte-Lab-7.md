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
    ggventas2 <- ggplotly(ggventas)
    ggventas2

<div id="htmlwidget-e9c0f2f0cb2e8d943cd0" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e9c0f2f0cb2e8d943cd0">{"x":{"data":[{"orientation":"v","width":[0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5],"base":[0,0,0,0,0,0,0,0,0,0,0,0],"x":[1,2,3,4,5,6,7,8,9,10,11,12],"y":[3093370.98,2766568.99,3139264.25,3007125.67,3113697.82,2992436.49,3135909.11,3118555.04,3040445.51,3163691.25,3014113.74,3102917.46],"text":["Mes:  1<br />Ventas: 3093371","Mes:  2<br />Ventas: 2766569","Mes:  3<br />Ventas: 3139264","Mes:  4<br />Ventas: 3007126","Mes:  5<br />Ventas: 3113698","Mes:  6<br />Ventas: 2992436","Mes:  7<br />Ventas: 3135909","Mes:  8<br />Ventas: 3118555","Mes:  9<br />Ventas: 3040446","Mes: 10<br />Ventas: 3163691","Mes: 11<br />Ventas: 3014114","Mes: 12<br />Ventas: 3102917"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":54.7945205479452},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Ventas","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.175,12.825],"tickmode":"array","ticktext":["2.5","5.0","7.5","10.0","12.5"],"tickvals":[2.5,5,7.5,10,12.5],"categoryorder":"array","categoryarray":["2.5","5.0","7.5","10.0","12.5"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"2017","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-158184.5625,3321875.8125],"tickmode":"array","ticktext":["0e+00","1e+06","2e+06","3e+06"],"tickvals":[0,1000000,2000000,3000000],"categoryorder":"array","categoryarray":["0e+00","1e+06","2e+06","3e+06"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Q","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c30427c4096":{"x":{},"y":{},"type":"bar"}},"cur_data":"4c30427c4096","visdat":{"4c30427c4096":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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

![](Reporte-Lab-7_files/figure-markdown_strict/unnamed-chunk-4-1.png)

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
    ggdistanciasingreso2 <- ggplotly(ggdistanciasingreso)
    ggdistanciasingreso2

<div id="htmlwidget-5b6783624d5861909226" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-5b6783624d5861909226">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5,0.5,0.5],"base":[0,0,0,0,0],"x":[979332,1641827,1076186,1210636,3606096],"y":[1,4,2,3,5],"text":["reorder(Distancia, Ingreso): 120-<br />Ingreso:  979332","reorder(Distancia, Ingreso): 30-45<br />Ingreso: 1641827","reorder(Distancia, Ingreso): 45-75<br />Ingreso: 1076186","reorder(Distancia, Ingreso): 5-30<br />Ingreso: 1210636","reorder(Distancia, Ingreso): 75-120<br />Ingreso: 3606096"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[979332,1641827,1076186,1210636,3606096],"y":[1,4,2,3,5],"text":[979332,1641827,1076186,1210636,3606096],"hovertext":["reorder(Distancia, Ingreso): 120-<br />Ingreso:  979332<br />Ingreso:  979332","reorder(Distancia, Ingreso): 30-45<br />Ingreso: 1641827<br />Ingreso: 1641827","reorder(Distancia, Ingreso): 45-75<br />Ingreso: 1076186<br />Ingreso: 1076186","reorder(Distancia, Ingreso): 5-30<br />Ingreso: 1210636<br />Ingreso: 1210636","reorder(Distancia, Ingreso): 75-120<br />Ingreso: 3606096<br />Ingreso: 3606096"],"textfont":{"size":15.1181102362205,"color":"rgba(0,0,0,1)"},"type":"scatter","mode":"text","hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":60.6392694063927},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Ingreso por Distancia","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-180304.8,3786400.8],"tickmode":"array","ticktext":["0e+00","1e+06","2e+06","3e+06"],"tickvals":[0,1000000,2000000,3000000],"categoryorder":"array","categoryarray":["0e+00","1e+06","2e+06","3e+06"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Ingreso","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,5.6],"tickmode":"array","ticktext":["120-","45-75","5-30","30-45","75-120"],"tickvals":[1,2,3,4,5],"categoryorder":"array","categoryarray":["120-","45-75","5-30","30-45","75-120"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Distancia","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c3053265474":{"x":{},"y":{},"type":"bar"},"4c301f8461e":{"x":{},"y":{},"label":{}}},"cur_data":"4c3053265474","visdat":{"4c3053265474":["function (y) ","x"],"4c301f8461e":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

    ggdistanciasef <- ggplot(distanciasefectivas,aes(x = reorder(Distancia, Relacion), y = Relacion))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=Relacion), vjust=0.5, color="black", size=4)+
      ggtitle("Relacion por Distancia")+
      labs(x = "Distancia", y = "Relacion")+
      coord_flip()+
      theme_minimal()
    ggdistanciasef2 <- ggplotly(ggdistanciasef)
    ggdistanciasef2

<div id="htmlwidget-855d8f71c80d34aa33d7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-855d8f71c80d34aa33d7">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5,0.5,0.5],"base":[0,0,0,0,0],"x":[37.13,31.13,31.39,30.6,32.56],"y":[5,2,3,1,4],"text":["reorder(Distancia, Relacion): 120-<br />Relacion: 37.13","reorder(Distancia, Relacion): 30-45<br />Relacion: 31.13","reorder(Distancia, Relacion): 45-75<br />Relacion: 31.39","reorder(Distancia, Relacion): 5-30<br />Relacion: 30.60","reorder(Distancia, Relacion): 75-120<br />Relacion: 32.56"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[37.13,31.13,31.39,30.6,32.56],"y":[5,2,3,1,4],"text":[37.13,31.13,31.39,30.6,32.56],"hovertext":["reorder(Distancia, Relacion): 120-<br />Relacion: 37.13<br />Relacion: 37.13","reorder(Distancia, Relacion): 30-45<br />Relacion: 31.13<br />Relacion: 31.13","reorder(Distancia, Relacion): 45-75<br />Relacion: 31.39<br />Relacion: 31.39","reorder(Distancia, Relacion): 5-30<br />Relacion: 30.60<br />Relacion: 30.60","reorder(Distancia, Relacion): 75-120<br />Relacion: 32.56<br />Relacion: 32.56"],"textfont":{"size":15.1181102362205,"color":"rgba(0,0,0,1)"},"type":"scatter","mode":"text","hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":60.6392694063927},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Relacion por Distancia","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-1.8565,38.9865],"tickmode":"array","ticktext":["0","10","20","30"],"tickvals":[0,10,20,30],"categoryorder":"array","categoryarray":["0","10","20","30"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Relacion","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,5.6],"tickmode":"array","ticktext":["5-30","30-45","45-75","75-120","120-"],"tickvals":[1,2,3,4,5],"categoryorder":"array","categoryarray":["5-30","30-45","45-75","75-120","120-"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Distancia","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c3041eb38d3":{"x":{},"y":{},"type":"bar"},"4c3061136cce":{"x":{},"y":{},"label":{}}},"cur_data":"4c3041eb38d3","visdat":{"4c3041eb38d3":["function (y) ","x"],"4c3061136cce":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
    ggdirectcost2 <- ggplotly(ggdirectcost)    
    ggdirectcost2

<div id="htmlwidget-5b68f8dccb07d6c3a7d9" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-5b68f8dccb07d6c3a7d9">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5],"base":[0,0,0],"x":[5499059.54,12144675.48,249872.04],"y":[2,3,1],"text":["reorder(Tipov, CostoDirecto): Camion_5<br />CostoDirecto:  5499060","reorder(Tipov, CostoDirecto): Pickup<br />CostoDirecto: 12144675","reorder(Tipov, CostoDirecto): Moto<br />CostoDirecto:   249872"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[5499059.54,12144675.48,249872.04],"y":[2,3,1],"text":[5499059.54,12144675.48,249872.04],"hovertext":["reorder(Tipov, CostoDirecto): Camion_5<br />CostoDirecto:  5499060<br />CostoDirecto:  5499060","reorder(Tipov, CostoDirecto): Pickup<br />CostoDirecto: 12144675<br />CostoDirecto: 12144675","reorder(Tipov, CostoDirecto): Moto<br />CostoDirecto:   249872<br />CostoDirecto:   249872"],"textfont":{"size":15.1181102362205,"color":"rgba(0,0,0,1)"},"type":"scatter","mode":"text","hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":72.3287671232877},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Costo Directo por Unidad","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-607233.774,12751909.254],"tickmode":"array","ticktext":["0","2500000","5000000","7500000","10000000","12500000"],"tickvals":[0,2500000,5000000,7500000,10000000,12500000],"categoryorder":"array","categoryarray":["0","2500000","5000000","7500000","10000000","12500000"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Cst. Directo","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["Moto","Camion_5","Pickup"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["Moto","Camion_5","Pickup"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Unidad","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c3092d4dff":{"x":{},"y":{},"type":"bar"},"4c3060bf106e":{"x":{},"y":{},"label":{}}},"cur_data":"4c3092d4dff","visdat":{"4c3092d4dff":["function (y) ","x"],"4c3060bf106e":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

    ggfijocost <- ggplot(Vehiculos_eficientes,aes(x = reorder(Tipov, CostoFijo), y = CostoFijo))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=CostoFijo), vjust=0.5, color="black", size=4)+
      ggtitle("Costo Fijo por Unidad")+
      labs(x = "Unidad", y = "Cst. Fijo")+
      coord_flip()+
      theme_minimal()
    ggfijocost2 <- ggplotly(ggfijocost)
    ggfijocost2

<div id="htmlwidget-c98c0b2fe2f2f14093a8" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c98c0b2fe2f2f14093a8">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5],"base":[0,0,0],"x":[3159303.74,6977232.39,143875.87],"y":[2,3,1],"text":["reorder(Tipov, CostoFijo): Camion_5<br />CostoFijo: 3159303.7","reorder(Tipov, CostoFijo): Pickup<br />CostoFijo: 6977232.4","reorder(Tipov, CostoFijo): Moto<br />CostoFijo:  143875.9"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[3159303.74,6977232.39,143875.87],"y":[2,3,1],"text":[3159303.74,6977232.39,143875.87],"hovertext":["reorder(Tipov, CostoFijo): Camion_5<br />CostoFijo: 3159303.7<br />CostoFijo: 3159303.7","reorder(Tipov, CostoFijo): Pickup<br />CostoFijo: 6977232.4<br />CostoFijo: 6977232.4","reorder(Tipov, CostoFijo): Moto<br />CostoFijo:  143875.9<br />CostoFijo:  143875.9"],"textfont":{"size":15.1181102362205,"color":"rgba(0,0,0,1)"},"type":"scatter","mode":"text","hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":72.3287671232877},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Costo Fijo por Unidad","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-348861.6195,7326094.0095],"tickmode":"array","ticktext":["0e+00","2e+06","4e+06","6e+06"],"tickvals":[0,2000000,4000000,6000000],"categoryorder":"array","categoryarray":["0e+00","2e+06","4e+06","6e+06"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Cst. Fijo","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["Moto","Camion_5","Pickup"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["Moto","Camion_5","Pickup"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Unidad","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c3068725dbd":{"x":{},"y":{},"type":"bar"},"4c302c522cc9":{"x":{},"y":{},"label":{}}},"cur_data":"4c3068725dbd","visdat":{"4c3068725dbd":["function (y) ","x"],"4c302c522cc9":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

    ggingreso <- ggplot(Vehiculos_eficientes,aes(x = reorder(Tipov, Ingreso), y = Ingreso))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      geom_text(aes(label=Ingreso), vjust=0.5, color="black", size=4)+
      ggtitle("Ingreso por Unidad")+
      labs(x = "Unidad", y = "Ingreso")+
      coord_flip()+
      theme_minimal()
    ggingreso2 <- ggplotly(ggingreso)
    ggingreso2

<div id="htmlwidget-262bb120fb83a68072de" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-262bb120fb83a68072de">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5],"base":[0,0,0],"x":[2803617,5380176,330284],"y":[2,3,1],"text":["reorder(Tipov, Ingreso): Camion_5<br />Ingreso: 2803617","reorder(Tipov, Ingreso): Pickup<br />Ingreso: 5380176","reorder(Tipov, Ingreso): Moto<br />Ingreso:  330284"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[2803617,5380176,330284],"y":[2,3,1],"text":[2803617,5380176,330284],"hovertext":["reorder(Tipov, Ingreso): Camion_5<br />Ingreso: 2803617<br />Ingreso: 2803617","reorder(Tipov, Ingreso): Pickup<br />Ingreso: 5380176<br />Ingreso: 5380176","reorder(Tipov, Ingreso): Moto<br />Ingreso:  330284<br />Ingreso:  330284"],"textfont":{"size":15.1181102362205,"color":"rgba(0,0,0,1)"},"type":"scatter","mode":"text","hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":72.3287671232877},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Ingreso por Unidad","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-269008.8,5649184.8],"tickmode":"array","ticktext":["0e+00","2e+06","4e+06"],"tickvals":[0,2000000,4000000],"categoryorder":"array","categoryarray":["0e+00","2e+06","4e+06"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Ingreso","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["Moto","Camion_5","Pickup"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["Moto","Camion_5","Pickup"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Unidad","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c30220f57ea":{"x":{},"y":{},"type":"bar"},"4c3079d85e21":{"x":{},"y":{},"label":{}}},"cur_data":"4c30220f57ea","visdat":{"4c30220f57ea":["function (y) ","x"],"4c3079d85e21":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
    ggactingreso2 <- ggplotly(ggactingreso)
    ggactingreso2

<div id="htmlwidget-2847a27267246ff63786" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-2847a27267246ff63786">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5],"base":[0,0,0,0,0,0,0,0,0,0],"x":[1011009,854277,74874,259247,2652070,442789,1044181,1365161,68471,741998],"y":[7,6,2,3,10,4,8,9,1,5],"text":["reorder(Cod, Ingreso): CAMBIO_CORRECTIVO<br />Ingreso: 1011009","reorder(Cod, Ingreso): CAMBIO_FUSIBLE<br />Ingreso:  854277","reorder(Cod, Ingreso): CAMBIO_PUENTES<br />Ingreso:   74874","reorder(Cod, Ingreso): OTRO<br />Ingreso:  259247","reorder(Cod, Ingreso): REVISION<br />Ingreso: 2652070","reorder(Cod, Ingreso): REVISION_TRANSFORMADOR<br />Ingreso:  442789","reorder(Cod, Ingreso): VERIFICACION_INDICADORES<br />Ingreso: 1044181","reorder(Cod, Ingreso): VERIFICACION_MEDIDORES<br />Ingreso: 1365161","reorder(Cod, Ingreso): VISITA<br />Ingreso:   68471","reorder(Cod, Ingreso): VISITA_POR_CORRECCION<br />Ingreso:  741998"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":165.844748858448},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Ingreso por Actividad","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-132603.5,2784673.5],"tickmode":"array","ticktext":["0e+00","1e+06","2e+06"],"tickvals":[0,1000000,2000000],"categoryorder":"array","categoryarray":["0e+00","1e+06","2e+06"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Ingreso","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,10.6],"tickmode":"array","ticktext":["VISITA","CAMBIO_PUENTES","OTRO","REVISION_TRANSFORMADOR","VISITA_POR_CORRECCION","CAMBIO_FUSIBLE","CAMBIO_CORRECTIVO","VERIFICACION_INDICADORES","VERIFICACION_MEDIDORES","REVISION"],"tickvals":[1,2,3,4,5,6,7,8,9,10],"categoryorder":"array","categoryarray":["VISITA","CAMBIO_PUENTES","OTRO","REVISION_TRANSFORMADOR","VISITA_POR_CORRECCION","CAMBIO_FUSIBLE","CAMBIO_CORRECTIVO","VERIFICACION_INDICADORES","VERIFICACION_MEDIDORES","REVISION"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Actividad","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c305dd553b":{"x":{},"y":{},"type":"bar"}},"cur_data":"4c305dd553b","visdat":{"4c305dd553b":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

    ggactrel <- ggplot(actividadesef,aes(x = reorder(Cod, relacion), y = relacion))+
      geom_bar(stat='identity', width = 0.5, fill = "steelblue")+
      ggtitle("Relacion por Actividad")+
      labs(x = "Actividad", y = "Relacion")+
      coord_flip()+
      theme_minimal()
    ggactrel2 <- ggplotly(ggactrel)
    ggactrel2

<div id="htmlwidget-926688865b62f865fce7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-926688865b62f865fce7">{"x":{"data":[{"orientation":"h","width":[0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5],"base":[0,0,0,0,0,0,0,0,0,0],"x":[28.1861495999331,44.6237463435019,40.7145187601958,44.1572134219043,29.3734494063441,35.3326683689754,32.7124373433584,28.8051188994155,28.8785322648671,44.9750272760335],"y":[1,9,7,8,4,6,5,2,3,10],"text":["reorder(Cod, relacion): CAMBIO_CORRECTIVO<br />relacion: 28.18615","reorder(Cod, relacion): CAMBIO_FUSIBLE<br />relacion: 44.62375","reorder(Cod, relacion): CAMBIO_PUENTES<br />relacion: 40.71452","reorder(Cod, relacion): OTRO<br />relacion: 44.15721","reorder(Cod, relacion): REVISION<br />relacion: 29.37345","reorder(Cod, relacion): REVISION_TRANSFORMADOR<br />relacion: 35.33267","reorder(Cod, relacion): VERIFICACION_INDICADORES<br />relacion: 32.71244","reorder(Cod, relacion): VERIFICACION_MEDIDORES<br />relacion: 28.80512","reorder(Cod, relacion): VISITA<br />relacion: 28.87853","reorder(Cod, relacion): VISITA_POR_CORRECCION<br />relacion: 44.97503"],"type":"bar","marker":{"autocolorscale":false,"color":"rgba(70,130,180,1)","line":{"width":1.88976377952756,"color":"transparent"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":165.844748858448},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Relacion por Actividad","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-2.24875136380167,47.2237786398351],"tickmode":"array","ticktext":["0","10","20","30","40"],"tickvals":[0,10,20,30,40],"categoryorder":"array","categoryarray":["0","10","20","30","40"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Relacion","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,10.6],"tickmode":"array","ticktext":["CAMBIO_CORRECTIVO","VERIFICACION_MEDIDORES","VISITA","REVISION","VERIFICACION_INDICADORES","REVISION_TRANSFORMADOR","CAMBIO_PUENTES","OTRO","CAMBIO_FUSIBLE","VISITA_POR_CORRECCION"],"tickvals":[1,2,3,4,5,6,7,8,9,10],"categoryorder":"array","categoryarray":["CAMBIO_CORRECTIVO","VERIFICACION_MEDIDORES","VISITA","REVISION","VERIFICACION_INDICADORES","REVISION_TRANSFORMADOR","CAMBIO_PUENTES","OTRO","CAMBIO_FUSIBLE","VISITA_POR_CORRECCION"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Actividad","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"4c306b73e62":{"x":{},"y":{},"type":"bar"}},"cur_data":"4c306b73e62","visdat":{"4c306b73e62":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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
