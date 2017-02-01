# BMTC API

Root url : http://bmtcmob.hostg.in/api

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
Returns Nearest stopes details
* **URL**

  `/busstops/stopnearby/lat/:lat/lon/:lon/rad/2`

* **Method:**

  `GET`

**Search stop**
----
Returns stops matching the query string

* **URL**

  `http://bmtcmob.hostg.in/api/busstops/stopsearch/name/:query`

* **Method**

  `GET`

**Stop details**
---
Returns stop details
* **URL**

  `http://bmtcmob.hostg.in/api/itsstopwise/details`
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

    `http://bmtcmob.hostg.in/api/tripfare/details`
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

    `http://bmtcmob.hostg.in/api/tripdetails/routestop/routeid/:route_id`
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
