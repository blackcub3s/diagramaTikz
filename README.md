# Introducción

En este repositorio muestro el código en LaTeX necesario para la creación del diagrama de la aplicación de mi repositorio demostración "[miApp](https://github.com/blackcub3s/miApp)" mediante la librería de LaTeX Tikz ([https://tikz.dev/](https://tikz.dev/)).

Para llegar a ese diagrama se partió del diagrama original hecho a mano alzada (ver apartado [Semilla](#Semilla)), pasando por el código que chat gpt generó del mismo (ver apartado [versión gpt](#versión-gpt)) hasta llegar hasta el código LaTeX que compila el diagrama de la versión final (ver apartado [versión final](#versión-final)).

>NOTA: La librería Tikz permite dibujar diagramas con la elevada calidad tipográfica que nos proporciona LaTeX mediante la definición de una estructura de nodos y aristas (es decir, de grafo) y un sistema propio interno para generar posicionamientos entre nodos y estilos defiibles independientemente y aplicables a dichos nodos.

# Semilla

Inicialmente el diagrama lo dibujé a mano alzada:

![aquí](/img/esquemaApp.jpeg)

Luego le pasé a chatGPT una fotografía del mismo acompañada de la siguiente prompt:

![diagrama no cargó](/img/peticionSemilla.PNG)

# versión gpt

La petición del apartado anterior consiguió que la herramienta de openAI generase el código [semillaGPT](/semillaGPT.tex). Este código, al compilarse, produce una primera "semilla" de aspecto verdaderamente aberrante pero cuyos nodos y aristas ya están definidos:

<div align="center">
  <img src="/img/compilacionSemillaCaptura.PNG" alt="diagrama gpt aberrante no cargó" />
</div>

>NOTA: Hace años que programo en latex y puedo asegurar que chat gpt no genera diagramas tikz de calidad si el programador no tiene conocimiento de lo que está haciendo, pero la cantidad de trabajo que es posible ahorrarse si uno ya conoce el lenguaje LaTeX es verdaderamente increible (este diagrama lo tuve listo en un par o tres de horas, mientras que sin chatGPT podría haberme demorado perfectamente una tarde entera -siendo optimista-).

# Versión final

Se tomó [semillaGPT](/semillaGPT.tex) y se fue modificando, borrando lo innecesario y añadiendo:

1. Nodos fantasma o vacíos para permitir flechas a 90 grados (`invisible1`,`invisible2`) -sin los cuales no es posible definir flechas entre nodos visibles que tengan ángulos de 90 grados-.
2. Nuevos nodos para considerar desde los nodos con las urls (`dummy1`, `dummy2`... `dummy11`) hasta los nodos de las notas en la cabezera (`asterisc1sortida`, `asterisc1Arribada`,`asterisc1Explicacio`,`asterisc1ExplicacioComplement`)
3. Nodos de decisión para el back-end (`dec1`,`dec2`) y para el frontend (`paypal`, `debit`, `altre`).
3. Se definieron posiciones relativas de todos los nodos mediante las propiedades `below of`, `right of`, `left of`, etc. asi como `xshift` y `yshift`.
4. Los paralelepípedos se sustituyeron por rectángulos por mejora en el aspecto final.
5. Se aplicaron los estilos pertinentes a los nodos (`decisionBackend`, `decisionFrontend`, `aspecteAsterisc`, `aspecteExplicacioAsterisc`,etc).
4. Se definieron tres colores mediante RGB `yellowfosforito`, `blauCian`, `taronjaBrillant`.

Después de este proceso se obtuvo el resultado final [diagramaTikzDefinitiu.tex](/diagramaTikzDefinitiu.tex) y después de compilarlo se generó un resultado de aspecto tipográfico cercano a la imagen original y plenamente satisfactorio. Se puede consultar [aquí](/diagramaTikzDefinitiu.pdf) y en la siguiente imagen:

![diagrama output no cargó](/img/diagramaOutput.png)

# ¿Qué instalar para compilar un archivo .tex?

Si el lector desea obtener el resultado de la compilación del código .tex en un [pdf](/diagramaTikzDefinitiu.pdf), puede instalarse la distribución MikTex (si usa windows) o texLive (si usa linux). En ambos casos el editor teXstudio es idóneo para editar y compilar archivos .tex. 

A continuación especifico estos pasos para hacer la instalación de latex en Linux (tanto del compilador como del editor):
```
    sudo apt update
    sudo apt install texlive
    sudo apt install texstudio
```

Una vez instalado el compilador ya podemos compilar el archivo con pdflatex (que pertenece a texlive) para obtener así el pdf resultante con el siguiente ocmando:

```
    pdflatex diagramaTikzDefinitiu.tex
```

Si se desea obtener la imagen del diagrama en lugar de un pdf, con la máxima calidad se puede tratar de obtener un archivo .svg. Este formato asefgura que la calidad sea máxima incluso al hacer zoom, dado que no es una archivo de imagen per se, sino que se renderiza en tiempo real en el navegador. Para poder generar el .svg del diagrama debemos instalar el paquete `dvisvgm` con el comando:

```sudo apt install dvisvgm```

Acto seguido ya podremos obtener un archivo .dvi desde el archivo .tex, que nos permitirá obtener a su vez el archivo .svg deseado. Lo haremos con estos dos comandos:


```
    # creamos el archivo .dvi a partir del .tex
    latex diagramaTikzDefinitiu.tex

    # creamos el archivo .svg buscado a partir del .dvi
    dvisvgm diagramaTikzDefinitiu.dvi   
```


