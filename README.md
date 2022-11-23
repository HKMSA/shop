# **HKMSA SHOP**

- [**HKMSA SHOP**](#hkmsa-shop)
  - [**Available query parameters**](#available-query-parameters)
    - [**Sample query**](#sample-query)
  - [**API**](#api)
    - [**Get products**](#get-products)
    - [**Get single product**](#get-single-product)
    - [**Get wishlist**](#get-wishlist)
    - [**Add to wishlist**](#add-to-wishlist)
    - [**Remove from wishlist**](#remove-from-wishlist)
    - [**Get listings**](#get-listings)
    - [**Get single listing**](#get-single-listing)
    - [**Create a listing**](#create-a-listing)
    - [**Update listing**](#update-listing)
    - [**Delete listing**](#delete-listing)
  - [**Important developer Notes**](#important-developer-notes)
  
---

## **Available query parameters**

| Name | Type | Param | Values |
| ------- | ------- | ------- | ------- |
| Category | str | category | Bags, Apparel, Furniture, ElectricalAppliances |
| Condition | str | condition | BrandNew, LikeNew, Used |
| Status | str | status | Available, Reserved, Sold |
| Delivery option | str | deliveryOption | MeetUp, Delivery |
| Sort by | str | sort | recent, price |
| Ascending | bool | asc | True, False |
| Min price | int | minPrice | *integer value* |
| Max price | int | maxPrice | *integer value* |
| Limit | int | limit | *integer value* |
| Offset | int | offset | *integer value* |

### **Sample query**
Get all Bags and Furniture that are BrandNew or Used, sort by price:
http://api-dev.thehkmsa.com/products?category=Bags|Furniture&condition=BrandNew|Used&sort=price&asc=True

---

## **API**

---

### **Get products**

- **Description**

    Get all products on sale. Sort and filter with query parameters, using pipe delimiter '|' or %7C

- **Endpoint**

    `/products`
  
- **Request Method:**
  
    `GET`

- **Visibility**

    Public

- **Parameters**

    Query string

    | Name | Type | Example |
    | ----------- | ----------- | ----------- |
    | Category | str | ?category=Bags\|Apparel |
    | Condition | str | ?condition=BrandNew |
    | Status | str | status | ?status=Available |
    | Delivery option | str | ?deliveryOption=MeetUp |
    | Sort by | str | ?sort=recent |
    | Ascending | bool | ?asc=True |
    | Min price | int | ?minPrice=69 |
    | Max price | int | ?maxPrice=420 |
    | Limit | int | ?limit=6 |
    | Offset | int | ?offset=6 |

- **Responses**

    `200 OK`

    ```JSON
    {
        "message" : "Successful",
        "data" : [
            {
                "id": str,
                "hashID": str,
                "memberID": int,
                "status": str,
                "category": str,
                "name": str,
                "description": str,
                "condition": str,
                "price": float,
                "deliveryOption": str,
                "location": str,
                "createdAt": datetime,
                "imagePath": list,
                "isDraft": bool,
                "contact": str
            },
        ]
    }
    ```

    `404 NOT FOUND`

    ```JSON
    {
        "message" : "Not Found",
        "data" : []
    }
    ```
    
    `422 Unprocessable Entity`

---

### **Get single product**

- **Description**
  
    Get single product page (by hash)

- **Endpoint**
  
    `/products/{hash}`

- **Request Method**

    `GET`

- **Visiblity**

    Public

- **Parameters**

    Path parameter

    | Name | Type | Description |
    |-----|-----|-----|
    | hash | str | the hash of a product

- **Responses**

    `200 OK`

    ```JSON
    {
        "message" : "Successful",
        "data": {
            "id": str,
            "hashID": str,
            "memberID": int,
            "status": str,
            "category": str,
            "name": str,
            "description": str,
            "condition": str,
            "price": float,
            "deliveryOption": str,
            "location": str,
            "createdAt": datetime,
            "imagePath": list,
            "isDraft": bool,
            "contact": str
        },
    }
    ```

    `404 NOT FOUND`

    ```JSON
    {
        "message" : "Not found",
        "data" : {}
    }
    ```

---

### **Get wishlist**

- **Description**

    Get all products in a member's wishlist (wishlist with a member's ID). Sort and filter with query parameters, using pipe delimiter %7C

- **Endpoint**
  
    `/wishlist`

- **Request Method**

    `GET`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    Query string

    | Name | Type | Example |
    | ----------- | ----------- | ----------- |
    | Category | str | ?category=Bags |
    | Condition | str | ?condition=BrandNew |
    | Status | str | status | ?status=Available |
    | Delivery option | str | ?deliveryOption=MeetUp |
    | Sort by | str | ?sort=recent |
    | Ascending | bool | ?asc=True |
    | Min price | int | ?minPrice=69 |
    | Max price | int | ?maxPrice=420 |
    | Limit | int | ?limit=6 |
    | Offset | int | ?offset=6 |

- **Responses**

    `200 OK`

    ```JSON
    {
        "message" : "Successful",
        "data" : [
            {
                "id": str,
                "hashID": str,
                "memberID": int,
                "status": str,
                "category": str,
                "name": str,
                "description": str,
                "condition": str,
                "price": float,
                "deliveryOption": str,
                "location": str,
                "createdAt": datetime,
                "imagePath": list,
                "isDraft": bool,
                "contact": str
            },
        ]
    }
    ```

    `403 FORBIDDEN`

    `404 NOT FOUND`

    ```JSON
    {
        "message" : "Not found",
        "data" : []
    }
    ```
    
    `422 Unprocessable Entity`

---

### **Add to wishlist**

- **Description**

    Add a product to a member's wishlist

- **Endpoint**
  
    `/wishlist/{hash}`

- **Request Method**

    `POST`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    Path parameter

    | Name | Type | Description |
    |-----|-----|-----|
    | hash | str | the hash of a product

- **Responses**

    `204 NO CONTENT`

    `400 BAD REQUEST`

    ```JSON
    {
        "message": "Error message"
    }
    ```

    `403 FORBIDDEN`

---

### **Remove from wishlist**

- **Description**

    Delete a product from a member's wishlist

- **Endpoint**
  
    `/wishlist/{hash}`

- **Request Method**

    `DELETE`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    Path parameter

    | Name | Type | Description |
    |-----|-----|-----|
    | hash | str | the hash of a product

- **Responses**

    `204 NO CONTENT`

    `400 BAD REQUEST`

    ```JSON
    {
        "message": "Error message"
    }
    ```

    `403 FORBIDDEN`

---

### **Get listings**

- **Description**

    Get a members's listings or drafts (get all products with member's ID). Sort and filter with query parameters, using pipe delimiter %7C

- **Endpoint**
  
    `/listings`

- **Request Method**

    `GET`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    Query string

    | Name | Type | Example |
    | ----------- | ----------- | ----------- |
    | Category | str | ?category=bags |
    | Condition | str | ?condition=BrandNew |
    | Status | str | status | ?status=Available |
    | Delivery option | str | ?deliveryOption=MeetUp |
    | Sort by | str | ?sort=recent |
    | Ascending | bool | ?asc=True |
    | isDraft | bool | ?isDraft=True |
    | Min price | int | ?minPrice=69 |
    | Max price | int | ?maxPrice=420 |
    | Limit | int | ?limit=6 |
    | Offset | int | ?offset=6 |

- **Responses**

    `200 OK`

    ```JSON
    {
        "message": "successful",
        "data": [
            {
                "id": str,
                "hashID": str,
                "memberID": int,
                "status": str,
                "category": str,
                "name": str,
                "description": str,
                "condition": str,
                "price": float,
                "deliveryOption": str,
                "location": str,
                "createdAt": datetime,
                "imagePath": list,
                "isDraft": bool,
                "contact": str
            },
        ]
    }
    ```

    `403 FORBIDDEN`

    `404 NOT FOUND`

    ```JSON
    {
        "message": "Not found",
        "data": []
    }
    ```
    
    `422 Unprocessable Entity`

---

### **Get single listing**

- **Description**

    Get a member's single listing for editing. Depending on isDraft -> Draft page will have buttons SAVE DRAFT, ADD ITEM, DELETE | Existing product page will have buttons SAVE, DELETE

- **Endpoint**
  
    `/listings/{hash}`

- **Request Method**

    `GET`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    Path parameter

    | Name | Type | Description |
    |-----|-----|-----|
    | hash | str | the hash of a product

- **Responses**

    `200 OK`

    ```JSON
    {
        "message": "success",
        "data": {
            "id": str,
            "hashID": str,
            "memberID": int,
            "status": str,
            "category": str,
            "name": str,
            "description": str,
            "condition": str,
            "price": float,
            "deliveryOption": str,
            "location": str,
            "createdAt": datetime,
            "imagePath": list,
            "isDraft": bool,
            "contact": str
        },
    }
    ```

    `403 FORBIDDEN`

    `404 NOT FOUND`

    ```JSON
    {
        "message": "Not found",
        "data": {}
    }
    ```

---

### **Create a listing**

- **Description**

    Create a new listing (published if isDraft=false, draft if isDraft=true)

- **Endpoint**
  
    `/listings`

- **Request Method**

    `POST`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    JSON Body

    ```JSON
    {
        "status": str,
        "category": str,
        "name": str,
        "description": str,
        "condition": str,
        "price": float,
        "deliveryOption": str,
        "location": str,
        "imagePath": list,
        "isDraft": bool,
    }
    ```

- **Responses**

    `201 CREATED`

    ```JSON
    {
        "message": "Successful",
        "data": {
            "id": str,
            "hashID": str,
            "memberID": int,
            "status": str,
            "category": str,
            "name": str,
            "description": str,
            "condition": str,
            "price": float,
            "deliveryOption": str,
            "location": str,
            "createdAt": datetime,
            "imagePath": list,
            "isDraft": bool,
            "contact": str
        },
    }
    ```

    `400 BAD REQUEST`

    ```JSON
    {
        "message": "Error message",
        "data": {}
    }
    ```

    `403 FORBIDDEN`
    
    `422 Unprocessable Entity`

---

### **Update listing**

- **Description**

    Update a listing or draft

- **Endpoint**
  
    `/listings/{hash}`

- **Request Method**

    `PUT`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    JSON Body

    ```JSON
    {
        "status": str,
        "category": str,
        "name": str,
        "description": str,
        "condition": str,
        "price": float,
        "deliveryOption": str,
        "location": str,
        "addImages": list,
        "deleteImages": list,
        "isDraft": bool,
    }
    ```

- **Responses**

    `200 OK`
    
    ```JSON
    {
      "message": "Successful",
      "data": {
          "id": str,
          "hashID": str,
          "memberID": int,
          "status": str,
          "category": str,
          "name": str,
          "description": str,
          "condition": str,
          "price": float,
          "deliveryOption": str,
          "location": str,
          "createdAt": datetime,
          "imagePath": list,
          "isDraft": bool,
          "contact": str
      },
    }
    ```

    `400 BAD REQUEST`

    ```JSON
    {
        "message": "Error message"
    }
    ```

    `403 FORBIDDEN`
    
    `422 Unprocessable Entity`

---

### **Delete listing**

- **Endpoint**
  
    `/listings/{hash}`

- **Description**

    Delete a listing or draft

- **Request Method**

    `DELETE`

- **Authentication**

    | Name | Type | Comments |
    | ----------- | ----------- | ----------- |
    | JWT | str | extract credentials for validation |

- **Parameters**

    Path parameter

    | Name | Type | Description |
    |-----|-----|-----|
    | hash | str | the hash of a product

- **Responses**

    `204 NO CONTENT`

    `403 FORBIDDEN`

---

## **Important developer Notes**

- Refer to tests/TESTCASE.md and tests/setup.sql for creating dummy users for authentication
- API returns `422 Unprocessable Entity` status code when data is not in the correct type (e.g. `asc=string_value`) or missing certain fields
- Query parameters and request fields are no longer case sensitive
- Datetime format is {Y}-{M}-{D}T{H}:{m}:{s}
- If there are any bugs and any suggestions, please report via WhatsApp or Discord
