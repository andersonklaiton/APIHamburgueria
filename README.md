<h1 align='center'>
    JSON Server React Entrega 5A12
</h1>

## Endpoints

A url base da API é https://server-anderson-hamburguer.herokuapp.com/

## Rotas que não precisam de autenticação

<h3 align='center'> Cadastro de usuário</h3>

`POST /users - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "anderson@klaiton.com",
  "password": "123456",
  "name": "Anderson"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFuZGVyc29uQGtsYWl0b24uY29tIiwiaWF0IjoxNjM1OTc4ODI3LCJleHAiOjE2MzU5ODI0MjcsInN1YiI6IjIifQ.z5Y5z0v9WjA40Puk-WXB7ZVmbGtHyEGMS4xvDVSUD_M",
  "user": {
    "email": "anderson@klaiton.com",
    "name": "Klaiton",
    "id": 2
  }
}
```

<h3 align='center'> Login </h3>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "anderson@klaiton.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFuZGVyc29uQGtsYWl0b24uY29tIiwiaWF0IjoxNjM1OTc4ODI3LCJleHAiOjE2MzU5ODI0MjcsInN1YiI6IjIifQ.z5Y5z0v9WjA40Puk-WXB7ZVmbGtHyEGMS4xvDVSUD_M",
  "user": {
    "email": "anderson@klaiton.com",
    "name": "Klaiton",
    "id": 2
  }
}
```

<h3 align='center'> Lista de  produtos </h3>

`GET /products - FORMATO DA RESPOSTA - STATUS 200`

```JSON
[
  [
  {
    "id": 1,
    "name": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "image": "https://s3-alpha-sig.figma.com/img/b802/7d43/77b97cf91adff632bb964dc7b056d179?Expires=1636934400&Signature=PNhZpOqfVsP80AYjycl7hCtJsf4fUTiVlryJQev3R7XoEvHPYBFS-DZgr7nmR1LljWTPjJlZv-2xA6IcIqyK9Tzfiy4gIMxAkVohJPfMoTD0u0tg6vcXzSlY2kaA77rr1MSvD-xROTYPbGB3EKEYxPs6~C9VxdAvo6QRbSEhbwbINx9TRj1V5n6c907pBv0YxmN7wzwQnlx4G~ODOdsaOBaRPNu7CEwVP2OGNo20Ld3mfkARTV~5TuYL72vL~7cFlia9PyocSAr3NctuveBtkeo3vt638cFH3zLsrM39af0IqpDkEAeBthKVkS5eT1PgmdeHy2xOoeqSTnnuLhBnkQ__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA"
  },
  {
    "id": 2,
    "name": "X-Burguer",
    "category": "Sanduíches",
    "price": 16,
    "image": "https://s3-alpha-sig.figma.com/img/a31b/2c16/9de750feaf42d98ebd46941dad1f6afd?Expires=1636934400&Signature=CC~itVkTJHtH5dJmAt9kGp9WEQw2stM~wcd8j8KTqGSMSoRsE5n78ElXmyjvoumEg3Ra5xm-cc8vHPwguK2raJ9pft7qr5FEgN7xGxzXFnBbjRAJpsRTkrvT~eK~KJBaaDT2XS-Qjnn0laIGMj-Bczxz0ZR284yBUaSYbMk2Hv-7NRn4h-ZzyeKmI8PtNvGRisMn4DVc5qyRxVAb2mblzmqwvHUJlexfyv69kJl5tWrGzlaIA0BUX-4xgSesC2b7tM0Kwi2WDYAQhWf8079cVkj4~5ylC0-uwSAvfQkVzoXK6gHhh8fE5gW8XyI8MPY0S6RC4hWhOBzP38hF-SSCgQ__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA"
  },

]
```

## Rotas que precisam de autenticação

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir acessar os endpoints abaixo:

<h3 align='center'> Adicionar itens ao carrinho </h3>

`POST /cart - FORMATO DA REQUISIÇÃO`

```JSON

  {
    "name": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "image": "https://s3-alpha-sig.figma.com/img/b802/7d43/77b97cf91adff632bb964dc7b056d179?Expires=1636934400&Signature=PNhZpOqfVsP80AYjycl7hCtJsf4fUTiVlryJQev3R7XoEvHPYBFS-DZgr7nmR1LljWTPjJlZv-2xA6IcIqyK9Tzfiy4gIMxAkVohJPfMoTD0u0tg6vcXzSlY2kaA77rr1MSvD-xROTYPbGB3EKEYxPs6~C9VxdAvo6QRbSEhbwbINx9TRj1V5n6c907pBv0YxmN7wzwQnlx4G~ODOdsaOBaRPNu7CEwVP2OGNo20Ld3mfkARTV~5TuYL72vL~7cFlia9PyocSAr3NctuveBtkeo3vt638cFH3zLsrM39af0IqpDkEAeBthKVkS5eT1PgmdeHy2xOoeqSTnnuLhBnkQ__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA",
    "quantity": 1,
    "totValue": 14,
    "userId": "2"
  }

```

Caso dê tudo certo, a resposta será assim:

`POST /cart - FORMATO DA RESPOSTA - STATUS 201`

```json
[
  {
    "name": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "image": "https://s3-alpha-sig.figma.com/img/b802/7d43/77b97cf91adff632bb964dc7b056d179?Expires=1636934400&Signature=PNhZpOqfVsP80AYjycl7hCtJsf4fUTiVlryJQev3R7XoEvHPYBFS-DZgr7nmR1LljWTPjJlZv-2xA6IcIqyK9Tzfiy4gIMxAkVohJPfMoTD0u0tg6vcXzSlY2kaA77rr1MSvD-xROTYPbGB3EKEYxPs6~C9VxdAvo6QRbSEhbwbINx9TRj1V5n6c907pBv0YxmN7wzwQnlx4G~ODOdsaOBaRPNu7CEwVP2OGNo20Ld3mfkARTV~5TuYL72vL~7cFlia9PyocSAr3NctuveBtkeo3vt638cFH3zLsrM39af0IqpDkEAeBthKVkS5eT1PgmdeHy2xOoeqSTnnuLhBnkQ__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA",
    "quantity": 1,
    "totValue": 14,
    "userId": 2,
    "id": 1
  }
]
```

<h3 align='center'> Visualizar carrinho </h3>

`GET /cart?userId=2 - FORMATO DA REQUISIÇÃO`


Caso dê tudo certo, e tiver itens no carrinho a resposta será assim:

`GET /cart?userId=2 - FORMATO DA RESPOSTA - STATUS 200`

```json
[
  {
    "name": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "image": "https://s3-alpha-sig.figma.com/img/b802/7d43/77b97cf91adff632bb964dc7b056d179?Expires=1636934400&Signature=PNhZpOqfVsP80AYjycl7hCtJsf4fUTiVlryJQev3R7XoEvHPYBFS-DZgr7nmR1LljWTPjJlZv-2xA6IcIqyK9Tzfiy4gIMxAkVohJPfMoTD0u0tg6vcXzSlY2kaA77rr1MSvD-xROTYPbGB3EKEYxPs6~C9VxdAvo6QRbSEhbwbINx9TRj1V5n6c907pBv0YxmN7wzwQnlx4G~ODOdsaOBaRPNu7CEwVP2OGNo20Ld3mfkARTV~5TuYL72vL~7cFlia9PyocSAr3NctuveBtkeo3vt638cFH3zLsrM39af0IqpDkEAeBthKVkS5eT1PgmdeHy2xOoeqSTnnuLhBnkQ__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA",
    "quantity": 1,
    "totValue": 14,
    "userId": 2,
    "id": 1
  }
]
```

`DELETE /cart/id - FORMATO DA REQUISIÇÃO `

Caso dê tudo certo o item que possuir o id será removido a lista:

`DELETE /cart/id - FORMATO DA RESPOSTA - STATUS 200`


<h3 align='center'> Atualizar quantidade de itens </h3>

`PATCH /cart/id - FORMATO DA REQUISIÇÃO`

```JSON

[
  {
   "quantity":2,
   "totValue":28,
  }
]
```

Caso dê tudo certo a resposta será assim:

`PATCH /cart/id - FORMATO DA RESPOSTA - STATUS 200`


```JSON

[
  {
    "name": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "image": "https://s3-alpha-sig.figma.com/img/b802/7d43/77b97cf91adff632bb964dc7b056d179?Expires=1636934400&Signature=PNhZpOqfVsP80AYjycl7hCtJsf4fUTiVlryJQev3R7XoEvHPYBFS-DZgr7nmR1LljWTPjJlZv-2xA6IcIqyK9Tzfiy4gIMxAkVohJPfMoTD0u0tg6vcXzSlY2kaA77rr1MSvD-xROTYPbGB3EKEYxPs6~C9VxdAvo6QRbSEhbwbINx9TRj1V5n6c907pBv0YxmN7wzwQnlx4G~ODOdsaOBaRPNu7CEwVP2OGNo20Ld3mfkARTV~5TuYL72vL~7cFlia9PyocSAr3NctuveBtkeo3vt638cFH3zLsrM39af0IqpDkEAeBthKVkS5eT1PgmdeHy2xOoeqSTnnuLhBnkQ__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA",
    "quantity": 2,
    "totValue": 28,
    "userId": 2,
    "id": 1
  }
]
```
