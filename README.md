1. Make login (POST https://dummyjson.com/auth/login) with username hbingley1 and password CQutx25i8r
Check that:
* status code 200
* id = 2
* username = hbingley1
* email = hbingley1@plala.or.jp
* firstName = Sheldon
* lastName = Quigley
* gender = male
* image has valid url which is started from https:// and ends with .png
* token is not null


2. Get products list (GET https://dummyjson.com/products)
Check that:
* status code 200
* total = 100
* skip = 0
* limit = 30
* every product has not null [id]
* every product has not null or not empty [title]
* every product has not null [price]
* every product has not at least one [image]

3. Get single product by id (GET https://dummyjson.com/products/10)
Check that:
* status code 200
* id = 10
* title = HP Pavilion 15-DK1056WM
* description = HP Pavilion 15-DK1056WM Gaming Laptop 10th Gen Core i5, 8GB, 256GB SSD, GTX 1650 4GB, Windows 10
* price = 1099
* discountPercentage = 6.17
* rating = 4.43
* stock = 89
* brand = HP Pavilion
* category = laptops
* images size is 4

4. Search product (GET https://dummyjson.com/products/search?q=Samsung)
Check that:
* status code 200
* product titles are [Samsung Universe 9, Samsung Galaxy Book]
* total 2

6. Add new product (POST https://dummyjson.com/products/add) with following data:

{
    "title": "MacBook Air Pro",
    "description": "MacBook Air Pro 13",
    "price": 1500,
    "discountPercentage": 5,
    "rating": 5,
    "stock": 150,
    "brand": "Mac",
    "category": "laptops",
    "thumbnail": "https://i.dummyjson.com/data/products/10/thumbnail.jpeg",
    "images": [
        "https://i.dummyjson.com/data/products/10/1.jpg",
        "https://i.dummyjson.com/data/products/10/2.jpg"
    ]
}

Check that:
* status code 200
* id = 101
* all fields from request exist in response with same values


7. Update product (PUT https://dummyjson.com/products/10) with new title and price

{
    "title": "Google Pixel 6 Pro",
    "price": 1200
}

Check that:
* status code 200
* title and price was updated with new values from request

8. Delete product (DELETE https://dummyjson.com/products/33)

Check that:
* status code 200
* id = 33
* isDeleted = true
* deletedOn contains date of deletion


9. Get cart by id (GET https://dummyjson.com/carts/1)
Check that:

* status code 200
* id = 1
* every product in [products] list has
  * not null id
  * not null title
  * not null price
  * not null quantity
  * not null total
  * not null discountPercentage
  * not null discountedPrice
  
* [total] of every product should calculate as [price] * [quantity]
* [discountedPrice] of every product should calculate as [total] * [discountPercentage] - [total] (check rounding)
* general [total] should be sum of total of every product
* general [discountedTotal] should be sum of discountedPrice of every product
* [userId] should be 97
* [totalProducts] should be equals to amount of products from the list
* [totalQuantity] should be equals to sum of quantity of every product
