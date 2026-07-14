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
    // Pääkohteet
    { name: "München (Munich)", coords: [48.1351, 11.5820], desc: "<b>Pääkohde</b>: Kulttuuria, puistoja ja historiaa Baijerin sydämessä.", link: "itävalta/Munich.html" },
    { name: "Innsbruck", coords: [47.2692, 11.4041], desc: "<b>Pääkohde</b>: Tirolin pääkaupunki, alppiluontoa ja historiaa.", link: "itävalta/Innsbruck.html" },
    { name: "Zell am See", coords: [47.3235, 12.7968], desc: "<b>Pääkohde</b>: Upeita alppijärvimaisemia ja jäätiköitä.", link: "itävalta/Zell_am_See.html" },

    // Sellrain
    { name: "Sellrain (Lähtöpiste)", coords: [47.2133, 11.2181], desc: "Innsbruckin alueen matkasi majoitus- ja aloituspiste.", link: "itävalta/Innsbruck.html" },

    // Innsbruckin kohteet
    { name: "Kultainen katto (Goldenes Dachl)", coords: [47.2686, 11.3933], desc: "Innsbruckin tunnetuin maamerkki.", link: "itävalta/Innsbruck.html" },
    { name: "Stadtturm", coords: [47.2685, 11.3937], desc: "Keskiaikainen kaupungintorni Innsbruckissa.", link: "itävalta/Innsbruck.html" },
    { name: "Hofkirche & Volkskunstmuseum", coords: [47.2689, 11.3956], desc: "Hovikirkko ja Tirolin kansantaiteen museo.", link: "itävalta/Innsbruck.html" },
    { name: "Keisarillinen palatsi (Hofburg)", coords: [47.2689, 11.3946], desc: "Innsbruckin keisarillinen palatsi.", link: "itävalta/Innsbruck.html" },
    { name: "Nordkette (Hafelekar)", coords: [47.3115, 11.3837], desc: "Innsbruckin alppihuiput köysiradalla.", link: "itävalta/Innsbruck.html" },
    { name: "Schloss Ambras", coords: [47.2636, 11.4319], desc: "Upea renessanssilinna Innsbruckissa.", link: "itävalta/Innsbruck.html" },
    { name: "Bergisel & Tirol Panorama", coords: [47.2485, 11.3995], desc: "Hyppyrimäki ja panoraamamuseo.", link: "itävalta/Innsbruck.html" },
    { name: "Swarovski Kristallwelten", coords: [47.2861, 11.5975], desc: "Kristallitaiteen elämysmaailma Wattensissa (15 km Innsbruckista).", link: "itävalta/Innsbruck.html" },
    { name: "Hall in Tirol", coords: [47.2804, 11.5076], desc: "Keskiaikainen suolakaupunki.", link: "itävalta/Innsbruck.html" },
    { name: "Seefeld in Tirol", coords: [47.3294, 11.1873], desc: "Alppikylä ja ulkoilualue.", link: "itävalta/Innsbruck.html" },
    { name: "Stubaier Gletscher", coords: [46.9858, 11.1118], desc: "Stubai-jäätikkö ja hiihtoalue.", link: "itävalta/Innsbruck.html" },
    { name: "Festung Kufstein", coords: [47.5833, 12.1667], desc: "Kufsteinin linnoitus.", link: "itävalta/Innsbruck.html" },
    { name: "Mittenwald", coords: [47.4422, 11.2642], desc: "Kaunis viulunrakentajakylä Saksassa.", link: "itävalta/Innsbruck.html" },
    { name: "Ötztal-laakso", coords: [47.2343, 10.9856], desc: "Ötztalin alppilaakso ja vesiputous.", link: "itävalta/Innsbruck.html" },
    { name: "Lienz (Schloss Bruck)", coords: [46.8317, 12.7533], desc: "Lienzin museo ja Bruckin linna.", link: "itävalta/Innsbruck.html" },

    // Münchenin kohteet
    { name: "Marienplatz (München)", coords: [48.1372, 11.5755], desc: "Münchenin keskusaukio ja Uusi kaupungintalo.", link: "itävalta/Munich.html" },
    { name: "Englischer Garten", coords: [48.1526, 11.5919], desc: "Münchenin suuri kaupunkipuisto ja surffiaalto.", link: "itävalta/Munich.html" },
    { name: "BMW-museo", coords: [48.1768, 11.5591], desc: "BMW-automuseo ja BMW Welt.", link: "itävalta/Munich.html" },
    { name: "Deutsches Museum", coords: [48.1301, 11.5838], desc: "Maailman suurin tekniikan museo.", link: "itävalta/Munich.html" },
    { name: "Schloss Nymphenburg", coords: [48.1583, 11.5036], desc: "Barokkipalatsi Münchenissä.", link: "itävalta/Munich.html" },
    { name: "Lenbachhaus", coords: [48.1469, 11.5636], desc: "Taidemuseo, joka tunnetaan erityisesti Blaue Reiter -ekspressionistisesta taiteesta.", link: "itävalta/Munich.html" },
    { name: "Bayerisches Nationalmuseum", coords: [48.1431, 11.5910], desc: "Baijerin kansallismuseo – Euroopan taidetta ja taidekäsityötä.", link: "itävalta/Munich.html" },
    { name: "Valentin-Karlstadt-Musäum", coords: [48.1350, 11.5824], desc: "Karl Valentinille omistettu hassuttelumuseo Isartorissa.", link: "itävalta/Munich.html" },
    { name: "Schleißheimin linnat", coords: [48.2486, 11.5606], desc: "Barokkilinnakompleksi Münchenin lähellä.", link: "itävalta/Munich.html" },
    { name: "Dachau keskitysleiri", coords: [48.2700, 11.4682], desc: "Dachaun keskitysleirin muistopaikka.", link: "itävalta/Munich.html" },
    { name: "Freising", coords: [48.4029, 11.7485], desc: "Katedraalikaupunki ja Weihenstephan-panimo.", link: "itävalta/Munich.html" },
    { name: "Luostari Fürstenfeldbruck", coords: [48.1697, 11.2632], desc: "Upea barokkiluostari.", link: "itävalta/Munich.html" },
    { name: "Neuschwanstein & Hohenschwangau", coords: [47.5576, 10.7498], desc: "Kuuluisat linnat Alpeilla.", link: "itävalta/Munich.html" },
    { name: "Linderhofin palatsi", coords: [47.5714, 10.9632], desc: "Kuningas Ludwig II:n palatsi.", link: "itävalta/Munich.html" },
    { name: "Berchtesgaden & Kotkanpesä", coords: [47.6114, 13.0416], desc: "Obersalzberg ja Kotkanpesä.", link: "itävalta/Munich.html" },
    { name: "Grünwaldin linna", coords: [48.0422, 11.5217], desc: "Keskiaikainen linna Münchenin eteläpuolella.", link: "itävalta/Munich.html" },

    // Zell am Seen kohteet
    { name: "Schmittenhöhe", coords: [47.329, 12.738], desc: "Näköalavuori Zell am Seen yllä & Art on the Mountain -ulkoilmataidenäyttely.", link: "itävalta/Zell_am_See.html" },
    { name: "Kaprunin linna", coords: [47.273, 12.762], desc: "Keskiaikainen linna Kaprunissa.", link: "itävalta/Zell_am_See.html" },
    { name: "Kitzsteinhorn", coords: [47.202, 12.686], desc: "Jäätikkö ja Gipfelwelt 3000.", link: "itävalta/Zell_am_See.html" },
    { name: "Kaprun Museum", coords: [47.2725, 12.7592], desc: "Kaprunin paikallishistoriaa ja alppikulttuuria.", link: "itävalta/Zell_am_See.html" },
    { name: "Vötter's Vehicle Museum", coords: [47.2743, 12.7663], desc: "Vötterin automuseo – klassikkoajoneuvoja.", link: "itävalta/Zell_am_See.html" },
    { name: "Kaprunin vuoristopadot (Mooserboden)", coords: [47.168, 12.723], desc: "Suurpatorakennelmat alppimaisemissa.", link: "itävalta/Zell_am_See.html" },
    { name: "Hohenwerfenin linna", coords: [47.4827, 13.1894], desc: "Historiallinen linna ja haukkanäytökset.", link: "itävalta/Zell_am_See.html" },
    { name: "Eisriesenwelt", coords: [47.5028, 13.1897], desc: "Maailman suurin jääluola Werfenissä.", link: "itävalta/Zell_am_See.html" },
    { name: "Grossglocknerin alppitie", coords: [47.083, 12.842], desc: "Panoraamatie alppimaisemissa.", link: "itävalta/Zell_am_See.html" },
    { name: "Gerlos-solatie", coords: [47.241, 12.115], desc: "Upea panoraamatie alppimaisemissa.", link: "itävalta/Zell_am_See.html" },
    { name: "Salzburgin vanhakaupunki", coords: [47.8095, 13.0550], desc: "UNESCO-maailmanperintökohde ja barokkikaupunki.", link: "itävalta/Zell_am_See.html" },
    { name: "Halleinin suolakaivos", coords: [47.667, 13.083], desc: "Historiallinen suolakaivos.", link: "itävalta/Zell_am_See.html" },
    { name: "Saalfelden", coords: [47.4264, 12.8481], desc: "Hiihto- ja vaellusalue.", link: "itävalta/Zell_am_See.html" },
    { name: "Kitzbühel", coords: [47.4464, 12.3917], desc: "Kuuluisan Hahnenkamm-syöksylaskun kaupunki.", link: "itävalta/Zell_am_See.html" },
    { name: "Fügen", coords: [47.3458, 11.8494], desc: "Fügen-Spieljoch alppialue.", link: "itävalta/Zell_am_See.html" },
    { name: "Bad Gastein", coords: [47.1156, 13.1364], desc: "Kylpyläkaupunki ja vesiputous.", link: "itävalta/Zell_am_See.html" }
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
