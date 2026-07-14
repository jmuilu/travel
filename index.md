# Itävallan ja lähialueiden matkaopas

Tervetuloa matkaoppaaseen, joka kattaa upeita kohteita Itävallassa ja Saksan puolella lähialueilla. Täältä löydät parhaat nähtävyydet, museot, sotaan liittyvät historialliset kohteet sekä valmiit päiväretkiehdotukset.

## Kohteet

Valitse alta matkakohde tutustuaksesi tarkemmin sen tarjontaan:

*   [**Innsbruck**](itävalta/Innsbruck.md) — Tirolin helmi, upeaa alppiluontoa, museoita ja runsaasti 1. maailmansodan kohteita lähistöllä.
*   [**München (Munich)**](itävalta/Munich.md) — Saksan Baijerin sydän, kulttuuria, upeita puistoja ja mielenkiintoisia automuseoita.
*   [**Zell am See**](itävalta/Zell_am_See.md) — Kauniita alppijärvimaisemia, jäätiköitä ja historiallisia linnoja.

## Matkakohteet kartalla

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
<div id="main-map" style="height: 450px; border-radius: 12px; margin: 20px 0; border: 1px solid #ddd; box-shadow: 0 4px 12px rgba(0,0,0,0.1); z-index: 1;"></div>
<script>
(function initMap() {
  if (typeof L === 'undefined') {
    setTimeout(initMap, 50);
    return;
  }
  var map = L.map('main-map').setView([47.7, 12.1], 8);
  L.tileLayer('https://{s}.basemaps.cartocdn.com/rastertiles/voyager/{z}/{x}/{y}{r}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors &copy; <a href="https://carto.com/attributions">CARTO</a>'
  }).addTo(map);

  var locations = [
    { name: "München (Munich)", coords: [48.1351, 11.5820], desc: "Kulttuuria, puistoja ja historiaa Baijerin sydämessä.", link: "itävalta/Munich.md" },
    { name: "Innsbruck", coords: [47.2692, 11.4041], desc: "Tirolin pääkaupunki, alppiluontoa ja historiaa.", link: "itävalta/Innsbruck.md" },
    { name: "Zell am See", coords: [47.3235, 12.7968], desc: "Upeita alppijärvimaisemia ja jäätiköitä.", link: "itävalta/Zell_am_See.md" }
  ];

  locations.forEach(function(loc) {
    L.marker(loc.coords).addTo(map)
      .bindPopup('<b><a href="' + loc.link + '">' + loc.name + '</a></b><br>' + loc.desc);
  });
})();
</script>

---
*Tämä sivusto on julkaistu automaattisesti GitHub Pagesin avulla.*  
*Created by Antigravity*
