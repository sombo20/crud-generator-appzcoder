# Criar API para laravel 9 usando o gerador de CRUD/API

## Instalar laravel
laravel new api-customers
cd api-customers

## Instalar o geradord e CRUDs
composer require ribafs/crud-generator-appzcoder

## Publicar
php artisan vendor:publish --provider="Appzcoder\CrudGenerator\CrudGeneratorServiceProvider"

## Configurar

Configure o banco no .env
```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=api
DB_USERNAME=root
DB_PASSWORD=root
```
## Criar o CRUD customers para API
```bash
php artisan crud:api Customers --fields='name#string; email#string' --controller-namespace=Api
```
## Ajuste a rota criada em routes/api.php para:
```bash
Route::resource('customers', 'App\Http\Controllers\Api\CustomersController', ['except' => ['create', 'edit']]);
```
## Execute
```bash
php artisan migrate
```
## Testando
```bash
php artisan serve
```
http://localhost:8000/api/customers


## Usando com o Insomnia

## Algumas configurações

Header - Content-Type - Application/JSON

Body - JSON

## Adicionar registro

POST
```json
{
	"nome": "Ribamar",
	"email": "ribafs@gmail.com",
	"updated_at": "2022-10-10T15:55:44.000000Z",
	"created_at": "2022-10-10T15:55:44.000000Z"
}
```

http://localhost:8000/api/clientes - SEND

201 Created
```json
{
	"nome": "Ribamar",
	"email": "ribafs@gmail.com",
	"updated_at": "2022-10-10T15:36:19.000000Z",
	"created_at": "2022-10-10T15:36:19.000000Z",
	"id": 1
}
```

## Consultar

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
			"nome": "Ribamar",
			"email": "ribafs@gmail.com"
		}
	],
...
}
```

## Atualizar

PATCH  http://localhost:8000/api/clientes/1

{
	"nome": "Ribamar Ferreira",
	"email": "ribafs@gmail.com"
}

Retorno
```json
{
	"id": 1,
	"created_at": "2022-10-10T19:39:36.000000Z",
	"updated_at": "2022-10-10T19:39:36.000000Z",
	"name": null,
	"email": "ribafs@gmail.com"
}
```

## Excluir

DELETE http://localhost:8000/api/clientes/1 SEND

