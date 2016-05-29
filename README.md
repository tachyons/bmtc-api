# BMTC API
**Route wise details**
----
Returns route wise details
* **URL**

  `/itsroutewise/details`

* **Method:**

  `POST`

<!-- *  **URL Params** -->

   <!-- **Required:** -->

   <!-- `id=[integer]` -->

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
    ["vehicleno:KA01FA1909","routeno:171UP","vehiclelat:12.932159","vehiclelng:77.631950","routeid:30741","serviceid:1","nearestlatlng:12.93673009,77.62652607","start_busstopname:Kempegowda Bus Station","end_busstopname:Koramangala 1st Block","traveldistance:19.704","ETA:0","FARE:22.0","routeorder:31"]]
  ```
* **Error Response:**
  * **Code:** 404 <br />
  **Content:**
  ```javascript
  {"status":false,"message":"Please send required parameters as mentioned in the document"}
  ```
