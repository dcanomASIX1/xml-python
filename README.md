#    Documentacio DOM i XSLT/XPATH
## DOM
És un modul de python que permet treballar amb fitxers **XML**
### Estructura
L'estructura dels elements quan treballem amb el modul de DOM hereden d'un node anterior fin arribar al node arrel , es a dir es treballa amb una estructura d'arbre on tots els nodes estan conectats a un node anterior exepte el node arrel.

Aquesta estructura es com la del **XSD**

Per idicar el fill al qual volem accedir empleem **[X]** al costat del element fill indicant el numero al cual volem accedir es a dir
Doc.chilnodes **[0]** fa referencia al numero (*de la posicio*) del fill on ens ubiquen en aquest moment

**ex**
Doc.chilnodes **[0]** Doc.chilnodes **[0]** Doc.chilnodes **[0]** 
en aquest cas estariem fen referencia al Primer fill del primer fill del primer fill del elemenr **arrel**

### Objectes en DOM
Al treballar en DOM exiteixen una gran varietat d'elements als cuals hi podem accedir a la seva enformacio. 
Aquest es coneixen com **OBJECTES**
a continuacio una imatge amb tots els objectes amb els que podem interactuar:

![Captura de pantalla de 2024-04-02 16-35-43](https://github.com/dcanomASIX1/xml-python/assets/165805335/eddccb75-0f12-480e-83ca-9efb38e1ad14)

### Primers pasos

Ara be un cop coneixem els objectes i com esta estructurat com podem começar a treballar amb aquest modul de pyhton?

1. Cmençem important el modul de dom amb la seguent linea de codi:
`from xml.dom import minidom `
2. Indiquem el document **XML**amb el qual importarem dades i treballarem 
 `personas=doc.getElementsByTagName("person") `
Cal tenir en compte que per poder accedir al document , cal esta ubicat en la terminal on executem en la mateixa capeta del arxiu **XML** indicat

3. Obrim en mode d'escriptura un nou arxiu en el qual mes endevant escriurem les dades desitjades
`f_=open("HTML_ACT6", "w")`
- **f_** --> És el nom de la variable del nou arxiu creat
- **HTML_ACT6** --> És el nom amb el cual es crearà l'arxiu, pots posar el que desitgis 
- **w** --> Indica que l'arxiu s'obrira en opcio d' escriptura


4. Indiquem l'element a escriure amb la funcio f_.write(*Aqui indiquem l'element que desitgem escriure*)

### Petits truquets a l'hora d'Implementacio d'Objectes
- Quan desitgis obtenir un element pel nom pots emplear **getElementsByTagName("name")[0]**
**name** --> fa referencia al nom que destgis indicar 
**0** --> Fa referencia a la posocio que desitgis agafar d'aquest fill

- **Compte** amb eredar pel nom, Ja que agafaras tots els elements per el nom. Si desitges filtrar pots indicar l'element anterior i despres eredar el que desitgis
`Colores = doc.getElementsByTagName("colors")[0].getElementsByTagName("assignatura")`
- **getElementsByTagName** t'agrupta tots els elements amb el mateix nom.**Pots buscar per altres indicadors, però l'aplicacio és emblant**
- Per agafar el text, indiques el fill que desitgis i **.firstChild.data**
`getElementsByTagName("name")[0].firstChild.data`
- Si vols agafar l'atribut emplees **getAttribute** despres del firstChild
`getElementsByTagName("name")[0].firstChild.data`

  
#### **Importatnt**

has de tenir en compte que el que enmagatzemes a la variable són totes les etiquetes (i la informacio dintre d'aquestes) amb el nom indicat, filles de la variable a la qual aplique el **getElementByTagNAme**

**ex**

```doc = minidom.parse("horari.xml")```
```dia=doc.getElementsByTagName("dia")```

* Començem guardant la informacio del arxiu **horari.xml* a una variable anomenada **doc**, per tant aquesta actuara com la etiqueta arrel o primer pare.
  
* En aquest cas estas guardant a la variable **dia** totes les etiquetes amb nom dia, filles de l'etiqueta arrel 
  

- Per veure totes les implementacion d'objectes visita la seguent pagina: https://docs.python.org/3/library/xml.dom.html



### Implementacio del bucle FOR
Usualment cuant volguem enmagatzemar diverses dates diferents d'un mateix pare emplearem un bucle **FOR* en el qual a la variable que recorres enmagatzemes la informacio desitjada en forma de llista  y amb la variable x recorres aquesta llista
**ex**

```for x in Colores:
    ColorAssignatura = x.firstChild.data
    AtributoColor= x.getAttribute("color")
    print(f'''{AtributoColor} {ColorAssignatura}''')
    DiccionarioColores[ColorAssignatura]= AtributoColor```


### Exemple d'implementacio en un codi "simple"
```
from xml.dom import minidom 
doc=minidom.parse("111.xml")

personas=doc.getElementsByTagName("person") 
f_=open("HTML_ACT6", "w")



f_.write('''<html><head><title>Diaris DOM</title></head>
   <body>''')
for x in personas:
    ids=x.getAttribute("id")
    
    gender=x.getElementsByTagName("name")[0].getAttribute("gender")
    
    nom=x.getElementsByTagName("name")[0].firstChild.data
    
    age=x.getElementsByTagName("age")[0].firstChild.data
    
    naixement=x.getElementsByTagName("naixement")[0].firstChild.data
    f_.write(f'''      <h2>{ids} - {nom}</h2>
       <ul>
           <li>age - { age}</li>
           <li>sex - {gender}</li>
           <li>maixement - { naixement}</li>
       </ul>''')
f_.write('''</body>
</html>
      ''')
```

## XSLT i XPATH
### Introduccio XSLT
XSLT és un llenguatge que s'emplea per transformar ditxers XML en fitxer d'aletres tipus com podes HTML , text o d'altres com tambe es pot convertir en altre tipus d'XML. **En aquest cas aprendrem a transformar en HTML**. 
Tingues en compte que es necesita tenir un *processador XSLT* i aprendre *XPATH*
### XPATH
Es un sistema empleat per la seleccio dels nodes

Existeixen 7 tipus de nodes possibles

![Captura de pantalla de 2024-04-02 17-29-53](https://github.com/dcanomASIX1/xml-python/assets/165805335/116cfcb4-f9e9-4a3a-b641-31c2267852be)

Aquest tambe te una estructura tipus arbre amb tots els nodes amb un node pare exepte el **Node arrel**

Cada element pot tenir entre 0 o diversos fills 

Els elements amb el mateix pare es consideren germans

#### SELECCIO DE NODES

![Captura de pantalla de 2024-04-02 17-38-23](https://github.com/dcanomASIX1/xml-python/assets/165805335/ac07360b-55dd-47b7-a01c-aa05031fe75c)

**Buscar nodes especifics**
Per filtrar els nodes desitjats emplearem **[]** radera del node que desitgem filtrar en el qual indicamer els elements i quantitats a buscar

exemples per buscar nodes especifics

**/botiga/bluray[1]** indica el primer element bluray.

**//title[@idioma]** indica els títols amb l’atribut idioma.

**//title[@idioma=‘cat’]** indica els títols amb l’atribut idioma igual a cat.

**/botiga/bluray[preu>10]** indica tots els bluray amb preu >10.

**/botiga/bluray[preu>10]/any** indica tots els anys dels bluray amb preu >10.

**/botiga/*/preu** indica tots els preus dels fills de botiga.

**//*** indica tots els elements del document.

**//titol[@*]** indica tots els elements titol amb qualsevol atribut.

**//titol | // preu** indica tots els titols i preus del document.

**/botiga/bluray[2]/titol** indica el títol del segon bluray

**/botiga/bluray[position()<6]/titol** indica el títol de les 5 primeres entrades.

### Treballar amb XSLT
1. Creem un document amb extensio xsl i indiquem el seguent
`<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
....
</xsl:stylesheet>`
Assegurat que els dos docuemtns estiguin a la mateixa carpeta

2.Al document **XML** referenciem el document anterior

```<?xml version="1.0" encoding="UTF-8"?>```

```<?xml-stylesheet type="text/xsl" href="fitxer.xsl"?>```
    
* **type** = Indica el tipus de fitxer al qual esta referenciat

* **href** = referencia al nom fitxer de referencia 

#### Element <xsl:template>
Aquest element s'emplea per crear les plantilles d'XLT



```<?xml version="1.0" encoding="UTF-8"?>```

```<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform ">```

```<xsl:template match="/">```

*Aqui va l'estructura HTML*

```</xsl:template>```

```</xsl:stylesheet>```


* **match** S'emlea per associar l'element arrel de la plantilla a un element del xml original. Es a dir és un element **XPATH**

**Exemple de com acabaria**


<img width="332" alt="Captura3" src="https://github.com/dcanomASIX1/xml-python/assets/165805335/f350364c-782e-44b1-bab1-5bada4b3c91c">

#### Element <xsl:value-of>
S'emplea per extreure els valors d'els elements

```<td><xsl:value-of select="catalog/cd/title"/></td>```

```<td><xsl:value-of select="catalog/cd/artist"/></td>```

En aquest cas s'extreu el valor text acumulat registrat en **catalog/cd/title** i **catalog/cd/artist**





#### L'element <xsl:for-each>
Faria la funcio d' un for en un llenguatge de programació es a dir , recorre tots els **elements** del nivell indicat.

![Captura de pantalla de 2024-04-02 20-06-10](https://github.com/dcanomASIX1/xml-python/assets/165805335/6a04211a-c70d-452c-833e-106edcb5deaa)

En aquest exemple recorrem tots els cd que heredin de catalog i el seu artista sigui Bob Dylan

#### L'element <xsl:sort>
Serveix per ordenar segons un element una agrupacio d'Elements superiors que els contingui 

![Captura de pantalla de 2024-04-02 20-06-21](https://github.com/dcanomASIX1/xml-python/assets/165805335/17f72932-c86c-4820-b858-0c182cf9c7c7)


#### L'element <xsl:if>
S'emplea despres del for each per posar una condicio al contingut del fitxer XML

![Captura de pantalla de 2024-04-02 20-06-53](https://github.com/dcanomASIX1/xml-python/assets/165805335/10fcf37c-235c-496d-a7b4-b2261161fd90)


#### L'element <xsl:choose>
S'emplea per poder obtenir una condicio multiple, és a dir diversos if junts depenent del numero de condicions requerides.

![Captura de pantalla de 2024-04-02 20-07-05](https://github.com/dcanomASIX1/xml-python/assets/165805335/f64e84c4-6ca3-4e4d-b35b-2c3c265467f3)

D'aquest depenenen les funcions  **xsl:when** i **xsl:otherwhise**



en aquest exemple declarem un color en l'artitsa si el preu del disc es superior a 10

#### Afegir enllaços e imatges
s'emplea l'atribut **xsl:attribute name="href"** per afegir enllaçps de referencia

![Captura de pantalla de 2024-04-02 20-10-48](https://github.com/dcanomASIX1/xml-python/assets/165805335/1410fbb1-47cf-47bb-8b84-7a7a345e8e86)


s'emplea l'atribut **xsl:attribute name="src"** per afegir imatges

![Captura de pantalla de 2024-04-02 20-07-27](https://github.com/dcanomASIX1/xml-python/assets/165805335/462803ec-ac63-49c0-9ee5-4d920515fb52)

#### Declarar varables

Per crear noves variables amb les vuals treballar emplearem la seguent linea de codi 
```<xsl:variable name="i" select="position()"/>```
**name** indica el nom de la variable
**select** el tipus de la variable a eeplear

per emplear les variables les cridarem de la seguen forma: [$i].
On **i** representa el nom de la varaible

**ej**

```<xsl:variable name="color" select="/horari/colors/color[@codi=current()/modul[$i]/codi]"/>```

si desitges aprofundir mes pots visitar: https://www.w3schools.com/xml/xsl_intro.asp

#### Exemple de codi XSLT
```<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <html>
    <head>
      <style type="text/css">
      body{
        margin:0;
        padding: 0;
    }
    
    table{
        padding: 10px;
        border: 4px solid black;
        border-collapse: collapse;
        background-color: rgb(240, 240, 240);
        margin: 0 ;
    }
    td{
        padding-left: 6vw;
        padding-right: 6vw;
    }
  </style>
    </head>
    <body >
      <img width="100%" height="100pv" margin="0px"  >
        <xsl:attribute name="src">
          <xsl:value-of select="horari/@header"/>
        </xsl:attribute>
      </img> 
      <table >
        <tr>
          <xsl:for-each select="horari/setmana/dia">
            <td class="table1">
              
                  <xsl:value-of select="@nom"/>    
            </td>
          </xsl:for-each>
        </tr>
        <xsl:for-each select="horari/setmana/dia[1]/modul">
        <xsl:variable name="i" select="position()"/>
        <tr>
          <xsl:for-each select="/horari/setmana/dia">
            <xsl:variable name="color" select="/horari/colors/color[@codi=current()/modul[$i]/codi]"/>
            <td style="background-color: {$color}">
              <xsl:value-of select="concat(modul[$i]/codi, ' ', modul[$i]/nom)"/>
            </td>
          </xsl:for-each>   
        </tr>
      </xsl:for-each>
      </table>
      <p style="text-align:center">
      <h2>
        <xsl:value-of select="horari/links/@nom" />
      </h2>
      <xsl:for-each select="horari/links/link">
        <xsl:sort select="nom"/>
        <p>
        <a>
          <xsl:attribute name="href">
          <xsl:value-of select="url"/>
          </xsl:attribute>
          <xsl:value-of select="nom"/>
        </a>
      </p>
        </xsl:for-each>
      </p>
    </body>
  </html>
</xsl:template>

</xsl:stylesheet>```
