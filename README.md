# **HKMSA SHOP**
- [**HKMSA SHOP**](#hkmsa-shop)
  - [**API**](#api)
    - [**Get products**](#get-products)
    - [**Get single product**](#get-single-product)
    - [**Get wishlist**](#get-wishlist)
    - [**Add to wishlist**](#add-to-wishlist)
    - [**Remove from wishlist**](#remove-from-wishlist)
    - [**View listings**](#view-listings)
    - [**Upload products form**](#upload-products-form)
    - [**Upload a product**](#upload-a-product)
    - [**Edit product page**](#edit-product-page)
    - [**Update listing**](#update-listing)
    - [**Delete listing**](#delete-listing)
  
---

## **API**

---

### **Get products**

- **Description**

    Get all products on sale. Sort and filter with query parameters

- **Visibility**

    Public

- **Endpoint**

    `/products`
  
- **Request Method:**
  
  `GET`

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
                "id": "ID",
                "hash": "hash",
                "memberID" : "Seller's ID",
                "status" : "status",
                "productCategory": "category",
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

- **Visiblity**

    Public

- **Endpoint**
  
    `/products/{hash}`

- **Request Method**

    `GET`

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
            "id": "ID",
            "hash": "hash",
            "memberID" : "Seller's ID",
            "status" : "status",
            "productCategory": "category",
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

    Get all products in your wishlist (wishlist with your memberID)

- **Visibility**

    Private

- **Endpoint**
  
    `/wishlist`

- **Request Method**

    `GET`

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
                "id": "ID",
                "hash": "hash",
                "memberID": "Seller's ID",
                "status": "status",
                "productCategory": "category",
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

    `404 NOT FOUND`

    ```JSON
    {
        "message" : "Not found",
        "data" : []
    }
    ```

    `403 FORBIDDEN`

---

### **Add to wishlist**

- **Description**

    Add a product to your wishlist

- **Visibility**

    Private

- **Endpoint**
  
    `/wishlist`

- **Request Method**

    `POST`

- **Parameters**

    JSON Body

    ```JSON
    {
        "productID": "product ID"
    }
    ```

- **Responses**

    `201 CREATED`

    ```JSON
    {
        "message": "Successful"
    }
    ```

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

    Delete product from your wishlist

- **Visibility**

    Private

- **Endpoint**
  
    `/wishlist`

- **Request Method**

    `DELETE`

- **Parameters**

    JSON Body

    ```JSON
    {
        "productID" : "ID"
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

### **View listings**

- **Description**

    View all your listings (get products with memberID = your ID). Sort and filter by query parameters

- **Visibility**

    Private

- **Endpoint**
  
    `/sell`

- **Request Method**

    `GET`

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
                "id": "ID",
                "hash": "hash",
                "memberID": "Seller's ID",
                "status": "status",
                "productCategory": "category",
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

### **Upload products form**

- **Description**

    Returns a blank form for the seller to fill in

- **Visibility**

    Private

- **Endpoint**
  
    `/sell/new`

- **Request Method**

    `GET`

- **Parameters**

    `N/A`

- **Responses**

    `200 OK`

    ```JSON
    {
        "message": "successful"
    }
    ```

    `401 UNAUTHORIZED`

---

### **Upload a product**

- **Description**

    Upload a new product -> published if isDraft=false, draft if isDraft=true

- **Visibility**

    Private

- **Endpoint**
  
    `/sell`

- **Request Method**

    `POST`

- **Parameters**

    JSON Body

    ```JSON
    {
        "memberID" : "Seller's ID",
        "productCategory": "category",
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

### **Edit product page**

- **Description**

    Page to edit product details, depending on isDraft | Draft page will have buttons SAVE DRAFT, ADD ITEM, DELETE | Existing product page will have buttons SAVE, DELETE

- **Visibility**

    Private

- **Endpoint**
  
    `/sell/{hash}`

- **Request Method**

    `GET`

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
            "status": "status",
            "productCategory": "category",
            "name": "",
            "description": "",
            "condition": "",
            "price": "",
            "dealOption": "",
            "meetupLocation": "",
            "shippingLocation": "",
            "imagePath": "",
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

### **Update listing**

- **Description**

    Save edits

- **Visibility**

    Private

- **Endpoint**
  
    `/sell`

- **Request Method**

    `PUT`

- **Parameters**

    JSON Body

    ```JSON
    {
        "hash": "hash",
        "status": "status",
        "productCategory": "category",
        "name": "",
        "description": "",
        "condition": "",
        "price": "",
        "dealOption": "",
        "meetupLocation": "",
        "shippingLocation": "",
        "imagePath": "",
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
  
    `/sell`

- **Visibility**

    Private

- **Description**

    Delete a listing

- **Request Method**

    `DELETE`

- **Parameters**

    JSON BODY

    ```JSON
    {
        "hash": "hash",
    }
    ```

- **Responses**

    `204 NO CONTENT`

    `403 FORBIDDEN`

---
