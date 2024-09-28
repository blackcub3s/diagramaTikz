# Objetivo

En este repositorio muestro el código en LaTeX necesario para la creación del diagrama de la aplicación de mi repositorio demostración "[miApp](https://github.com/blackcub3s/miApp)"" mediante la librería de latex Tikz ([https://tikz.dev/](https://tikz.dev/)).

Para llegar a ese diagrama se partió del diagrama original hecho a mano alzada (ver apartado [Semilla](#Semilla)), pasando por el código que chat gpt generó del mismo (ver apartado [versión gpt](#versión-gpt)), y la modificación que hizo al código de chatGPT para llegar al código LaTeX que compila el diagrama de la versión final (ver apartado [versión final](#versión-final)).

>NOTA: La librería Tikz permite dibujar diagramas con la elevada calidad tipográfica que nos proporciona LaTeX mediante la definición de una estructura de nodos y aristas (es decir, de grafo) y un sistema propio interno para generar posicionamientos entre nodos y estilos defiibles independientemente y aplicables a dichos nodos.

# Semilla

Inicialmente el diagrama lo dibujé a mano alzada:

![diagrama no cargó](/img/peticionSemilla.PNG)

# versión gpt

Se pasó la imagen de este diagrama a chatGPT (véase [prompt](/img/peticionSemilla.PNG)) que generó el código [semillaGPT](/semillaGPT.tex). Este código, al compilarse, genera una primera "semilla" de aspecto verdaderamente aberrante (véase [imagen](img/compilacionSemillaCaptura.PNG)) pero cuyos nodos y aristas ya están definidas y permite ahorrarse dos horas de trabajo perfectamente dado que se convierte en una primera aproximación al problema:

![diagrama gpt aberrante no cargó](/img/compilacionSemillaCaptura.PNG)


# Versión final

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

# ¿Qué instalar para compilar un archivo .tex?

Si el lector desea obtener el resultado de la compilación del código .txt en un [pdf](/diagramaTikzDefinitiu.pdf), puede instalarse la distribución MikTex (si usa windows) o texLive (si usa linux). En ambos casos el editor teXstudio es idóneo para editar i compilar archivos .tex. 






