# Locations

The following endpoints return information regarding Locations. 
It is advised to use this API in order to have a uniform format for addresses.
Country, Region, State, City, Province, and District are the parameters that make up the address format.

## Get Countries

<div class="center-column"></div>

```
{{base_url}}/locations/countries
```

```
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

