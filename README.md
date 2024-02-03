# Wind farms in scotland
### circleMarker popup fixed

Live Demo: https://rmcf.github.io/wind-farms-in-scotland-cluster-popup/

I have just added this code to the script section into index.html

Rows [101-142](https://github.com/rmcf/wind-farms-in-scotland-cluster-popup/blob/90f7a5cb0b1e539e430a1efbb13615b8ef316764/index.html#L101)

```JS
      // clustering with popups
      // ==========================================================
      var markers = L.markerClusterGroup()

      L.geoJSON(windFarmsAll, {
        pointToLayer: function (feature, latlng) {
          return L.circleMarker(latlng, markerStyle(feature))
        },
        onEachFeature: function (feature, layer) {
          layer.bindPopup(markerPopUp(feature))
        },
      }).addTo(markers)

      map.addLayer(markers)

      // circle style
      function markerStyle(feature) {
        return {
          radius: 5,
          color: feature.properties.color,
          weight: 1,
          opacity: 1,
          fillOpacity: 0.9,
        }
      }

      // circle popup content
      function markerPopUp(feature) {
        const text =
          '<h4>Wind Farms</h4>' +
          '<div class="container"><table class="table table-striped">' +
          '<tbody><tr><td> Name </td><td>' +
          feature.properties.Name +
          '</td></tr>' +
          '<tr><td>Type </td><td>' +
          feature.properties.Type +
          '</td></tr>' +
          '<tr><td> Capacity (MW) </td><td>' +
          feature.properties.MW
        return text
      }
      // ==========================================================

```
