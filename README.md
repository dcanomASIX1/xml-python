# xml-python

Procesamos/       ficheros xml
Trasnformamos/

-3 Semanas DOM
-2Semanas SAXs
-2Semanas XSLT + Xpatch


Apuntes : MarkDown → Tomar apuntes desde aqui

DOM: Document Object Model 
* Metodos == Funciones /Herramientas → Nom(Argumento)
* No implementado 
* Python Paquete XML.DOM.
    * MiniDOM


## Estructura
Forma estructura de arbol **Como HTML o XSD**
Separar nodos por 
    1. Elementos 
    2. Raiz

**Elementos a un mismo nivel son hermanos**

Doc.chilnodes **[0]** hace referencia al numero del hijo de donde estas 

**ej**
Doc.chilnodes **[0]** Doc.chilnodes **[0]** Doc.chilnodes **[0]** 
Haria referencia al hijo 0 del hijo 0 del hijo 0 de la referencia raiz

**Firstchild** es el primer hijo == Doc.chilnodes **[0]**
**LAstchil** Ultimo hijo4

TagName == Nombre de la etiqueta
**GetAtribute**
**GetElementByTagName**()


## DOM desde Python

xml.dom.minidom == **Modulo**

obtener datos desde XML

#### Tipus objetos
1. ATTR
1. Comment
1. Text
1. ProcesingInstruction



from xml.DOM import Minidom
doc =minidom.parse(**"fitxer.xml"**)



Nodo raiz= Document --> tiene un unico hijo Nodo raiz del xml


	
Sirve para :-1: 
1.     Obtener datos
2.     Modificar datos
3.     Añadir datos



**Tipos de elementos**
>>Representas tipos de nodos>>
*     Node
*     Document 
*     Element
*     Text


## XSLT  Y XPATH
- EXTENSIBLE STYLESHEAT LANGUAGE TRANSFORM

-**XPATH** -->Transforma XML EN arbol

