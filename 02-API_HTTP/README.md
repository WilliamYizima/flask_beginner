# API e HTTP

## O que é API?

API é uma sigla:
Application Programming Interface = interface de programação de aplicação.
Tá, mas e aí? Em um meio mais prático, API são "intermediadores" que utilizamos para consumir ou utilizar algum recurso.


Exemplo:
  - Eu quero buscar as informações de cotação do BTC do Mercado Bitcoin. Em vez de criar alguma forma de buscar, o Mercado Bitcoin disponibiliza uma API (um serviço para consultas) que mostra os dados desejados (https://www.mercadobitcoin.com.br/api-doc/).
  - Esse exemplo é um WEB, mas é possível ver isso em diversos casos, como API de uma câmera do smartphone para ser utilziado, API de uma biblioteca para uso, etc.

## O que é HTTP?
HTTP é um protocolo de transferência que a internet usa.
Tá, mas e por quê devo saber?
Através desse protocolo, que é feita a comunicação da web e dos serviços web(API) não feitos.

Existem vários pontos importantes sobre o protocolo:
  - url - endereço da internet onde o recurso é acessado(podendo ser um site) - https://www.hotmail.com
  - porta - utilizado geralmente por aplicações, mas é a porta onde a api "escuta"(ex: porta 3000) - https://www.hotmail.com:3000
  - request - é a etapa em que algum client faz uma solicitação(requisição) para a api
  - response - é a etapa em que a api responde ao client
  - status code - é o código específico que a aplicação respondeu(é incluso no response), as boas práticas deixam explícitas alguns códigos conhecidos:
    - 404 - status de não encontrado
    - 200 - status de sucesso
    - 201 - status de criado
    - 500 - status de bad request(houve algum problema na api)
  - header - o response e o request tem um header, para nós o mais importante é visualizar o header incluso no request
  - body - o response e o request tem um body, é nele que geralmente trafegamos algumas informações
  - method - as requisições podem ter vários tipos de métodos, dessa maneira cada método geralmente representa uma ação, como:
    - GET - método responsável para consulta ou retorno de algo(não altera nenhum dado)
    - POST - através do body da request, recebe alguns dados e pode alterar
    - DELETE - faz a deleção(deleta) algum dado
    - PUT - faz a alteração de algum dado(geralmente pelo body)

## O que é APIREST?
APIREST ou APIRESTful é um tipo de api que segue alguns padrões/boas práticas.
O que é necessário para ser considerada APIREST:
- Arquitetura cliente/servidor e gerenciada por HTTP
- Comunicação stateless(na parte do request e response, as informações do cliente não são armazenadas e nem tem ligação com outras requisições de outros clientes)
- Interface uniforme dos componentes(todos utilizam o padrão de methods mostrado)

Existem outros pontos mais complexos, mas de forma simples é à respeito da "maturidade" da aplicação, como: 
- o retorno trazer sempre os possíveis recursos à serem utilizados
- organização por camadas e hierarquias(acessibilidade do cliente ver alguns recursos)

## Vendo uma API REST na prática.

Utilizando como exemplo: 
[api do mercado btc](https://www.mercadobitcoin.com.br/api-doc/)

Conseguimos fazer uma *request do method GET na api do Mercado Bitcoin*, organizando isso:
  - url: www.mercadobitcoin.net
  - recurso: api/{coin}/day-summary/{year}/{month}/{day}/
  - method: GET
  - header: não vamos precisar pensar nisso agora
  - body: não vamos precisar pensar nisso agora
  - response body esperado:
  ```
    {
      "date": "2022-02-20",
      "opening": 206712.51201,
      "closing": 203509,
      "lowest": 197510.78338,
      "highest": 206859.28985,
      "volume": "8896501.41235249",
      "quantity": "44.39621211",
      "amount": 6382,
      "avg_price": 200388.74916422
    }
  ```
Para fazer o teste, cole em seu navegador a seguinte url: https://www.mercadobitcoin.net/api/BTC/day-summary/2022/2/20/

Veja que irá mostrar somente um json como resposta.



Referências:

- [API REST](https://www.redhat.com/pt-br/topics/api/what-is-a-rest-api)
- [HTTP](https://rockcontent.com/br/blog/http/)
