# Nosso Primeiro Desafio

Nosso principal desafio é a popularização dos meios de pagamento digitais para
os pequenos e médios comerciantes e prestadores de serviço!

Para podermos resolver esse desafio e ajudar essas pessoas, você precisará construir
uma API que será onde ficarão registrados todos os pagamentos realizados por clientes
a um estabelecimento.

O sistema irá receber uma requisição de um PDV (ponto de venda) com as seguintes
informações:

Endpoint de recebimento de transação: /api/v1/transacao (POST)


# JSON POST:


```python
{
    "estabelecimento": "45.283.163/0001-67",
    "cliente": "094.214.930-01",
    "valor": 590.01,
    "descricao": "Almoço em restaurante chique pago via Shipay!"
}
```

# Resposta:

```python
{
    "aceito": True
}
```

Já se os dados estiverem inválidos (CNPJ e CPF sem validação, valor em outro formato e etc),
devemos retornar o aceito como false.
```python
{
    "estabelecimento": "45.283.163/0001-67",
    "cliente": "094.214.01",
    "valor": 590.01,
    "descricao": "Almoço em restaurante chique pago via Shipay!"
}
```
```python
{
    "aceito": False
}
```
```python
{
    "estabelecimento": "45.283.163/0001",
    "cliente": "094.214.930-01",
    "valor": 590.01,
    "descricao": "Almoço em restaurante chique pago via Shipay!"
}
```
# Resposta:

```python
{
    "aceito": False
}
```
```python
{
    "estabelecimento": "45.283.163/0001-67",
    "cliente": "094.214.930-01",
    "valor": 590.01000,
    "descricao": "Almoço em restaurante chique pago via Shipay!"
}
```

# Resposta:

```python
{
    "aceito": False
}
```



Para também podermos ter os relatórios de transações de um certo estabelecimento, devemos
implementar um endpoint GET onde pegamos todo o listing de transações.

Endpoint: /api/v1/transacoes/estabelecimento?cnpj= (parâmetro de CNPJ deve receber um CNPJ)

```python
{
    "estabelecimento": {
        "nome": "Nosso Restaurante de Todo Dia LTDA",
        "cnpj": "45.283.163/0001-67",
        "dono": "Fabio I.",
        "telefone": "11909000300",
    },
    "recebimentos": [
        {
            "cliente": "094.214.930-01",
            "valor": 590.01,
            "descricao": "Almoço em restaurante chique pago via Shipay!"
        },
        {
            "cliente": "094.214.930-01",
            "valor": 591,
            "descricao": "Almoço em restaurante chique pago via Shipay!"
        },
    ],
    "total_recebido": 1181.01
}
```

# Resposta:

```python
{
    "aceito": false
}
```