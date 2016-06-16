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
  Returns Nearest routes details
  * **URL**

    `/busstops/stopnearby/lat/:lat/lon/:lan/rad/2`

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

    `GET`
  * **Data Params**

    ```javascript
    {
    "stopID" : '9235'
    }
    ```

# Implementations
 * https://github.com/tachyons/bmtc
