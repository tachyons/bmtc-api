# BMTC API

Root url : https://bmtcmob.hostg.in/api

**Note:** When using curl, you may encounter an error like `curl: (60) SSL certificate problem: unable to get local issuer certificate`. In such a case use the `--insecure` option to ignore it.

**Stop and Route List**
----
Returns list of stops, chartered stops and routes

* **URL**

  `/busstops/allstop`
  
  `/busstops/charteredstop`
  
  `/routemap/routeno`
  

* **Method:**

  `GET`
  
**Trip Planner (Direct)**
----
Returns list of buses plying directly between given stops

* **URL**

  `/itstrips/direct`
  
* **Method:**
  `POST`
  
* **Data Params**

  ```javascript
  {
  endID : "KR Market"
  salt_value : <32characterhexadecimalstring>
  startID : "Kempegowda Bus Station"    
  }
  ```
  
* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
    
  ```javascript
  [{"vehicleno":"NULL","routeno":"211-B","vehiclelat":"NULL","vehiclelng":"NULL","routeid":"2909","serviceid":"1","nearestlatlng":"NULL","start_busstopname":"Kempegowda Bus Station","end_busstopname":"Somanahalli","traveldistance":"29.581","ETA":"0","FARE":"0","routeorder":"0","start_busstopcord":"12.97867246,77.56985352"},
  {"vehicleno":"NULL","routeno":"213-N","vehiclelat":"NULL","vehiclelng":"NULL","routeid":"3068","serviceid":"1","nearestlatlng":"NULL","start_busstopname":"Kempegowda Bus Station","end_busstopname":"Nettigere","traveldistance":"116.481","ETA":"0","FARE":"0","routeorder":"0","start_busstopcord":"12.97867246,77.56985352"},
  {"vehicleno":"NULL","routeno":"212-D","vehiclelat":"NULL","vehiclelng":"NULL","routeid":"3083","serviceid":"1","nearestlatlng":"NULL","start_busstopname":"Kempegowda Bus Station","end_busstopname":"Agara (Towards Gangasandra)","traveldistance":"24.281","ETA":"0","FARE":"0","routeorder":"0","start_busstopcord":"12.97867246,77.56985352"}
  ...
  ```
  
* **Error Response:**
  * **Code:** 404 <br />
  **Content:**
  
  ```javascript
  []
  ```  
  
**Trip Planner (Indirect)**
----
Returns list of intermediate stops, at which bus should be changed, to travel between two stops without a direct route.

* **URL**

  `/transitroute/transitpoint`
  
* **Method:**
  `POST`
  
* **Data Params**

  ```javascript
  {
  salt_value : <32characterhexadecimalstring>
  endStop : Yeshwanthapura Railway Station                  
  startStop : Kengeri Satellite Town  
  }
  ```
  
* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
    
  ```javascript
  {"start_grp_id":"22349","end_grp_id":"23366","transit_points":
  [{"common_group_id":"16466","common_group_name":"Vijayanagara TTMC","ori_busstop_name":"Kengeri Satellite Town","ori_busstop_lat":"12.92383974","ori_busstop_lang":"77.48494014","ori_transit_busstop_name":"Vijayanagara TTMC","ori_transit_busstop_lat":"12.96551023","ori_transit_busstop_lang":"77.53470719","ori_vehicle":[],"dest_transit_busstop_name":"Vijayanagara TTMC","dest_transit_busstop_lat":"12.96551023","dest_transit_busstop_lang":"77.53470719","dest_busstop_name":"Yeshwanthapura Railway Station","dest_busstop_lat":"13.02176584","dest_busstop_lang":"77.55314268","dest_vehicle":[]},
  {"common_group_id":"19575","common_group_name":"Kempegowda Bus Station","ori_busstop_name":"Kengeri Satellite Town","ori_busstop_lat":"12.92378203","ori_busstop_lang":"77.48497840","ori_transit_busstop_name":"Kempegowda Bus Station","ori_transit_busstop_lat":"12.97750611","ori_transit_busstop_lang":"77.57291257","ori_vehicle":[],"dest_transit_busstop_name":"Kempegowda Bus Station","dest_transit_busstop_lat":"12.97825298","dest_transit_busstop_lang":"77.57081777","dest_busstop_name":"Yeshwanthapura Railway Station","dest_busstop_lat":"13.02339976","dest_busstop_lang":"77.55055099","dest_vehicle":[]},
  ...
  ```
  
**Number of Buses (Indirect)**
----
Returns number of buses available between each end and the intermediate stop

* **URL**

  `/transitroute/transitbuscount`
  
* **Method:**
  `POST`
  
* **Data Params**

  ```javascript
  {
  DestinationTransitname : Yeshwanthapura
  SourceTransitname : Yeshwanthapura
  SourceName : Kengeri Satellite Town
  DestinationName : Yeshwanthapura Railway Station
  salt_value : <32characterhexadecimalstring>
  }
  ```
  
* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
    
  ```javascript
  { 
  "sourceCount": 4,  
  "transitCount": 4 
  }   
  ```
  
**List of Buses (Indirect)**
----
Returns list of buses between each end and the intermediate stop

* **URL**

  `/itstrips/indirect`
  
* **Method:**
  `POST`
  
* **Data Params**

  ```javascript
  {
  salt_value : 4ce2634b63ca9d93dab6940fe1de642d   
  endStop : Yeshwanthapura                  
  startStop : Kengeri Satellite Town  
  }
  ```
  
* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
    
  ```javascript
  {"vehicleno":"KA53F0292","routeno":"401-M","vehiclelat":"12.915822","vehiclelng":"77.481865","serviceid":"1","EtDepart":"166","ETArrive":2617,"routeorder":"7"},
  {"vehicleno":"KA57F2863","routeno":"401-L","vehiclelat":"12.918146","vehiclelng":"77.490822","serviceid":"1","EtDepart":"307","ETArrive":2760,"routeorder":"29"},
  {"vehicleno":"KA01F8982","routeno":"401-MDN","vehiclelat":"12.910482","vehiclelng":"77.483063","serviceid":"1","EtDepart":"600","ETArrive":3054,"routeorder":"4"},
  {"vehicleno":"KA01F4949","routeno":"401-MDN","vehiclelat":"12.914580","vehiclelng":"77.486916","serviceid":"1","EtDepart":9999999,"EtArrive":9999999,"routeorder":"1"},
  ...
  ```
  
**Route wise details**
----
Returns route wise details

* **URL**

  `/itsroutewise/details`

* **Method:**

  `POST`

* **Data Params**

  ```javascript
  {
    direction : "up"
    routeNO : "356CW INFOPL"
  }
  ```

* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
  ```javascript
  [
    ["vehicleno:KA01F4397","routeno:171UP","vehiclelat:12.951280","vehiclelng:77.595207","routeid:30741","serviceid:1","nearestlatlng:12.95140577,77.59521987","start_busstopname:Kempegowda Bus Station","end_busstopname:Koramangala 1st Block","traveldistance:19.704","ETA:0","FARE:22.0","routeorder:19"],
    ["vehicleno:KA01FA1909","routeno:171UP","vehiclelat:12.932159","vehiclelng:77.631950","routeid:30741","serviceid:1","nearestlatlng:12.93673009,77.62652607","start_busstopname:Kempegowda Bus Station","end_busstopname:Koramangala 1st Block","traveldistance:19.704","ETA:0","FARE:22.0","routeorder:31"]
  ]
  ```
* **Error Response:**
  * **Code:** 404 <br />
  **Content:**
  ```javascript
  {"status":false,"message":"Please send required parameters as mentioned in the document"}
  ```

**Route map details**
----
Returns route map details
* **URL**

  `/routemap/details`

* **Method:**

  `POST`
* **Data Params**

    ```javascript
    {
      direction : "up"
      routeNO : "356CW INFOPL"
    }
    ```

* **Success Response:**

    * **Code:** 200 <br />
      **Content:**
    ```javascript
    [
  [
    "vehicleno:KA01FA0959",
    "routeno:340-AUP",
    "vehiclelat:12.891232",
    "vehiclelng:77.625931",
    "routeid:30740",
    "serviceid:1",
    "nearestlatlng:12.91270327,77.63806830",
    "start_busstopname:Kempegowda Bus Station",
    "end_busstopname:Kempegowda Bus Station",
    "traveldistance:27.238",
    "ETA:0",
    "FARE:25.0",
    "routeorder:38"
  ],
  [
    {
      "path": "mtenAsvmxMEzC",
      "distance": "80",
      "latLng": "12.97751447, 77.57178022",
      "stopName": "Kempegowda Bus Station"
    },  
    ...
    ...
    {
      "path": "stenAwqmxMyJO",
      "distance": "210"
    }
  ]
    ```
* **Error Response:**
  * **Code:** 404 <br />
  **Content:**
  ```javascript
  {"status":false,"message":"Please send required parameters as mentioned in the document"}
  ```

**Nearest stop**
---
Returns list of stops nearest to a given coordinate

* **URL**

  `/busstops/stopnearby/lat/:lat/lon/:lon/rad/2`
  
  or
  
  `/busstops/stopname/lat/:lat/lon/:lon/rad/1/format`
  
* **Method:**

  `GET`
 
* **Example**

  `/busstops/stopnearby/lat/12.9809/lon/77.5974/rad/2`
    
  ```javascript
  {
  {"StopId":"12567","StopName":"Cubbon Park Metro Station(towards -GPO)",
  "StopLat":"12.98093983","StopLong":"77.59717248","StopDist":"0.02"},
  {"StopId":"645","StopName":"GPO(towards - Raj Bhavan)",
  "StopLat":"12.98174883","StopLong":"77.59483300","StopDist":"0.18"},
  {"StopId":"587","StopName":"Indian Express(towards - Vidhana Soudha)",
  "StopLat":"12.98347460","StopLong":"77.59634127","StopDist":"0.19"}
  ```
  
**Search stop**
----
Returns list of stops with names matching the query string

* **URL**

  `/busstops/stopsearch/name/:query`

* **Method**

  `GET`

**Stop details**
---
Returns stop details

* **URL**

  `/itsstopwise/details`
* **Method**

  `POST`
* **Data Params**

  ```javascript
    {
    "stopID" : '9234'
    }
    ```

**Trip Fare**
---
Returns trip fare details
* **URL**

    `/tripfare/details`
* **Method**

    `POST`
* **Data Params**

    ```javascript
    {
        'adults' : <no_of_adults>,
        'destination' : <destination>,
        'serviceType' : <service_type>,
        'source' : <source>
    }
    ```
    Service types can be either
  * ordinary
  * vajra
  * vayu_vajra
  * atal_sarige
  * nice_service
  * bengaluru_darshini


**Trip Stops**
----
Returns list of stops on route matching route id
    
* **URL**

    `/tripdetails/routestop/routeid/:route_id`
* **Method**

    `GET`
* **Success Response:**

  * **Code:** 200 <br />
    **Content:**
    
    ```javascript
    [
    {"StopId":"2084","StopName":"Shell Petrol Bunk(towards - Kadugodi Bus Station )","StopLat":"13.01761897","StopLong":"77.76219562","StopDist":"0.02"},
    {"StopId":"2083","StopName":"Shell Petrol Bunk(towards - Hoskote)","StopLat":"13.01772834","StopLong":"77.76208131","StopDist":"0.03"},
    {"StopId":"2049","StopName":"Seegehalli Gate(towards - Hoskote)","StopLat":"13.01344395","StopLong":"77.76104447","StopDist":"0.27"},
    {"StopId":"9469","StopName":"Seegehalli Gate(towards - Seegehalli)","StopLat":"13.01323740","StopLong":"77.76110239","StopDist":"0.29"},
    {"StopId":"2085","StopName":"Seegehalli Gate(towards - Hope Farm)","StopLat":"13.01312693","StopLong":"77.76107313","StopDist":"0.29"},
    {"StopId":"2051","StopName":"Chaithanya Samarpan Apartment(towards - Hoskote)","StopLat":"13.02169602","StopLong":"77.76197046","StopDist":"0.31"},
    {"StopId":"2082","StopName":"Chaithanya Samarpan Apartment(towards - Kadugodi Bus Station )","StopLat":"13.02183505","StopLong":"77.76203544","StopDist":"0.32"},
    {"StopId":"2088","StopName":"Seegehalli(towards - Kadugodi Bus Station )","StopLat":"13.01188920","StopLong":"77.76467509","StopDist":"0.41"},
    {"StopId":"2087","StopName":"Seegehalli(towards - Seegehalli Gate)","StopLat":"13.01163656","StopLong":"77.76479067","StopDist":"0.43"},
    {"StopId":"2080","StopName":"Sai Lakshmi Industries(towards - Hoskote)","StopLat":"13.02441694","StopLong":"77.76162487","StopDist":"0.49"},
    {"StopId":"2081","StopName":"Sai Lakshmi Industries(towards - Kadugodi Bus Station )","StopLat":"13.02447953","StopLong":"77.76174941","StopDist":"0.50"},
    {"StopId":"2078","StopName":"Bevina Mara(towards - Hoskote)","StopLat":"13.02788267","StopLong":"77.76031444","StopDist":"0.74"},
    {"StopId":"7066","StopName":"Chikka Banahalli(towards - Kadugodi Bus Station )","StopLat":"13.01989737","StopLong":"77.75140352","StopDist":"0.75"},
    {"StopId":"2079","StopName":"Bevina Mara(towards - Kadugodi Bus Station )","StopLat":"13.02794748","StopLong":"77.76044967","StopDist":"0.75"},
    {"StopId":"7067","StopName":"Chikka Banahalli(towards - Avalahalli)","StopLat":"13.01984315","StopLong":"77.75134921","StopDist":"0.75"},
    {"StopId":"11415","StopName":"CS-Ardendale Gate Kannamangala Road(towards - Ardendale Gate Kannamangala Road)","StopLat":"13.02691644","StopLong":"77.76731439","StopDist":"0.75"},
    {"StopId":"6344","StopName":"Kannamangala(towards - Kannamangala Gate)","StopLat":"13.02623247","StopLong":"77.76964657","StopDist":"0.80"},
    {"StopId":"6342","StopName":"Kannamangala(towards - Seegehalli)","StopLat":"13.02624227","StopLong":"77.76969686","StopDist":"0.80"},
    {"StopId":"2090","StopName":"Bellathur(towards - Hope Farm)","StopLat":"13.00407373","StopLong":"77.75703659","StopDist":"0.97"},
    {"StopId":"2047","StopName":"Bellathur(towards - Hoskote)","StopLat":"13.00410489","StopLong":"77.75691881","StopDist":"0.97"}
    ]
    ```
    
* **Error Response:**
  * **Code:** 404 <br />
  **Content:**
  
  ```javascript
  {"status":false,"message":"Please send lat and long"}
  ```
        
**Bus Timetable**
---
Returns a timetable of the given bus route
 
* **URL**
   
    `http://bmtcmob.hostg.in/index.php/api/routetiming/timedetails/service/ord/routeno/:route-name`
* **Method**
     
    `GET`   

* **Success Response:**

    * **Code:** 200 <br />
      **Content:**
      
    ```javascript
    [
    {"upRouteName":"Hebbala To Mysore Road Bus Station",
    "downRouteName":"Mysore Road Bus Station To Hebbala"}
    
    [{"busRouteDetailId":"29536","time":"04:00:00"},
    {"busRouteDetailId":"29536","time":"07:05:00"},
    {"busRouteDetailId":"29536","time":"07:40:00"},
    {"busRouteDetailId":"29536","time":"08:05:00"},
    {"busRouteDetailId":"29536","time":"09:50:00"},
    {"busRouteDetailId":"29536","time":"10:30:00"},
    {"busRouteDetailId":"29536","time":"11:20:00"}],
    
    [{"busRouteDetailId":"29537","time":"05:25:00"},
    {"busRouteDetailId":"29537","time":"06:00:00"},
    {"busRouteDetailId":"29537","time":"06:18:00"},
    {"busRouteDetailId":"29537","time":"07:02:00"},
    {"busRouteDetailId":"29537","time":"07:30:00"},
    {"busRouteDetailId":"29537","time":"08:25:00"},
    {"busRouteDetailId":"29537","time":"09:05:00"},
    {"busRouteDetailId":"29537","time":"10:45:00"},
    {"busRouteDetailId":"29537","time":"11:40:00"},
    {"busRouteDetailId":"29537","time":"11:55:00"},
    {"busRouteDetailId":"29537","time":"13:35:00"}]
    ]
    ```
* **Error Response:**
  * **Code:** 404 <br />
  **Content:**
  
  ```javascript
  {"status":false,"message":"Please send required parameters as mentioned in the document"}
  ```



# Implementations
 * https://github.com/tachyons/bmtc
 * https://github.com/tvsijin/bmtc-api-php
 * https://github.com/vineeshnp/bmtc-js-api
 * https://github.com/sreecodeslayer/bmtc-api-python
