<html>
<head>
  <meta charset="utf-8" />
  <title>APARTMENT MAP</title>
  <meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no" />

  <!-- Load Leaflet from CDN -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css"
  integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ=="
  crossorigin=""/>
  <script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js"
  integrity="sha512-gZwIG9x3wUXg2hdXF6+rVkLF/0Vi9U8D2Ntg4Ga5I5BZpVkVxlJWbSQtXPSiUTtC0TjtGOmxa1AJPuV0CPthew=="
  crossorigin=""></script>


  <!-- Load Esri Leaflet from CDN -->
  <script src="https://unpkg.com/esri-leaflet@2.3.3/dist/esri-leaflet.js"
  integrity="sha512-cMQ5e58BDuu1pr9BQ/eGRn6HaR6Olh0ofcHFWe5XesdCITVuSBiBZZbhCijBe5ya238f/zMMRYIMIIg1jxv4sQ=="
  crossorigin=""></script>




  <!-- Load Leaflet MarkerCluster and Esri Leaflet Cluster from CDN -->
  <link rel="stylesheet" type="text/css"
    href="https://unpkg.com/leaflet.markercluster@1.4.1/dist/MarkerCluster.Default.css"
    integrity="sha512-BBToHPBStgMiw0lD4AtkRIZmdndhB6aQbXpX7omcrXeG2PauGBl2lzq2xUZTxaLxYz5IDHlmneCZ1IJ+P3kYtQ=="
    crossorigin="">
  <link rel="stylesheet" type="text/css" href="https://unpkg.com/leaflet.markercluster@1.4.1/dist/MarkerCluster.css"
    integrity="sha512-RLEjtaFGdC4iQMJDbMzim/dOvAu+8Qp9sw7QE4wIMYcg2goVoivzwgSZq9CsIxp4xKAZPKh5J2f2lOko2Ze6FQ=="
    crossorigin="">
  <script src="https://unpkg.com/leaflet.markercluster@1.4.1/dist/leaflet.markercluster.js"
    integrity="sha512-MQlyPV+ol2lp4KodaU/Xmrn+txc1TP15pOBF/2Sfre7MRsA/pB4Vy58bEqe9u7a7DczMLtU5wT8n7OblJepKbg=="
    crossorigin=""></script>
  <script src="https://unpkg.com/esri-leaflet-cluster@2.0.1/dist/esri-leaflet-cluster.js"
    integrity="sha512-2/Nwrks+A2omjKeWrF4TKFLIrUbAhSl8EDEm6xunuwXXYqMoJI71PZtlW0/vqt9d3DOyP1md/bzAnNH2KuAhaQ=="
    crossorigin=""></script>

  <style>
    body { margin:0; padding:0; }
    #map { position: absolute; top:0; bottom:0; right:0; left:0; }
  </style>
</head>
<body>

<style>
  .cluster {
    background: #2d84c8;
    border-radius: 50%;
    text-align: center;
    color: white;
    font-weight: 700;
    border: 1px solid #2d84c8;
    font-family: monospace;
  }

  .cluster:before {
    content: ' ';
    position: absolute;
    border-radius: 50%;
    z-index: -1;
    top: 1px;
    left: 1px;
    right: 1px;
    bottom: 1px;
    border: 1px solid white;
  }

  .digits-1 {
    font-size: 14px;
    height: 28px;
    width: 28px;
    line-height: 28px;
    margin-top: -14px;
    margin-left: -14px;
  }

  .digits-2 {
    font-size: 16px;
    height: 34px;
    width: 34px;
    line-height: 35px;
    margin-top: -17px;
    margin-left: -17px;
  }

  .digits-2:before {
    border-width: 2px;
  }

  .digits-3 {
    font-size: 18px;
    height: 48px;
    width: 47px;
    line-height: 47px;
    border-width: 3px;
    margin-top: -24px;
    margin-left: -24px;
  }

  .digits-3:before {
    border-width: 3px;
  }

  .digits-4 {
    font-size: 18px;
    height: 58px;
    width: 58px;
    line-height: 57px;
    border-width: 4px;
    margin-top: -29px;
    margin-left: -29px;
  }

  .digits-4:before {
    border-width: 4px;
  }
</style>

<div id="map"></div>

    <script>
var markers = [
  {
    "name":"An Binh City",
    "city":"Goroka, Papua New Guinea",
    "iata_faa":"GKA",
    "icao":"AYGA",
    "lat":21.050269,
    "lng":105.779182,
    "alt":5282,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"Chung Cu C1 - C2 Xuan Dinh",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.070436,
    "lng":105.791523,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"CT3 Co Nhue",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.050844,
    "lng":105.786173,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"Goldmark City",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.043421,
    "lng":105.767855,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"Green Stars",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.052203,
    "lng":105.780868,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"Hanhud Hoang Quoc Viet",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.047067,
    "lng":105.786543,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"test1",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.047087,
    "lng":105.788543,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  },{
    "name":"test3",
    "city":"Madang, Papua New Guinea",
    "iata_faa":"MAG",
    "icao":"AYMD",
    "lat":21.049087,
    "lng":105.798543,
    "alt":20,
    "tz":"Pacific/Port_Moresby"
  }
];
</script>

<script>
var map = L.map( 'map', {
  center: [21.052203, 105.780868],
  minZoom: 2,
  zoom: 13
});
//api key and map style here 
L.tileLayer( 'https://api.maptiler.com/maps/streets/{z}/{x}/{y}.png?key=XDzNX0JCRQPYWEUXDDxM', {
 attribution: '&copy; <a href=”<a href="https://www.maptiler.com/copyright/" target="_blank">&copy; MapTiler</a> <a href="https://www.openstreetmap.org/copyright" target="_blank">&copy; OpenStreetMap contributors</a>”>OpenStreetMap</a> contributors',
 subdomains: ['a','b','c']
}).addTo( map );
 

 
var myIcon = L.icon({
  iconUrl: 'https://4.bp.blogspot.com/-NI_7HK9mcbA/W-KoaBBzn-I/AAAAAAAAAZQ/kNHeKbXkaHQGbvMN6fRrJT9WkyvQuO6NwCLcBGAs/s1600/x25.png',
  iconRetinaUrl: 'https://4.bp.blogspot.com/-NI_7HK9mcbA/W-KoaBBzn-I/AAAAAAAAAZQ/kNHeKbXkaHQGbvMN6fRrJT9WkyvQuO6NwCLcBGAs/s1600/x25.png',
  iconSize: [23, 30],
  iconAnchor: [9, 21],
  popupAnchor: [0, -14]
});
var markerClusters = L.markerClusterGroup();
 
for ( var i = 0; i < markers.length; ++i )
{
  var popup = markers[i].name +
              '<br/>' + markers[i].city +
              '<br/><b>IATA/FAA:</b> ' + markers[i].iata_faa +
              '<br/><b>ICAO:</b> ' + markers[i].icao +
              '<br/><b>Altitude:</b> ' + Math.round( markers[i].alt * 0.3048 ) + ' m' +
              '<br/><b>Timezone:</b> ' + markers[i].tz;
 
  var m = L.marker( [markers[i].lat, markers[i].lng], {icon: myIcon} )
                  .bindPopup( popup );
 
  markerClusters.addLayer( m );
}
 
map.addLayer( markerClusters );
</script>
  </body>
</html>