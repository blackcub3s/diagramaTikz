# Objetivo

En este repositorio muestro el código LaTeX para la creación del diagrama de la aplicación [miApp](https://github.com/blackcub3s/miApp).

# Semilla

Inicialmente el diagrama lo dibujé a mano alzada:


Se pasó la imagen de este diagrama a chatGPT (véase [prompt](/img/peticionSemilla.PNG)) que generó el código [semillaGPT](/semillaGPT.tex). Este código, al compilarse, genera una primera "semilla" de aspecto aberrante (véase [imagen](img/compilacionSemillaCaptura.PNG)), pero una primera aproximación al problema (con nodos y aristas ya definidos) que permite ahorrarse dos horas de trabajo perfectamente, incluso si se es un programador LaTeX avanzado


# versión final (svg)

Se tomó [semillaGPT](/semillaGPT.tex) y se fue modificando, borrando lo innecesario y añadiendo:

1. Nodos fantasma o vacíos para permitir flechas a 90 grados (`invisible1`,`invisible2`).
2. Nuevos nodos para considerar desde los nodos con las urls (`dummy1`, `dummy2`... `dummy11`) hasta los nodos de las notas en la cabezera (`asterisc1sortida`, `asterisc1Arribada`,`asterisc1Explicacio`,`asterisc1ExplicacioComplement`)
3. Nodos de decisión para el back-end (`dec1`,`dec2`) y para el frontend (`paypal`, `debit`, `altre`).
3. Se definieron posiciones relativas de todos los nodos mediante las propiedades `below of`, `right of`, `left of`, etc. asi como `xshift` y `yshift`.
4. Los paralelepípedos se sustituyeron por rectángulos por mejora en el aspecto final.
5. Se aplicaron los estilos pertinentes a los nodos (`decisionBackend`, `decisionFrontend`, `aspecteAsterisc`, `aspecteExplicacioAsterisc`,etc).
4. Se definieron tres colores mediante RGB `yellowfosforito`, `blauCian`, `taronjaBrillant`.

Después de este proceso se obtuvo el resultado final [diagramaTikzDefinitiu.tex](/diagramaTikzDefinitiu.tex) y después de compilarlo se generó un resultado de aspecto tipográfico cercano a la imagen original y plenamente satisfactorio. Se puede consultar [aquí](/diagramaTikzDefinitiu.pdf) y en la siguiente imagen:

![diagrama output no cargó](/img/diagramaOutput.png)

# Compilar el codigo 

Si el lector desea obtener el resultado de la compilación del código en [pdf](/diagramaTikzDefinitiu.pdf) por sí mismo puede instalarse MikTex en windows y el editor teXstudio para compilar el archivo .tex. 

Alternativamente, si se quiere correr en linux, puede instalarse LaTeX también con la distribución texLive.






