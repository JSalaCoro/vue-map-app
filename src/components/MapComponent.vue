

<template>
    <div ref="map-root" style="width: 100%; height: 100%"></div>
  </template>
  
  <script>
    import View from 'ol/View'
    import Map from 'ol/Map'
    import TileLayer from 'ol/layer/Tile'
    import OSM from 'ol/source/OSM'
    import Static from 'ol/source/ImageStatic.js';
    import ImageLayer from 'ol/layer/Image.js';

    // importing the OpenLayers stylesheet is required for having
    // good looking buttons!
    import 'ol/ol.css'
  
    export default {
      name: 'MapContainer',
      components: {},
      props: {},
      mounted() {
        // this is where we create the OpenLayers map

        const pngSource = new Static({
          url: 'http://localhost:5173/vue-map-app/src/data/map/NEP_2023.png',
          imageExtent: [-849.770, 4862430.787, 629354.408, 5308029.701]
        })

        new Map({
          // the map will be created using the 'map-root' ref
          target: this.$refs['map-root'],
          layers: [
            // adding a background tiled layer
            new TileLayer({
              source: new OSM() // tiles are served by OpenStreetMap
            }),
            new ImageLayer({
              source: pngSource
            })
          ],
          // the map view will initially show the whole world
          view: new View({
            zoom: 7.5,
            center: [239298.956079, 5043620.874369],
            constrainResolution: true
          }),
        })
      },
    }
  </script>
  