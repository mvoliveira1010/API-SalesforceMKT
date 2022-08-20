## Guia para usar a REST API da Salesforce Marketing Cloud

### 1. Configurar o app para uso da API na Marketing Cloud

### 2. Obter autorização para o seu app:
URL para requisição do token de autorização para uso da API:
```
https://SUBDOMAIN.auth.marketingcloudapis.com/v2/token
```
#### Exemplo de código para obtenção do TOKEN:
```
HEADERS = {'Content-type': 'application/json'}
PAYLOAD = {
    "grant_type": "client_credentials",
    "client_id": CLIENT_ID,
    "client_secret": CLIENT_SECRET,
    "scope": "data_extensions_write"
}

AUTHENTICATION_RESPONSE = requests.post(
    url=URL, data=json.dumps(PAYLOAD), headers=HEADERS
).json()
```

### 3. Exemplo de uso da API: inserindo dados em uma data extension
```
URL = f"https://SUBDOMAIN.rest.marketingcloudapis.com/data/v1/async/dataextensions/key:EXTERNALKEY/rows"
    headers = {'Content-type': 'application/json',
               'authorization': f'Bearer {access_token}'}
               
insert_request = requests.post(
    url=URL,
    data=json.dumps(data),
    headers=HEADERS
)
```

#### Exemplo de dados para inserção:
```
data = {
        "items": [{
            "FIELD_STRING" : "NAME",
            "FIELD_BOOLEAN" : "false"
        }]
    }
```
