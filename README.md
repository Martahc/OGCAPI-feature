# OGCAPI-feature

## ProcesadorAnotacionSemantica

Este Notebook de Phyton se va utilizar para dos funciones:

- Preprocesar las propiedades y los valores de esas propiedades de cada feature.
- Realizar consultas SPARQL distruibuidas a los repositorios de Wikidata, Dbpedia y LinkedGeoData, con las propiedades y los valores preprocesados.

### Requisitos de ejecucion
Este codigo ha sido desarrollado y probado con Python 3.9.12 y pip 21.2.4.

Es necesario tener una cuenta de usuario en las siguientes APIs: 
  - BabelNet ( https://babelnet.org/ )
  - bing-spell-check2 ( https://rapidapi.com/microsoft-azure-org-microsoft-cognitive-services/api/bing-spell-check2/ )

*Estas APIs le proporciona una clave API que debe introducir en el codigo, en los metodos make_synonymous y make_suggestion*

Ejemplo BabelNet: 

```
def make_synonymous(word,source_lang,target_lang):
    url = f"https://babelnet.io/v8/getSynsetIds?lemma={word}&searchLang={source_lang}&targetLang={target_lang}&key={claveAPI}"
    response = requests.get(url)
    ....
  
    for synset_id in synset_ids:
        ....
        url = f"https://babelnet.io/v8/getSynset?id=bn:{id}&key={claveAPI}"
        ....

    return resul
```
Ejemplo bing-spell-check2

```
def make_suggestion(word):
    url = "https://bing-spell-check2.p.rapidapi.com/spellcheck"
    ....
    
    headers = {
        'X-RapidAPI-Key': '{claveAPI}',
        'X-RapidAPI-Host': 'bing-spell-check2.p.rapidapi.com'
    }
    ...
   
```

### Instrucciones de ejecucion

Se debe cambiar el nombre de la API en las URI que sean iguales a:
"https://geo.linkeddata.es/{nombreAPI}/feature/"

Ejemplo:

Si la URL de la cual vamos a preprocesar los datos fuese:

```
"https://geoserveis.ide.cat/servei/catalunya/inspire/ogc/features/collections/inspire:PS.ProtectedSite.Natura2000/items?f=json"
```

El nombre de la API es:

```
geoserveis.ide.cat
```

Las URI deben ser:

```
"https://geo.linkeddata.es/geoserveis.ide.cat/feature/"
```


### License and contact

Distribuido bajo [Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0). 

Principal autor y contacto: Marta Hidalgo 
