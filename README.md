# busca-cep
## Desafio Técnico Luizalabs ##

A API consiste basicamente em cadastrar e pesquisar CEPs, expondo duas rotas devidamente autenticadas de [GET] e [POST]. A principal regra da API é no momento da busca de um determinado CEP, onde há uma validação caso não encontre nenhum registro. A validação percorre toda a cadeia de caracteres do CEP e substitui o último caractere por 0, não encontrando registro do mesmo, a substituição é realizada no penúltimo caractere somente e assim sucessivamente. <br>
Exemplo de todo fluxo: 14403205 > 14403200 > 14403205 > 14403005 > 14400205 > 14403205 > 14003205 > 10403205 > 04403205.

### Requisitos: ###
```
NodeJs com Typescript
Express
TypeORM
Sqlite
Npm
```

### Instalação: ###
```
npm install
npm run typeorm migration:run
```
### Testes: ###

### Rotas: ###
- Checagem da conexão da aplicação: <br>
[GET]  http://localhost:3333/zipcode/health/ping <br><br>
- Adquirir token para realizar busca e cadastro dos CEPs: <br>
[POST] http://localhost:3333/zipcode/token <br><br>
- Busca de um determinado CEP: <br>
[GET]  http://localhost:3333/zipcode/:cep <br><br>
- Cadastro de CEP: <br>
[POST] http://localhost:3333/zipcode <br><br>

Para realizar cadastros ou buscas na API, é necessário gerar um token de autenticação utlizando a rota <b> [POST] zipcode/token </b>, e posteriormente usando no header da requisição 
```
 curl --location --request GET 'http://localhost:3333/zipcode/14403205' \
--header 'Authorization: Bearer xxxxxxxxxxxxxxxxxxxxxxxxxxx' 
```

### Payload para cadastro do CEP: ###
```
{
  "cep": "14403205",
  "rua": "RUA 3",
  "bairro": "CASTELO ",
  "cidade": "FRANCA",
  "uf": "SP"
}
```



