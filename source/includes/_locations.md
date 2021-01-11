# Locations

The following endpoints return information regarding Locations. 
It is advised to use this API in order to have a uniform format for addresses.
Country, Region, State, City, Province, and District are the parameters that make up the address format.

## <span class="http-get">GET</span> Get Countries

<div class="center-column"></div>

```
{{base_url}}/locations/countries
```

```json
{
    "total": 5,
    "per_page": 100,
    "current_page": 1,
    "last_page": 1,
    "next_page_url": null,
    "prev_page_url": null,
    "from": 1,
    "to": 5,
    "data": [
        {
            "id": 89844,
            "code": "CN",
            "name": "China",
            "type": "country",
            "parent_id": null,
            "postal_code": null
        },
        {
            "id": 36275,
            "code": "MY",
            "name": "Malaysia",
            "type": "country",
            "parent_id": null,
            "postal_code": null
        },
        {
            "id": 1,
            "code": "PH",
            "name": "Philippines",
            "type": "country",
            "parent_id": null,
            "postal_code": null
        },
        {
            "id": 143413,
            "code": "UK",
            "name": "United Kingdom",
            "type": "country",
            "parent_id": null,
            "postal_code": null
        },
        {
            "id": 36273,
            "code": "US",
            "name": "United States Of America",
            "type": "country",
            "parent_id": null,
            "postal_code": null
        }
    ]
}
```

Returns a list of countries.


## <span class="http-get">GET</span> Get Countries by ID

<div class="center-column"></div>

```
{{base_url}}/locations/countries/{{id}}
```

```json
{
	"id":44295,
	"code":"PH",
	"name":"Philippines",
	"type":"country",
	"parent_id":null,
	"postal_code":null
}
```

Returns a country by ID or the two letter ISO country code (eg. PH,EU,etc.).


## <span class="http-get">GET</span> Get Regions by Country ID

<div class="center-column"></div>

```
{{base_url}}/locations/countries/PH/regions
```

```json
{
   "total":4,
   "per_page":100,
   "current_page":1,
   "last_page":1,
   "next_page_url":null,
   "prev_page_url":null,
   "from":1,
   "to":4,
   "data":[
      {
         "id":1,
         "code":null,
         "name":"Luzon",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      },
      {
         "id":4,
         "code":null,
         "name":"Metro Manila",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      },
      {
         "id":3,
         "code":null,
         "name":"Mindanao",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      },
      {
         "id":2,
         "code":null,
         "name":"Visayas",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      }
   ]
}
```
Returns a list of regions for the given country.


## <span class="http-get">GET</span> Get States by Country ID

<div class="center-column"></div>

```
{{base_url}}/locations/countries/{{id}}/provinces
```

```json
{
   "total":81,
   "per_page":100,
   "current_page":1,
   "last_page":1,
   "next_page_url":null,
   "prev_page_url":null,
   "from":1,
   "to":81,
   "data":[
      {
         "id":5,
         "code":null,
         "name":"Abra",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":1420,
         "code":null,
         "name":"Agusan del Norte",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":2436,
         "code":null,
         "name":"Agusan del Sur",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":336,
         "code":null,
         "name":"Aklan",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":681,
         "code":null,
         "name":"Albay",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":1827,
         "code":null,
         "name":"Antique",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":1686,
         "code":null,
         "name":"Apayao",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":2765,
         "code":null,
         "name":"Aurora",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":5285,
         "code":null,
         "name":"Basilan",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":2925,
         "code":null,
         "name":"Bataan",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":4091,
         "code":null,
         "name":"Batanes",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":5554,
         "code":null,
         "name":"Batangas",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":3176,
         "code":null,
         "name":"Benguet",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":3461,
         "code":null,
         "name":"Biliran",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":4127,
         "code":null,
         "name":"Bohol",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":3602,
         "code":null,
         "name":"Bukidnon",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":6668,
         "code":null,
         "name":"Bulacan",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":8520,
         "code":null,
         "name":"Cagayan",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":9683,
         "code":null,
         "name":"Camarines Norte",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":10469,
         "code":null,
         "name":"Camarines Sur",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":9619,
         "code":null,
         "name":"Camiguin",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":9978,
         "code":null,
         "name":"Capiz",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":11570,
         "code":null,
         "name":"Catanduanes",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":11897,
         "code":null,
         "name":"Cavite",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":7262,
         "code":null,
         "name":"Cebu",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":9370,
         "code":null,
         "name":"Compostela Valley",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":29313,
         "code":null,
         "name":"Cotabato (North Cotabato)",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":13590,
         "code":null,
         "name":"Davao del Norte",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":13054,
         "code":null,
         "name":"Davao del Sur",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":12859,
         "code":null,
         "name":"Davao Oriental",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":12751,
         "code":null,
         "name":"Dinagat Islands",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":13825,
         "code":null,
         "name":"Eastern Samar",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":14446,
         "code":null,
         "name":"Guimaras",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":15643,
         "code":null,
         "name":"Ifugao",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":17776,
         "code":null,
         "name":"Ilocos Norte",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":18357,
         "code":null,
         "name":"Ilocos Sur",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":15830,
         "code":null,
         "name":"Iloilo",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":14550,
         "code":null,
         "name":"Isabela",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":19160,
         "code":null,
         "name":"Kalinga",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":21006,
         "code":null,
         "name":"Laguna",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":21713,
         "code":null,
         "name":"Lanao del Norte",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":22243,
         "code":null,
         "name":"Lanao del Sur",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":23443,
         "code":null,
         "name":"La Union",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":19321,
         "code":null,
         "name":"Leyte",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":25294,
         "code":null,
         "name":"Maguindanao",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":28491,
         "code":null,
         "name":"Marinduque",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":24040,
         "code":null,
         "name":"Masbate",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":25877,
         "code":null,
         "name":"Metro Manila",
         "type":"state",
         "parent_id":4,
         "postal_code":null
      },
      {
         "id":24786,
         "code":null,
         "name":"Misamis Occidental",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":27960,
         "code":null,
         "name":"Misamis Oriental",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":29158,
         "code":null,
         "name":"Mountain Province",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":29875,
         "code":null,
         "name":"Negros Occidental",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":31453,
         "code":null,
         "name":"Negros Oriental",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":32036,
         "code":null,
         "name":"Northern Samar",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":30570,
         "code":null,
         "name":"Nueva Ecija",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":32630,
         "code":null,
         "name":"Nueva Vizcaya",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":24612,
         "code":null,
         "name":"Occidental Mindoro",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":28716,
         "code":null,
         "name":"Oriental Mindoro",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":32921,
         "code":null,
         "name":"Palawan",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":33380,
         "code":null,
         "name":"Pampanga",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":33941,
         "code":null,
         "name":"Pangasinan",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":35493,
         "code":null,
         "name":"Quezon",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":35354,
         "code":null,
         "name":"Quirino",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":36778,
         "code":null,
         "name":"Rizal",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":36981,
         "code":null,
         "name":"Romblon",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":38386,
         "code":null,
         "name":"Samar (Western Samar)",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":37456,
         "code":null,
         "name":"Sarangani",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":39364,
         "code":null,
         "name":"Siquijor",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":39505,
         "code":null,
         "name":"Sorsogon",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":37218,
         "code":null,
         "name":"South Cotabato",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":37866,
         "code":null,
         "name":"Southern Leyte",
         "type":"state",
         "parent_id":2,
         "postal_code":null
      },
      {
         "id":37604,
         "code":null,
         "name":"Sultan Kudarat",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":40748,
         "code":null,
         "name":"Sulu",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":40391,
         "code":null,
         "name":"Surigao del Norte",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":40062,
         "code":null,
         "name":"Surigao del Sur",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":41178,
         "code":null,
         "name":"Tarlac",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":41708,
         "code":null,
         "name":"Tawi-Tawi",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":41923,
         "code":null,
         "name":"Zambales",
         "type":"state",
         "parent_id":1,
         "postal_code":null
      },
      {
         "id":42185,
         "code":null,
         "name":"Zamboanga del Norte",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":42904,
         "code":null,
         "name":"Zamboanga del Sur",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      },
      {
         "id":43712,
         "code":null,
         "name":"Zamboanga Sibugay",
         "type":"state",
         "parent_id":3,
         "postal_code":null
      }
   ]
}
```
Returns a list of states for the given country.


## <span class="http-get">GET</span> Get Cities by Country ID

<div class="center-column"></div>

```
{{base_url}}/locations/countries/PH/cities
```

```json
{
   "total":1634,
   "per_page":100,
   "current_page":1,
   "last_page":17,
   "next_page_url":"http:\/\/api.staging.lbcx.ph\/v1\/locations\/countries\/PH\/cities?page=2",
   "prev_page_url":null,
   "from":1,
   "to":100,
   "data":[
      {
         "id":32936,
         "code":null,
         "name":"Aborlan",
         "type":"city",
         "parent_id":32921,
         "postal_code":null
      },
      {
         "id":24613,
         "code":null,
         "name":"Abra de Ilog",
         "type":"city",
         "parent_id":24612,
         "postal_code":null
      },
      {
         "id":2926,
         "code":null,
         "name":"Abucay",
         "type":"city",
         "parent_id":2925,
         "postal_code":null
      },
      {
         "id":8564,
         "code":null,
         "name":"Abulug",
         "type":"city",
         "parent_id":8520,
         "postal_code":null
      },
      {
         "id":19394,
         "code":null,
         "name":"Abuyog",
         "type":"city",
         "parent_id":19321,
         "postal_code":null
      },
      {
         "id":17777,
         "code":null,
         "name":"Adams",
         "type":"city",
         "parent_id":17776,
         "postal_code":null
      },
      {
         "id":35514,
         "code":null,
         "name":"Agdangan",
         "type":"city",
         "parent_id":35493,
         "postal_code":null
      },
      {
         "id":35355,
         "code":null,
         "name":"Aglipay",
         "type":"city",
         "parent_id":35354,
         "postal_code":null
      },
      {
         "id":34045,
         "code":null,
         "name":"Agno",
         "type":"city",
         "parent_id":33941,
         "postal_code":null
      },
      {
         "id":5575,
         "code":null,
         "name":"Agoncillo",
         "type":"city",
         "parent_id":5554,
         "postal_code":null
      },
      {
         "id":23469,
         "code":null,
         "name":"Agoo",
         "type":"city",
         "parent_id":23443,
         "postal_code":null
      },
      {
         "id":34063,
         "code":null,
         "name":"Aguilar",
         "type":"city",
         "parent_id":33941,
         "postal_code":null
      },
      {
         "id":15675,
         "code":null,
         "name":"Aguinaldo",
         "type":"city",
         "parent_id":15643,
         "postal_code":null
      },
      {
         "id":32956,
         "code":null,
         "name":"Agutaya",
         "type":"city",
         "parent_id":32921,
         "postal_code":null
      },
      {
         "id":15905,
         "code":null,
         "name":"Ajuy",
         "type":"city",
         "parent_id":15830,
         "postal_code":null
      },
      {
         "id":5303,
         "code":null,
         "name":"Akbar",
         "type":"city",
         "parent_id":5285,
         "postal_code":null
      },
      {
         "id":35494,
         "code":null,
         "name":"Alabat",
         "type":"city",
         "parent_id":35493,
         "postal_code":null
      },
      {
         "id":37457,
         "code":null,
         "name":"Alabel",
         "type":"city",
         "parent_id":37456,
         "postal_code":null
      },
      {
         "id":29334,
         "code":null,
         "name":"Alamada",
         "type":"city",
         "parent_id":29313,
         "postal_code":null
      },
      {
         "id":33942,
         "code":null,
         "name":"Alaminos",
         "type":"city",
         "parent_id":33941,
         "postal_code":null
      },
      {
         "id":21007,
         "code":null,
         "name":"Alaminos",
         "type":"city",
         "parent_id":21006,
         "postal_code":null
      },
      {
         "id":19322,
         "code":null,
         "name":"Alangalang",
         "type":"city",
         "parent_id":19321,
         "postal_code":null
      },
      {
         "id":5286,
         "code":null,
         "name":"Al-Barka",
         "type":"city",
         "parent_id":5285,
         "postal_code":null
      },
      {
         "id":19377,
         "code":null,
         "name":"Albuera",
         "type":"city",
         "parent_id":19321,
         "postal_code":null
      },
      {
         "id":4128,
         "code":null,
         "name":"Alburquerque",
         "type":"city",
         "parent_id":4127,
         "postal_code":null
      },
      {
         "id":33982,
         "code":null,
         "name":"Alcala",
         "type":"city",
         "parent_id":33941,
         "postal_code":null
      },
      {
         "id":8585,
         "code":null,
         "name":"Alcala",
         "type":"city",
         "parent_id":8520,
         "postal_code":null
      },
      {
         "id":7328,
         "code":null,
         "name":"Alcantara",
         "type":"city",
         "parent_id":7262,
         "postal_code":null
      },
      {
         "id":36982,
         "code":null,
         "name":"Alcantara",
         "type":"city",
         "parent_id":36981,
         "postal_code":null
      },
      {
         "id":7263,
         "code":null,
         "name":"Alcoy",
         "type":"city",
         "parent_id":7262,
         "postal_code":null
      },
      {
         "id":7272,
         "code":null,
         "name":"Alegria",
         "type":"city",
         "parent_id":7262,
         "postal_code":null
      },
      {
         "id":40392,
         "code":null,
         "name":"Alegria",
         "type":"city",
         "parent_id":40391,
         "postal_code":null
      },
      {
         "id":29314,
         "code":null,
         "name":"Aleosan",
         "type":"city",
         "parent_id":29313,
         "postal_code":null
      },
      {
         "id":11925,
         "code":null,
         "name":"Alfonso",
         "type":"city",
         "parent_id":11897,
         "postal_code":null
      },
      {
         "id":32640,
         "code":null,
         "name":"Alfonso Castaneda",
         "type":"city",
         "parent_id":32630,
         "postal_code":null
      },
      {
         "id":15644,
         "code":null,
         "name":"Alfonso Lista (Potia)",
         "type":"city",
         "parent_id":15643,
         "postal_code":null
      },
      {
         "id":30571,
         "code":null,
         "name":"Aliaga",
         "type":"city",
         "parent_id":30570,
         "postal_code":null
      },
      {
         "id":43713,
         "code":null,
         "name":"Alicia",
         "type":"city",
         "parent_id":43712,
         "postal_code":null
      },
      {
         "id":4157,
         "code":null,
         "name":"Alicia",
         "type":"city",
         "parent_id":4127,
         "postal_code":null
      },
      {
         "id":14611,
         "code":null,
         "name":"Alicia",
         "type":"city",
         "parent_id":14550,
         "postal_code":null
      },
      {
         "id":18358,
         "code":null,
         "name":"Alilem",
         "type":"city",
         "parent_id":18357,
         "postal_code":null
      },
      {
         "id":15831,
         "code":null,
         "name":"Alimodian",
         "type":"city",
         "parent_id":15830,
         "postal_code":null
      },
      {
         "id":5555,
         "code":null,
         "name":"Alitagtag",
         "type":"city",
         "parent_id":5554,
         "postal_code":null
      },
      {
         "id":8611,
         "code":null,
         "name":"Allacapan",
         "type":"city",
         "parent_id":8520,
         "postal_code":null
      },
      {
         "id":32037,
         "code":null,
         "name":"Allen",
         "type":"city",
         "parent_id":32036,
         "postal_code":null
      },
      {
         "id":38387,
         "code":null,
         "name":"Almagro",
         "type":"city",
         "parent_id":38386,
         "postal_code":null
      },
      {
         "id":3462,
         "code":null,
         "name":"Almeria",
         "type":"city",
         "parent_id":3461,
         "postal_code":null
      },
      {
         "id":7338,
         "code":null,
         "name":"Aloguinsan",
         "type":"city",
         "parent_id":7262,
         "postal_code":null
      },
      {
         "id":24787,
         "code":null,
         "name":"Aloran",
         "type":"city",
         "parent_id":24786,
         "postal_code":null
      },
      {
         "id":337,
         "code":null,
         "name":"Altavas",
         "type":"city",
         "parent_id":336,
         "postal_code":null
      },
      {
         "id":27961,
         "code":null,
         "name":"Alubijid",
         "type":"city",
         "parent_id":27960,
         "postal_code":null
      },
      {
         "id":11898,
         "code":null,
         "name":"Amadeo",
         "type":"city",
         "parent_id":11897,
         "postal_code":null
      },
      {
         "id":32631,
         "code":null,
         "name":"Ambaguio",
         "type":"city",
         "parent_id":32630,
         "postal_code":null
      },
      {
         "id":31454,
         "code":null,
         "name":"Amlan (Ayuquitan)",
         "type":"city",
         "parent_id":31453,
         "postal_code":null
      },
      {
         "id":25295,
         "code":null,
         "name":"Ampatuan",
         "type":"city",
         "parent_id":25294,
         "postal_code":null
      },
      {
         "id":8639,
         "code":null,
         "name":"Amulung",
         "type":"city",
         "parent_id":8520,
         "postal_code":null
      },
      {
         "id":37867,
         "code":null,
         "name":"Anahawan",
         "type":"city",
         "parent_id":37866,
         "postal_code":null
      },
      {
         "id":41179,
         "code":null,
         "name":"Anao",
         "type":"city",
         "parent_id":41178,
         "postal_code":null
      },
      {
         "id":4140,
         "code":null,
         "name":"Anda",
         "type":"city",
         "parent_id":4127,
         "postal_code":null
      },
      {
         "id":34004,
         "code":null,
         "name":"Anda",
         "type":"city",
         "parent_id":33941,
         "postal_code":null
      },
      {
         "id":14551,
         "code":null,
         "name":"Angadanan",
         "type":"city",
         "parent_id":14550,
         "postal_code":null
      },
      {
         "id":6669,
         "code":null,
         "name":"Angat",
         "type":"city",
         "parent_id":6668,
         "postal_code":null
      },
      {
         "id":33381,
         "code":null,
         "name":"Angeles City",
         "type":"city",
         "parent_id":33380,
         "postal_code":null
      },
      {
         "id":36779,
         "code":null,
         "name":"Angono",
         "type":"city",
         "parent_id":36778,
         "postal_code":null
      },
      {
         "id":15883,
         "code":null,
         "name":"Anilao",
         "type":"city",
         "parent_id":15830,
         "postal_code":null
      },
      {
         "id":1828,
         "code":null,
         "name":"Anini-y",
         "type":"city",
         "parent_id":1827,
         "postal_code":null
      },
      {
         "id":4173,
         "code":null,
         "name":"Antequera",
         "type":"city",
         "parent_id":4127,
         "postal_code":null
      },
      {
         "id":29381,
         "code":null,
         "name":"Antipas",
         "type":"city",
         "parent_id":29313,
         "postal_code":null
      },
      {
         "id":36790,
         "code":null,
         "name":"Antipolo",
         "type":"city",
         "parent_id":36778,
         "postal_code":null
      },
      {
         "id":33415,
         "code":null,
         "name":"Apalit",
         "type":"city",
         "parent_id":33380,
         "postal_code":null
      },
      {
         "id":8521,
         "code":null,
         "name":"Aparri",
         "type":"city",
         "parent_id":8520,
         "postal_code":null
      },
      {
         "id":32922,
         "code":null,
         "name":"Araceli",
         "type":"city",
         "parent_id":32921,
         "postal_code":null
      },
      {
         "id":29352,
         "code":null,
         "name":"Arakan",
         "type":"city",
         "parent_id":29313,
         "postal_code":null
      },
      {
         "id":33428,
         "code":null,
         "name":"Arayat",
         "type":"city",
         "parent_id":33380,
         "postal_code":null
      },
      {
         "id":7282,
         "code":null,
         "name":"Argao",
         "type":"city",
         "parent_id":7262,
         "postal_code":null
      },
      {
         "id":23444,
         "code":null,
         "name":"Aringay",
         "type":"city",
         "parent_id":23443,
         "postal_code":null
      },
      {
         "id":32647,
         "code":null,
         "name":"Aritao",
         "type":"city",
         "parent_id":32630,
         "postal_code":null
      },
      {
         "id":24041,
         "code":null,
         "name":"Aroroy",
         "type":"city",
         "parent_id":24040,
         "postal_code":null
      },
      {
         "id":13826,
         "code":null,
         "name":"Arteche",
         "type":"city",
         "parent_id":13825,
         "postal_code":null
      },
      {
         "id":34023,
         "code":null,
         "name":"Asingan",
         "type":"city",
         "parent_id":33941,
         "postal_code":null
      },
      {
         "id":15665,
         "code":null,
         "name":"Asipulo",
         "type":"city",
         "parent_id":15643,
         "postal_code":null
      },
      {
         "id":7354,
         "code":null,
         "name":"Asturias",
         "type":"city",
         "parent_id":7262,
         "postal_code":null
      },
      {
         "id":13591,
         "code":null,
         "name":"Asuncion (Saug)",
         "type":"city",
         "parent_id":13590,
         "postal_code":null
      },
      {
         "id":35527,
         "code":null,
         "name":"Atimonan",
         "type":"city",
         "parent_id":35493,
         "postal_code":null
      },
      {
         "id":3177,
         "code":null,
         "name":"Atok",
         "type":"city",
         "parent_id":3176,
         "postal_code":null
      },
      {
         "id":14646,
         "code":null,
         "name":"Aurora",
         "type":"city",
         "parent_id":14550,
         "postal_code":null
      },
      {
         "id":42905,
         "code":null,
         "name":"Aurora",
         "type":"city",
         "parent_id":42904,
         "postal_code":null
      },
      {
         "id":31463,
         "code":null,
         "name":"Ayungon",
         "type":"city",
         "parent_id":31453,
         "postal_code":null
      },
      {
         "id":10470,
         "code":null,
         "name":"Baao",
         "type":"city",
         "parent_id":10469,
         "postal_code":null
      },
      {
         "id":19458,
         "code":null,
         "name":"Babatngon",
         "type":"city",
         "parent_id":19321,
         "postal_code":null
      },
      {
         "id":682,
         "code":null,
         "name":"Bacacay",
         "type":"city",
         "parent_id":681,
         "postal_code":null
      },
      {
         "id":17779,
         "code":null,
         "name":"Bacarra",
         "type":"city",
         "parent_id":17776,
         "postal_code":null
      },
      {
         "id":4227,
         "code":null,
         "name":"Baclayon",
         "type":"city",
         "parent_id":4127,
         "postal_code":null
      },
      {
         "id":23519,
         "code":null,
         "name":"Bacnotan",
         "type":"city",
         "parent_id":23443,
         "postal_code":null
      },
      {
         "id":28717,
         "code":null,
         "name":"Baco",
         "type":"city",
         "parent_id":28716,
         "postal_code":null
      },
      {
         "id":21714,
         "code":null,
         "name":"Bacolod",
         "type":"city",
         "parent_id":21713,
         "postal_code":null
      },
      {
         "id":29876,
         "code":null,
         "name":"Bacolod City",
         "type":"city",
         "parent_id":29875,
         "postal_code":null
      },
      {
         "id":22315,
         "code":null,
         "name":"Bacolod-Kalawi (Bacolod Grande)",
         "type":"city",
         "parent_id":22243,
         "postal_code":null
      },
      {
         "id":33459,
         "code":null,
         "name":"Bacolor",
         "type":"city",
         "parent_id":33380,
         "postal_code":null
      },
      {
         "id":31488,
         "code":null,
         "name":"Bacong",
         "type":"city",
         "parent_id":31453,
         "postal_code":null
      }
   ]
}
```
Returns a list of cities for the given country.


## <span class="http-get">GET</span> Get Region by ID

<div class="center-column"></div>

```
{{base_url}}/locations/regions/{{id}}
```

```json
{
   "total":4,
   "per_page":100,
   "current_page":1,
   "last_page":1,
   "next_page_url":null,
   "prev_page_url":null,
   "from":1,
   "to":4,
   "data":[
      {
         "id":1,
         "code":null,
         "name":"Luzon",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      },
      {
         "id":4,
         "code":null,
         "name":"Metro Manila",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      },
      {
         "id":3,
         "code":null,
         "name":"Mindanao",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      },
      {
         "id":2,
         "code":null,
         "name":"Visayas",
         "type":"region",
         "parent_id":44295,
         "postal_code":null
      }
   ]
}
```
Returns a region by ID.


## <span class="http-get">GET</span> Get Provinces by Region ID

<div class="center-column"></div>

```
{{base_url}}/locations/regions/{{id}}/provinces
```

```json
{
   "total":17,
   "per_page":100,
   "current_page":1,
   "last_page":1,
   "next_page_url":null,
   "prev_page_url":null,
   "from":1,
   "to":17,
   "data":[
      {
         "id":25878,
         "code":null,
         "name":"Caloocan City",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":26070,
         "code":null,
         "name":"Las Pinas",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":26131,
         "code":null,
         "name":"Makati",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":26279,
         "code":null,
         "name":"Malabon",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":26097,
         "code":null,
         "name":"Mandaluyong",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":26302,
         "code":null,
         "name":"Manila",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27272,
         "code":null,
         "name":"Marikina",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27290,
         "code":null,
         "name":"Muntinlupa",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27305,
         "code":null,
         "name":"Navotas",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27404,
         "code":null,
         "name":"Paranaque City",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27444,
         "code":null,
         "name":"Pasay City",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27321,
         "code":null,
         "name":"Pasig City",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27433,
         "code":null,
         "name":"Pateros",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27662,
         "code":null,
         "name":"Quezon City",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27857,
         "code":null,
         "name":"San Juan",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27890,
         "code":null,
         "name":"Taguig City",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      },
      {
         "id":27923,
         "code":null,
         "name":"Valenzuela",
         "type":"city",
         "parent_id":25877,
         "postal_code":null
      }
   ]
}
```
Returns a list of provinces for the given region.


## <span class="http-get">GET</span> Get Province by ID

<div class="center-column"></div>

```
{{base_url}}/locations/provinces/{{id}}
```

```json
{
   "id":5554,
   "code":null,
   "name":"Batangas",
   "type":"state",
   "parent_id":1,
   "postal_code":null
}
```
Returns a state/province by ID.


## <span class="http-get">GET</span> Get Cities by Province ID

<div class="center-column"></div>

```
{{base_url}}/locations/provinces/18130/cities
```

```json
{
    "total": 4,
    "per_page": 100,
    "current_page": 1,
    "last_page": 1,
    "next_page_url": null,
    "prev_page_url": null,
    "from": 1,
    "to": 4,
    "data": [
        {
            "id": 18131,
            "code": null,
            "name": "Bangued",
            "type": "city",
            "parent_id": 18130,
            "postal_code": null
        },
        {
            "id": 18146,
            "code": null,
            "name": "Pidigan",
            "type": "city",
            "parent_id": 18130,
            "postal_code": null
        },
        {
            "id": 18156,
            "code": null,
            "name": "San Quintin",
            "type": "city",
            "parent_id": 18130,
            "postal_code": null
        },
        {
            "id": 18160,
            "code": null,
            "name": "Tayum",
            "type": "city",
            "parent_id": 18130,
            "postal_code": null
        }
    ]
}
```
Returns a list of cities for the given province.


## <span class="http-get">GET</span> Get City by ID

<div class="center-column"></div>

```
{{base_url}}/locations/cities/79
```

```json
{
   "id":79,
   "code":null,
   "name":"Dolores",
   "type":"city",
   "parent_id":5,
   "postal_code":null
}
```
Returns a city by ID.


## <span class="http-get">GET</span> Get District by City ID

<div class="center-column"></div>

```
{{base_url}}/locations/cities/79/districts
```

```json
{
   "total":15,
   "per_page":100,
   "current_page":1,
   "last_page":1,
   "next_page_url":null,
   "prev_page_url":null,
   "from":1,
   "to":15,
   "data":[
      {
         "id":80,
         "code":null,
         "name":"Bayaan",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":81,
         "code":null,
         "name":"Cabaroan",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":82,
         "code":null,
         "name":"Calumbaya",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":83,
         "code":null,
         "name":"Cardona",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":84,
         "code":null,
         "name":"Isit",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":85,
         "code":null,
         "name":"Kimmalaba",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":86,
         "code":null,
         "name":"Libtec",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":87,
         "code":null,
         "name":"Lub-lubba",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":88,
         "code":null,
         "name":"Mudiit",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":89,
         "code":null,
         "name":"Namit-ingan",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":90,
         "code":null,
         "name":"Pacac",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":91,
         "code":null,
         "name":"Poblacion",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":92,
         "code":null,
         "name":"Salucag",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":93,
         "code":null,
         "name":"Talogtog",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      },
      {
         "id":94,
         "code":null,
         "name":"Taping",
         "type":"district",
         "parent_id":79,
         "postal_code":"2801"
      }
   ]
}
```
Returns a list of districts for the given city.


## <span class="http-get">GET</span> Get District by ID

<div class="center-column"></div>

```
{{base_url}}/locations/district/107
```

```json
{
   "id":107,
   "code":null,
   "name":"Poblacion",
   "type":"district",
   "parent_id":103,
   "postal_code":"2824"
}
```
Returns a district by ID.



