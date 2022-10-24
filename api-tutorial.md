# Create API for laravel 9 using CRUD/API generator

Quite simply, so it seems to me that it is not suitable for those who are starting to learn APIs, but for those who already know. Before learning to only use it like this without needing to know.

## Install laravel
```php
composer create-project laravel/laravel api-customers
cd api-customers
```

## Install generator
```php
composer require ribafs/crud-generator-appzcoder
```
## Publishe
```php
php artisan vendor:publish --provider="Appzcoder\CrudGenerator\CrudGeneratorServiceProvider"
```
## Create database and Configue on .env

```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=api
DB_USERNAME=root
DB_PASSWORD=root
```
## Create the CRUD customers to API
```bash
php artisan crud:api Customers --fields='name#string; email#string' --controller-namespace=Api
```
## Execute
```bash
php artisan migrate
```
## Try
```bash
php artisan serve
```
http://localhost:8000/api/customers


## Using with Insomnia

## Configurations

Header - Content-Type - Application/JSON

Body - JSON

## Add new registeer

POST
```json
{
	"name": "Ribamar",
	"email": "ribafs@gmail.com"
}
```

http://localhost:8000/api/clientes - SEND

201 Created
```json
{
	"name": "Ribamar",
	"email": "ribafs@gmail.com",
	"updated_at": "2022-10-10T15:36:19.000000Z",
	"created_at": "2022-10-10T15:36:19.000000Z",
	"id": 1
}
```

## Query

http://localhost:8000/api/clientes - GET

200 OK 
```json
{
	"current_page": 1,
	"data": [
		{
			"id": 1,
		        "updated_at": "2022-10-10T15:55:44.000000Z",
		        "created_at": "2022-10-10T15:55:44.000000Z",
			"name": "Ribamar",
			"email": "ribafs@gmail.com"
		}
	],
...
}
```

## Update

PATCH  http://localhost:8000/api/clientes/1

{
	"nome": "Ribamar Ferreira",
	"email": "ribafs@gmail.com"
}

Return

```json
{
	"id": 1,
	"created_at": "2022-10-10T19:39:36.000000Z",
	"updated_at": "2022-10-10T19:44:12.000000Z",
	"name": "Ribamar Ferreira",
	"email": "ribafs@gmail.com"
}
```

## Delete

DELETE http://localhost:8000/api/clientes/1 SEND

Return:

```json
{
	"Register deleted": 204
}
```
