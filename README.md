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
![Captura de pantalla de 2024-04-02 16-35-43](https://hackmd.io/_uploads/SJ2yO9Fy0.png)

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

### Petits truquets a l'hora d'Implementacio d'O bjectes
- Quan desitgis obtenir un element pel nom pots emplear **getElementsByTagName("name")[0]**
**name** --> fa referencia al nom que destgis indicar 
**0** --> Fa referencia a la posocio que desitgis agafar d'aquest fill

- Compte amb eredar pel nom, Ja que agafaras tots els elements per el nom. Si desitges filtrar pots indicar e¡l'element anterior i despres eredar el que desitgis
`Colores = doc.getElementsByTagName("colors")[0].getElementsByTagName("assignatura")`
- **getElementsByTagName** t'agrupta tots els elements amb el mateix nom.**Pots buscar per altres indicadors, però l'aplicacio és emblant**
- Per agafar el text, indiques el fill que desitgis i **.firstChild.data**
`getElementsByTagName("name")[0].firstChild.data`
- Si vols agafar l'atribut emplees **getAttribute** despres del firstChild
`getElementsByTagName("name")[0].firstChild.data`
- Per veure totes les implementacion d'objectes visita la seguent pagina: https://docs.python.org/3/library/xml.dom.html

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

