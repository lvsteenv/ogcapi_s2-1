# Stap 5

We gaan een OGC API Features service maken voor Kontich! Joepie
Het is te zeggen, we gaan de stubs opzetten voor de OGC API Feature service en ze even in detail gaan bekijken (dit kwam al aan bod in sessie 1 van deze FLAGIS academische sessie)

## 1 Voorbereiding:
Eerst even Express installeren (om de repo zo klein mogelijk te houden, zit `express` er niet bij en moet je het installeren `npm install express --save` bij de eerste keer dat je de code runt in de directory. Eenmaal het er staat, ben je OK)


## 2 Eerste voorzichtige stapjes
```javascript
var express = require('express')
var router = express.Router()

// middleware that is specific to this router
router.use(function timeLog (req, res, next) {
  console.log('Time: ', Date.now())
  next()
})

// The server SHALL support the HTTP GET operation at the path /.
router.get('/', function (req, res) {
  res.send('Kontich landing page')
})

// The server SHALL support the HTTP GET operation at the path /conformance.
router.get('/conformance', function (req, res) {
  res.send('conformance page')
})

// Collections provides information about and access to the collections.
// The server SHALL support the HTTP GET operation at the path /collections.
router.get('/collections', function (req, res) {
  res.send('collections on this server')
})

// The server SHALL support the HTTP GET operation at the path
router.get('/collections/:collectionId', function (req, res) {
  console.log(req.params);
  res.send('collections on this server met bomen')
})

// define the about route
router.get('/collections/:collectionId/items', function (req, res) {
  res.send('collections on this server met bomen items')
})

// define the about route
router.get('/collections/:collectionId/items/:item', function (req, res) {
  console.log(req.params);
  res.send('collections on this server met bomen items id')
})

module.exports = router
```

We hebben een Landing Page, Conformance en Collections opgezet - mooi!
Dit zijn 3 essentiele paden die **moeten** aanwezig zijn

Laten we eens in de spec kijken wat we hier mee aan moeten:
- [Landing Page](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_api_landing_page)
- [Conformance](https://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_declaration_of_conformance_classes)
- [Feature collections](https://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_collections_)
- [Feature collection](https://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_collection_)
- [Feature](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_items_)

## Testen

http://localhost/kontich/

> `Kontich landing page`

## Klaar voor de volgende stap
https://github.com/flagis/ogcapi_s2/blob/master/step6/README.md
