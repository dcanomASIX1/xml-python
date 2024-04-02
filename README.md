#    Documentacio DOM i XSLT/XPATH
## DOM
És un modul de python que permet treballar amb fitxers **XML**
### Estructura
L'estructura dels elements quan treballem amb el modul de DOM hereden d'un node anterior fin arribar al node arrel , es a dir es treballa amb una estructura d'arbre on tots els nodes estan conectats a un node anterior exepte el node arrel.

Aquesta estructura es com la del **XSD**

Per idicar el fill al qual volem accedir empleem **[X]** al costat del element fill indicant el numero al cual volem accedir es a dir
Doc.chilnodes **[0]** fa referencia al numero (*de la posicio*) del fill on ens ubiquen en aquest moment

**ej**
Doc.chilnodes **[0]** Doc.chilnodes **[0]** Doc.chilnodes **[0]** 
en aquest cas estariem fen referencia al Primer fill del primer fill del primer fill del elemenr **arrel**

### Objectes en DOM
Al treballar en DOM exiteixen una gran varietat d'elements als cuals hi podem accedir a la seva enformacio. 
Aquest es coneixen com **OBJECTES**
a continuacio una imatge amb tots els objectes amb els que podem interactuar:

![Captura de pantalla de 2024-04-02 16-35-43](https://github.com/dcanomASIX1/xml-python/assets/165805335/16131955-b04c-48ee-8aba-e3f7c146ed59)
