# **HKMSA SHOP**

- [**HKMSA SHOP**](#hkmsa-shop)
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
  
---

## **API**

---

### **Get products**

- **Description**

    Get all products on sale. Sort and filter with query parameters, using pipe delimiter %7C

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
    | Category | str | ?category=bags%7Capparel |
    | Condition | str | ?condition=new |
    | Deal option | str | ?dealOption=meetup |
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
                "id": "",
                "hash": "",
                "memberID" : "",
                "status" : "",
                "productCategory": "",
                "name": "",
                "description": "",
                "condition": "",
                "price": "",
                "dealOption": "",
                "meetupLocation": "",
                "shippingLocation": "",
                "createdAt": "",
                "imagePath": ""
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
        "data" : {
            "id": "",
            "hash": "",
            "memberID" : "",
            "status" : "",
            "productCategory": "",
            "name": "",
            "description": "",
            "condition": "",
            "price": "",
            "dealOption": "",
            "meetupLocation": "",
            "shippingLocation": "",
            "createdAt": "",
            "imagePath": ""
        }
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
    | Category | str | ?category=bags |
    | Condition | str | ?condition=new |
    | Deal option | str | ?dealOption=meetup |
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
                "id": "",
                "hash": "",
                "memberID": "",
                "status": "",
                "productCategory": "",
                "name": "",
                "description": "",
                "condition": "",
                "price": "",
                "dealOption": "",
                "meetupLocation": "",
                "shippingLocation": "",
                "createdAt": "",
                "imagePath": "",
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
    | Condition | str | ?condition=new |
    | Deal option | str | ?dealOption=meetup |
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
                "id": "",
                "hash": "",
                "memberID": "",
                "status": "",
                "productCategory": "",
                "name": "",
                "description": "",
                "condition": "",
                "price": "",
                "dealOption": "",
                "meetupLocation": "",
                "shippingLocation": "",
                "createdAt": "",
                "imagePath": "",
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
            "status": "",
            "productCategory": "",
            "name": "",
            "description": "",
            "condition": "",
            "price": "",
            "dealOption": "",
            "meetupLocation": "",
            "shippingLocation": "",
            "imagePath": "",
            "isDraft": true or false,
        }
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
        "productCategory": "",
        "name": "",
        "description": "",
        "condition": "",
        "price": "",
        "dealOption": "",
        "meetupLocation": "",
        "shippingLocation": "",
        "imagePath": "",
        "isDraft": true or false,
    }
    ```

- **Responses**

    `201 CREATED`

    ```JSON
    {
        "message": "Successful",
        "data": {
            "id": "ID",
            "hash": "hash",
            "createdAt": "",
        }
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
        "status": "",
        "productCategory": "",
        "name": "",
        "description": "",
        "condition": "",
        "price": "",
        "dealOption": "",
        "meetupLocation": "",
        "shippingLocation": "",
        "imagePath": "",
        "isDraft": true or false
    }
    ```

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
