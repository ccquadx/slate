# AWB Printing
Endpoints for developers for generating pdf files of AWB/POD labels for printing.

## <span class="http-get">GET</span> AWB Label Single Print

<div class="center-column"></div>
```
{{base_url}}/print/awb/{{tracking_number}}?type=zebra
```

Gets a single pdf of the requested label. Tracking Number is required, along with the queried type (zebra or fuji).

### Request Headers ###

<b> Authorization: </b> `{{authorization}}`


### Request Params ###

<b> type: </b> `zebra` (valid values are `zebra` or `fuji`)

The header is the first part of the token where the token type (typ) and hashing algorithm (alg) used to generate the signature are defined. Only `HMAC SHA256` is supported at the moment.

### Example Response ###

<div class="center-column"></div>

```json
{
  "success": true,
  "message": {
    "tracking_number": "0570-6897-BHWJ",
    "date_pickup_at": "2020-11-26",
    "estimated_delivery_date": "2020-11-29",
    "pickup_hub": "NTH",
    "pickup_hub_zone": "Z112",
    "delivery_hub": "NTH",
    "awb": "https://s3.ap-southeast-1.amazonaws.com/awbpod.staging.quadx.xyz/zebra/AWB-0570-6897-BHWJ.pdf?AWSAccessKeyId=ASIA3SHA62V66MEVV67I&Expires=1606439747&Signature=G4POeYpI72XC3IfZgEEhpZmm6e4%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEIH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgGQJ4AOp%2FvJcvJr5gjJa0db1GjYb%2FuxUX39590FuRktECIQCjsu1QZ4l2o%2FELYrcDOf3m79xzT7aSSzRhO7zfvHY5Jir1AQj6%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDc5NTA0MDczMjU0MSIM2TkFDCXQoHp7pyhEKskBQ86QhdH9wSh%2FZfEQ90oslEskIZHc3LX7BE%2F2AuaLZ%2BB%2FnVWpFub1A6Z%2FwU31lR%2BLyvOk4uqyUXu8tpMHY8BjqXDlmxdMo%2BIqlk%2FFE1PArWf9BzYaq2%2BJD8XFlFlpugx22TG6HfLEgi1sGqXfsA%2FTFziEVgMAbBzPVCZgt7GXu4fmb5T4g9MyGgtbM6oDVfdEeJyIuZe3Wwdt8kbdBb76aZiT8EQCuPQp%2BaPOgqCA3Xz2C5XcHUtZzq08Lp3zzulJxgMIwwfIXKzUMLmD%2FP0FOuABm8jIBSLXzCx1q5Tk%2BbsdDh%2FtNOUGmnah4P6%2F%2BXBgUObdzSFqaVKyBfYZ4C1djBxwFQT5B5wd3L%2BC7nS64d0uXTlJhthCeqepy2wWWQFynQVFGwfATlJ98Xst7nn4K8wbFnDi%2B%2BRIPRkh%2B1w83McLZJKhUSKpxomF96Vp7WgNVG3yBVTykifK04shNWTKvTfs0uUDNHF1%2F74rxJOC2%2B7LJXeYpf3A1dXMGRdPcpvF0E6bWjN9o62Al0HHmoA0gB5vorDcLrbAGuWsbvGDl8EmZrHPrpq%2FPUUSWNArX5HH0W4%3D"
	}
}
```


## <span class="http-get">POST</span> AWB Label Bulk Print

<div class="center-column"></div>
```
{{base_url}}/print/awb?type=zebra
```

Gets a single pdf of the requested label. Tracking Number is required, along with the queried type (zebra or fuji).

### Request Headers ###

<b> Authorization: </b> `{{authorization}}`


### Request Params ###

<b> type: </b> `zebra`

### Example Request ###

<div class="center-column"></div>

> Example Request

```json
{
  "tracking_number": [
    "0248-8053-WMHB"
  ]
}
```
> Example Response

```json
{
    "pollUrl": "https://api.staging.quadx.xyz/v1/print/awb/poll/1606353498666",
    "success": true,
    "id": 1606353498666,
    "numOfBatches": 1,
    "message": null
}
```


## <span class="http-get">GET</span> Poll URL for Bulk Print

<div class="center-column"></div>
```
{{base_url}}/print/awb/poll/{{awb_poll_id}}
```

Gets a single pdf of the requested label. Tracking Number is required, along with the queried type (zebra or fuji).

### Request Headers ###

<b> Authorization: </b> `{{authorization}}`

> Example Response

```json
[
    {
        "batchgroupid": "1606353498666",
        "labelType": "awb",
        "sequence": 1,
        "batchid": "1606353498666-1-awb",
        "printer": "zebra",
        "status": "done",
        "file": "awb-1606353498666-1-of-1.pdf",
        "url": "https://s3.ap-southeast-1.amazonaws.com/awbpod.staging.quadx.xyz/batch/awb-1606353498666-1-of-1.pdf?AWSAccessKeyId=ASIA3SHA62V67NF5ICXL&Expires=1606439922&Signature=Up6ca68qwr9daLGYjdJ20cgaXWY%3D&x-amz-security-token=IQoJb3JpZ2luX2VjEIH%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkYwRAIgWXLf4bHhf%2BzpbygCmYJkCEPNrUf7qMhkAQNUyNCnKZsCIEjvF%2BWWR3Ad9x076NMm8zERx5INOxwJ5AkBgOzEp7%2BWKvYBCPr%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQARoMNzk1MDQwNzMyNTQxIgyUoZL3K6P1ucoUISgqygHTOajkUlavUW%2F%2FUAOHH3WItWkTyBu5odQJ5FindW00Vw93GvfrfT49CcIjwtcyTv2r4Lf%2BuaQL15SEmxwy5oVK%2FIzOGpU9oX27f%2BLjScDllADGF73fxFPROMfo0N5bcD1Oa3zMR%2FYvYfk91z%2Fb7dDtarJ2UiO12FVr0MnBBKM0z1QNwogJKRJXt2z2A5C7%2FNBiHePqUooFXmYykQIMPfiT0oNe%2F0mZzNFqiGs1MNx7lq1ZN1Jo2vIhR5ccdXaGx7WyxhVmPoceZzROMPCE%2FP0FOuEBbjv6RGg2rTMmBDc5LszuvgJlAPnKE9TAxH2djW68DOOqsvcGQn%2Ftu3cpnP8v0ON3rOdv8%2FPH0F3WqxIxFRcsF4dAMqoOPI1KJ47hKrspy%2FCv4rP0BeeEUkhCVmWJQ9JVn7TfKWKsES6DPqx3TLB82T%2Bfj6luV14Wjo7qQhKqgxuoE2WfR3uzdGU%2BPHIgHVrWNVe8J1NhT9KXRFtLRk2k6hEuYJ4lcoOP1evWOBN6HJtI%2FcOl7MCKyfn6RgoAYiSY7MgvBI1%2B8M72n3lOPXHOMM4H0PMyjoox6bLlrD5yG6aR"
    }
]
```


<p style="text-align:center;"><img src="https://i.imgur.com/LkBPnbV.png" class='small'/></p>


