## Documentação VendaAqui®App API

## Requisitos

Para realizar integração com o VendaAqui®App é necessário registrar seu usuário e empresa no nosso site. [https://app.vendaaquiapp.com.br](https://app.vendaaquiapp.com.br)


## Váriaveis

| Variáveis | Valor |
| --- | --- |
| domain | https://api.project-commerce.com.br/ |


--------

## Indices

* [Autenticação](#autenticação)

  * [Autenticação](#1-autenticação)

* [Estoque](#estoque)

  * [Atualizar produto](#1-atualizar-produto)
  * [Criar produto](#2-criar-produto)
  * [Listar produtos](#3-listar-produtos)
  * [Upload de produtos com CSV](#4-upload-de-produtos-com-csv)


--------


## Autenticação



### 1. Autenticação


Ao autenticar você terá no retorno o token para autenticação das demais requisições.

Para autenticar outras requisições, inclua o token da seguinte forma nos Headers.
```
Authorization: Bearer {{token}}
```


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{domain}}/signin
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |



***Body:***

```js        
{
  "password": "{{password}}",
  "email": "{{email}}"
}
```



## Estoque



### 1. Atualizar produto


Altera um produto a partir de seu ID.

| Campo | Descrição | Requerido? |
| --- | --- | --- |
| name | Nome do produto, este dado só será utilizado caso não exista este produto em nossa base de produtos. | Opicional |
| barcode | Código de barras do produto a ser cadastrado | *Requirido* |
| quantity | Quantidade de produtos que você possui no estoque | *Requirido* |
| maxQuantity | Quantidade máxima de produtos que podem ser comprados | Opicional |
| price | Preço do produto | *Requirido* |
| price_min | Preço mínimo do produto para promoção automática | Opicional |
| active_price_min | Ativa/Desativa preço mínimo do produto. (price_min) | Opicional |
| thumbnail | Imagem do produto, este dado só será utilizado caso não exista este produto em nossa base de produtos. |  Opicional |


***Endpoint:***

```bash
Method: PUT
Type: RAW
URL: {{domain}}/companies/{{company_id}}/products/{{product_id}}
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{token}} |  |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "barcode": "7894900011517",
  "quantity": 20000
}
```



***More example Requests/Responses:***


##### I. Example Request: Atualizar produto


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{token}} |  |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "barcode": "7894900011517",
  "quantity": 20000
}
```



##### I. Example Response: Atualizar produto
```js
{
    "id": 164040,
    "idCompany": 131,
    "barcode": "7894900011517",
    "customCodebarTemplate": null,
    "customCode": null,
    "quantity": "1000.00",
    "maxQuantity": 10,
    "price": "8.50",
    "price_min": "6.80",
    "active_price_min": false,
    "metadata": null,
    "images": null,
    "sku": null,
    "createdAt": "2020-08-17T16:13:50.871Z",
    "updatedAt": "2020-08-17T16:13:50.871Z",
    "product": {
        "barcode": "7894900011517",
        "factory": "RECOFARMA INDUSTRIA DO AMAZONAS LTDA",
        "category": "Refrigerante",
        "package": "UNIDADE",
        "packageUnit": "Garrafa",
        "volume": "2",
        "volumeUnit": "Litro(s)",
        "volumeUnitShort": "L",
        "brand": "Coca-Cola",
        "images": [
            "https://img.simplustec.com.br/product_images/7894900011517/1/7894900011517_8_1_1200_72_RGB.png?pid=13854&aclid=null&cmid=3623&action=API&hash=feebd832dd203e2225b26f6410ab30d5",
            "https://img.simplustec.com.br/product_images/7894900011517/1/7894900011517_1_1_1200_72_RGB.png?pid=13854&aclid=null&cmid=3623&action=API&hash=ac54a5b3b4c15b3baa7dc95c48b43aec",
            "https://img.simplustec.com.br/product_images/7894900011517/1/7894900011517_2_1_1200_72_RGB.png?pid=13854&aclid=null&cmid=3623&action=API&hash=123578dfc68acd33c4e8bf68dfe9e4d1"
        ],
        "description": "Refrigerante Coca-Cola Garrafa 2l",
        "thumbnail": "https://img.simplustec.com.br/product_images/7894900011517/1/7894900011517_1_1_1200_72_RGB.png?pid=13854&aclid=null&cmid=3623&action=API&hash=ac54a5b3b4c15b3baa7dc95c48b43aec",
        "idCompanyOwner": null,
        "idUnit": 1,
        "createdAt": "2017-03-07T16:45:33.413Z",
        "updatedAt": "2020-04-23T21:51:21.502Z"
    }
}
```


***Status Code:*** 200

<br>



### 2. Criar produto


Este recurso possibilita a você criar/alterar um produto já existente.

Os produtos são criados utilizando o barcode como indentificador principal. Caso em seu estoque já exista um produto
com o código de barras informado, o mesmo será alterado.

| Campo | Descrição | Requerido? |
| --- | --- | --- |
| name | Nome do produto, este dado só será utilizado caso não exista este produto em nossa base de produtos. | Opicional |
| barcode | Código de barras do produto a ser cadastrado | *Requirido* |
| quantity | Quantidade de produtos que você possui no estoque | *Requirido* |
| maxQuantity | Quantidade máxima de produtos que podem ser comprados | Opicional |
| price | Preço do produto | *Requirido* |
| price_min | Preço mínimo do produto para promoção automática | Opicional |
| active_price_min | Ativa/Desativa preço mínimo do produto. (price_min) | Opicional |
| thumbnail | Imagem do produto, este dado só será utilizado caso não exista este produto em nossa base de produtos. |  Opicional |


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{domain}}/companies/{{company_id}}/products
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{token}} |  |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "name": "REFRIGERANTE COCA-COLA GARRAFA 2L",
  "barcode": "7894900011517",
  "quantity": 1000,
  "maxQuantity": 10,
  "price": 8.5,
  "price_min": 6.8,
  "active_price_min": false
}
```



***More example Requests/Responses:***


##### I. Example Request: Criar produto


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{token}} |  |
| Content-Type | application/json |  |



***Body:***

```js        
{
  "name": "REFRIGERANTE COCA-COLA GARRAFA 2L",
  "barcode": "7894900011517",
  "quantity": 1000,
  "maxQuantity": 10,
  "price": 8.5,
  "price_min": 6.8,
  "active_price_min": false
}
```



##### I. Example Response: Criar produto
```js
{
    "id": 164040,
    "barcode": "7894900011517",
    "quantity": "1000.00",
    "maxQuantity": 10,
    "price": "8.50",
    "price_min": "6.80",
    "active_price_min": false,
    "idCompany": 131,
    "updatedAt": "2020-08-17T16:13:50.871Z",
    "createdAt": "2020-08-17T16:13:50.871Z",
    "customCodebarTemplate": null,
    "customCode": null,
    "metadata": null,
    "images": null,
    "sku": null
}
```


***Status Code:*** 200

<br>



### 3. Listar produtos


Lista todos os produtos em estoque do seu mercado.


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{domain}}/companies/{{company_id}}/products
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{token}} |  |
| Content-Type | application/json |  |



### 4. Upload de produtos com CSV


Este recurso permite a atualização do seu estoque de uma só vez, através do upload de um arquivo do tipo `CSV` separado por `,`.

Você pode fazer o download do modelo em: [http://vendaaquiapp.com.br/produtos.csv](http://vendaaquiapp.com.br/produtos.csv).

## Campos CSV
| Campo | Descrição | Requerido? |
| --- | --- | --- |
| Descrição | Nome do produto, este dado só será utilizado caso não exista este produto em nossa base de produtos. | Opicional |
| Código de Barras | Código de barras do produto a ser cadastrado | *Requirido* |
| Quantidade | Quantidade de produtos que você possui no estoque | *Requirido* |
| Preço Atual | Preço atual do produto | *Requirido* |
| Preço Mínimo | Preço mínimo do produto para promoção automática | Opicional |
| V.A.®Sold | Ativa/Desativa preço promocional do produto. (Preço Mínimo) | Opicional |
| Imagem | Imagem do produto, este dado só será utilizado caso não exista este produto em nossa base de produtos. |  Opicional |


***Endpoint:***

```bash
Method: POST
Type: FORMDATA
URL: {{domain}}/companies/{{company_id}}/products/upload
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Authorization | Bearer {{token}} |  |



***Body:***

| Key | Value | Description |
| --- | ------|-------------|
| products |  | Arquivo CSV |
