---
title: API Ganhe Você

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introdução

O Ganhe Você fornece uma API para todos que queiram desenvolver apenas a camada de requisição e deixar toda parte da gestão do negócio com nossa plataforma.

## Endpoint
### Ambiente de Homologação

https://apihomologacao.ganhevoce.com.br/v1

### Ambiente de Produção

https://api.ganhevoce.com.br/v1

## Métodos de Requisições Permitidos

Os métodos de requisições permitidos na API do Ganhe Você são: GET, POST, PUT e DELETE

## Convenção

- Nas requisições GET e DELETE, os valores dos parâmetros que foram strings, deverão ser codificados (URL Encode).

# Autenticação

A autenticação será feita em toda e qualquer solicitação feita para a API.  Você precisará solicitar um usuário e uma chave para autenticação. Envie um e-mail para contato@o3midia.com.br e solicite o usuário e a chave.

<aside class="notice">
O par usuário/chave são os mesmos para o ambiente de produção e homologação
</aside>

Com usuário e chave em mãos, você poderá executar sua solicitação passando seu usuário e chave, como no exemplo:

`curl -X GET -u USUARIO:CHAVE https://api.ganhevoce.com.br/v1/ACAO`

# Produto

## Listar Produtos
Lista dados de produtos pelos ID's informados.

> GET /v1/produto/listar-produtos

```shell
curl -X GET \
-u USUARIO:CHAVE \
"https://api.ganhevoce.com.br/v1/produto/listar-produtos?produto_id=372,624&pagina_inicial=1&quantidade_por_pagina=40&ordem=4"
```

> Resposta 200 Ok.

```json
[
  {
    "produto_id": 372,
    "nome_produto": "ANASOL BLOQUEADOR SOLAR FPS 30 125ML",
    "url_produto": "https://acisa.ganhevoce.com.br/produto/372/anasol-bloqueador-solar-fps-30-125ml",
    "cliente_id_loja": 156,
    "central_cliente_id": 184,
    "nickname_loja": "pro-pharmacos-73119927000119",
    "categoria_id": 3137,
    "nome_categoria": "Protetores e Bronzeadores",
    "categoria_encadeada": "Cuidados Pessoais;Corpo;Protetores e Bronzeadores",
    "categoria_encadeada_url": "cuidados-pessoais-corpo-protetores-e-bronzeadores",
    "preco_produto": 26.99,
    "preco_por_produto": 0,
    "preco_final_produto": 26.99,
    "preco_pontos": 300,
    "preco_pontos_em_reais": 30,
    "pontos_comprador_em_reais": 0.4,
    "pontos_comprador": 4,
    "comissao_indicador": 0.5,
    "descricao_produto": "ANASOL BLOQUEADOR SOLAR FPS 30 125ML\r\n",
    "quantidade_estoque": 10,
    "regra_promocao": "Para quem é da região do ABCDM a entrega é gratuita para produtos acima de R$20,00 e para quem não é deve pagar taxas de envios e se for para retirar pode ser retirada na loja próxima ao hospital brasil. \r\nPara opções motoboy colocar na opção de retirar.",
    "imagens": [
      "https://imgacisa.ganhevoce.com.br/3137/372_1.jpg"
    ]
  },
  {
    "produto_id": 624,
    "nome_produto": "Corte Bordado (Split Ender) - FRANN",
    "url_produto": "https://acisa.ganhevoce.com.br/produto/624/corte-bordado-split-ender---frann",
    "cliente_id_loja": 190,
    "central_cliente_id": 218,
    "nickname_loja": "frann-cabeleireiro-e-depil-center-10898645000147",
    "categoria_id": 3158,
    "nome_categoria": "Corte de Cabelo",
    "categoria_encadeada": "Serviços;Cabeleireiro / Barbeiro;Corte de Cabelo",
    "categoria_encadeada_url": "servicos-cabeleireiro--barbeiro-corte-de-cabelo",
    "preco_produto": 79.99,
    "preco_por_produto": 69.99,
    "preco_final_produto": 69.99,
    "preco_pontos": 700,
    "preco_pontos_em_reais": 70,
    "pontos_comprador_em_reais": 5,
    "pontos_comprador": 50,
    "comissao_indicador": 5,
    "descricao_produto": "Corte bordado é um procedimento realizado nos cabelos para retirar o excesso de pontas duplas, danificadas quebradas e secas.\r\nO Split Ender é uma máquina de corte que possui uma tecnologia particular que trabalha com pentes niveladores entre as laminas. O que possibilita aparar apenas os fios que estão espetados fora do contorno do cabelo.\r\nO primeiro passo pra realizar o corte bordado é lavar os cabelos e escová-los. Então o cabelo deve ser dividido em mechas finas. Cada mecha do cabelo é colocada entre os dentes da maquina e devagar vai passando por todo comprimento, como se fosse chapinha.\r\n\r\n",
    "quantidade_estoque": 999,
    "regra_promocao": "Atendimento somente com horário marcado.\r\nLigue e agende seu horário.\r\nDe terça-feira a sábado das 09:00 as 19:00.\r\n\r\n",
    "imagens": [
      "https://imgacisa.ganhevoce.com.br/3158/624_1.jpg"
    ]
  }
]
```

### Parâmetros
Parâmetro | Tipo  | Obrigatório | Valor Padrão | Descrição 
--------- | -------  | ------- | ----------- | -----------
produto_id | int | sim | | ID do produto 
pagina_inicial | int | não | 1 | Número da página
quantidade_por_pagina | int | não | 100 | Quantidade de produtos por página. O limite máximo é de 100 produtos por página. 
ordem | int | não | 1 | Determina a ordenação do resultado.<br /><br />1 = Relevância<br />2 = Preço Crescente<br />3 = Preço Decrescente<br />4 = Nome do Produto Crescente<br />5 = Nome do Produto Decrescente.

## Pesquisar Produtos
Retorna uma lista de produtos de acordo com o termo da pesquisa.

> GET /v1/produto/pesquisar-produtos

```shell
curl -X GET \
-u USUARIO:CHAVE \
"https://api.ganhevoce.com.br/v1/produto/pesquisar-produtos?termo_pesquisa=cabo+usb"
```

> Resposta 200 Ok.

```json
[
  {
    "produto_id": 30,
    "nome_produto": "Cabo USB Android p/ carregar e transmissão de dados - 1.0m - cor azul",
    "url_produto": "https://acisa.ganhevoce.local/produto/30/cabo-usb-android-p-carregar-e-transmissao-de-dados---10m---cor-azul",
    "cliente_id_loja": 121,
    "central_cliente_id": 149,
    "nickname_loja": "99smart-24534982000160",
    "categoria_id": 2563,
    "nome_categoria": "Acessórios",
    "categoria_encadeada": "Tecnologia;Telefonia;Acessórios",
    "categoria_encadeada_url": "tecnologia-telefonia-acessorios",
    "preco_produto": 20,
    "preco_por_produto": 0,
    "preco_final_produto": 20,
    "preco_pontos": 300,
    "preco_pontos_em_reais": 30,
    "pontos_comprador_em_reais": 2,
    "pontos_comprador": 20,
    "comissao_indicador": 2,
    "descricao_produto": "Cabo USB Android p/ carregar e transmissão de dados - 1.0m - cor azul\r\n\r\nCaracterísticas:\r\n1000ma\r\nCompatível com USB 2.0\r\n2 em 1: Transmissão de dados e carregamento\r\nMaterial de alta proteção e de sustentabilidade ambiental\r\nVelocidade de transmissão chega à 480mbps",
    "quantidade_estoque": 1,
    "regra_promocao": "",
    "imagens": [
      "https://imgacisa.ganhevoce.local/2563/30_1.jpg"
    ]
  },
  {
    "produto_id": 37,
    "nome_produto": "Cabo USB Android p/ carregar e transmissão de dados - 1.0m - cor rosa",
    "url_produto": "https://acisa.ganhevoce.local/produto/37/cabo-usb-android-p-carregar-e-transmissao-de-dados---10m---cor-rosa",
    "cliente_id_loja": 121,
    "central_cliente_id": 149,
    "nickname_loja": "99smart-24534982000160",
    "categoria_id": 2563,
    "nome_categoria": "Acessórios",
    "categoria_encadeada": "Tecnologia;Telefonia;Acessórios",
    "categoria_encadeada_url": "tecnologia-telefonia-acessorios",
    "preco_produto": 20,
    "preco_por_produto": 0,
    "preco_final_produto": 20,
    "preco_pontos": 300,
    "preco_pontos_em_reais": 30,
    "pontos_comprador_em_reais": 2,
    "pontos_comprador": 20,
    "comissao_indicador": 2,
    "descricao_produto": "Cabo USB Android p/ carregar e transmissão de dados - 1.0m - cor rosa\r\n\r\nCaracterísticas:\r\n1000ma\r\nCompatível com USB 2.0\r\n2 em 1: Transmissão de dados e carregamento\r\nMaterial de alta proteção e de sustentabilidade ambiental\r\nVelocidade de transmissão chega à 480mbps",
    "quantidade_estoque": 1,
    "regra_promocao": "",
    "imagens": [
      "https://imgacisa.ganhevoce.local/2563/37_1.jpg"
    ]
  }
]
```

### Parâmetros
 Parâmetro | Tipo  | Obrigatório | Valor Padrão | Descrição 
 -------  | ------- | ----------- | ----------- | ----------- 
 termo_pesquisa | string | sim |  | Termo da pesquisa baseada no nome de um produto ou nome de uma categoria.
pagina_inicial | int | não | 1 | Número da página
quantidade_por_pagina | int | não | 100 | Quantidade de produtos por página. O limite máximo é de 100 produtos por página. 
ordem | int | não | 1 | Determina a ordenação do resultado.<br /><br />1 = Relevância<br />2 = Preço Crescente<br />3 = Preço Decrescente<br />4 = Nome do Produto Crescente<br />5 = Nome do Produto Decrescente.

## Cadastrar Produto/Serviço

Cadastra um produto ou serviço

> POST /v1/produto/cadastrar

```shell
curl -X POST \
-u USUARIO:CHAVE \
"https://api.ganhevoce.com.br/v1/produto/cadastrar" -F 'imagens[]=@/home/ganhevoce/dell_2.jpg' -F 'imagens[]=@/home/ganhevoce/dell_1.jpg' -F 'cliente_id=15' -F 'categoria_id=3096' -F 'nome_produto=Notebook Dell 2' -F "descricao_produto=Descrição Notebook Dell" -F 'preco_produto=33.30' -F 'preco_por_produto=29.93' -F 'preco_produto_pontos_em_reais=35.3' -F 'pontos_em_reais=0.9' -F 'comissao_indicador=1.00' -F 'maximo_parcelas=1' -F 'publicado=1' -F 'quantidade_estoque=10' -F 'regra_promocao=Regra da Promoção' -F 'peso_produto=0.100' -F 'altura_produto=10.00' -F 'largura_produto=10.00' -F 'profundidade_produto=10.00'
```

> Resposta 200 Ok.

```json
{
  "mensagem_sucesso": "Produto/Serviço cadastrado com sucesso.",
  "status": true,
  "produto_id": "5356"
}
```

### Parâmetros

| Parâmetro                     | Tipo   | Obrigatório | Valor Padrão | Descrição                                                    |
| ----------------------------- | ------ | ----------- | ------------ | ------------------------------------------------------------ |
| cliente_id                    | int    | sim         |              | ID do lojista no marketplace                                 |
| categoria_id                  | int    | sim         |              | ID da categoria                                              |
| nome_produto                  | string | sim         |              | Nome do produto ou serviço                                   |
| descricao_produto             | string | sim         |              | Descrição completa do produto                                |
| preco_produto                 | float  | sim         |              | Preço do produto, ex.: 1053.99 (será R$ 1.053,99)            |
| preco_por_produto             | float  | não         |              | Preço do produto utilizado para promoção. Quando utilizado, a plataforma desconsidera o campo "preco_produto" e assume como valor verdadeiro o preco_por_produto, exibindo no box do produto "Preço De" e "Preço Por", ex.: 923.87 (será R$ 923,87) |
| preco_produto_pontos_em_reais | float  | sim         |              | Preço do produto ou serviço que o comprador poderá pagar com WinPoints. O valor aqui é informado como float padrão, ex.: 22.7 <br />Para o comprador será exibido um custo de 227 WinPoints. Esse campo só irá aceitar múltiplos de 0.10 |
| pontos_em_reais               | float  | sim         |              | Valor que será devolvido para o consumidor. O valor aqui é informado como float padrão, ex.: 0.9<br />O comprador receberá  9 WinPoints. Esse campo só irá aceitar múltiplos de 0.10 |
| comissao_indicador            | float  | sim         |              | Valor que irá para o indicador do comprador, ex.: 3.41 (será R$ 3,41) |
| maximo_parcelas               | int    | sim         |              | Número máximo de parcelas do valor do produto ou serviço. Os valores aceitos são de 1 até 12 |
| publicado                     | int    | não         | 0            | Define se, assim que inserido o produto ou serviço ele deverá ser exibido ou não no marketplace. 1 = Sim e 0 = Não |
| quantidade_estoque            | int    | sim         |              | Quantidade de produtos ou serviços disponíveis. O próprio marketplace se engarrega se ir subtraindo conforme os itens forem sendo comprados |
| regra_promocao                | string | não         |              | Campo de texto livre para adicionar regras específica sobre a venda do produto ou serviço |
| peso_produto                  | float  | depende     |              | Valor do peso do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios. A precisão deste campo é de 3 casas decimais e a unidade de medida a ser considerada é Quilo Ex.: para você informar um peso de 159 gr, informe 0.159, para 1,500 kg informe 1.500 |
| altura_produto                | float  | depende     |              | Valor da altura do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios.  A unidade de medida utilizada é centímetros Ex.: para você informar uma altura de 29,64 cm, informe 29.64 |
| largura_produto               | float  | depende     |              | Valor da largura do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios.  A unidade de medida utilizada é centímetros Ex.: para você informar uma largura de 10,02 cm, informe 10.02 |
| profundidade_produto          | float  | depende     |              | Valor da profundidade do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios.  A unidade de medida utilizada é centímetros Ex.: para você informar uma profundidade de 15,00 cm, informe 15.00 |
| imagens                       | array  | sim         |              | Array com os endereços locais das imagens para fazer upload  |

## Editar Produto/Serviço

Editar um produto ou serviço

> POST /v1/produto/editar

```shell
curl -X POST \
-u USUARIO:CHAVE \
"https://api.ganhevoce.com.br/v1/produto/cadastrar"  -F 'produto_id=5370' -F 'cliente_id=15' -F 'categoria_id=3096' -F "nome_produto=Notebook Dell" -F "descricao_produto=Descrição Notebook Dell" -F 'preco_produto=33.30' -F 'preco_por_produto=20.93' -F 'preco_produto_pontos_em_reais=35.3' -F 'pontos_em_reais=0.9' -F 'comissao_indicador=1.00' -F 'maximo_parcelas=4' -F 'publicado=1' -F 'quantidade_estoque=10' -F 'regra_promocao=Regra da Promoção' -F 'peso_produto=0.100' -F 'altura_produto=10.00' -F 'largura_produto=10.00' -F 'profundidade_produto=10.00'
```

> Resposta 200 Ok.

```json
{
  "mensagem_sucesso": "Produto/Serviço atualizado com sucesso.",
  "status": true
}
```

### Parâmetros

| Parâmetro                     | Tipo   | Obrigatório | Valor Padrão | Descrição                                                    |
| ----------------------------- | ------ | ----------- | ------------ | ------------------------------------------------------------ |
| produto_id                    | int    | sim         |              | ID do produto ou serviço                                     |
| cliente_id                    | int    | sim         |              | ID do lojista no marketplace                                 |
| categoria_id                  | int    | sim         |              | ID da categoria                                              |
| nome_produto                  | string | sim         |              | Nome do produto ou serviço                                   |
| descricao_produto             | string | sim         |              | Descrição completa do produto                                |
| preco_produto                 | float  | sim         |              | Preço do produto, ex.: 1053.99 (será R$ 1.053,99)            |
| preco_por_produto             | float  | não         |              | Preço do produto utilizado para promoção. Quando utilizado, a plataforma desconsidera o campo "preco_produto" e assume como valor verdadeiro o preco_por_produto, exibindo no box do produto "Preço De" e "Preço Por", ex.: 923.87 (será R$ 923,87) |
| preco_produto_pontos_em_reais | float  | sim         |              | Preço do produto ou serviço que o comprador poderá pagar com WinPoints. O valor aqui é informado como float padrão, ex.: 22.7 <br />Para o comprador será exibido um custo de 227 WinPoints. Esse campo só irá aceitar múltiplos de 0.10 |
| pontos_em_reais               | float  | sim         |              | Valor que será devolvido para o consumidor. O valor aqui é informado como float padrão, ex.: 0.9<br />O comprador receberá  9 WinPoints. Esse campo só irá aceitar múltiplos de 0.10 |
| comissao_indicador            | float  | sim         |              | Valor que irá para o indicador do comprador, ex.: 3.41 (será R$ 3,41) |
| maximo_parcelas               | int    | sim         |              | Número máximo de parcelas do valor do produto ou serviço. Os valores aceitos são de 1 até 12 |
| publicado                     | int    | não         | 0            | Define se, assim que inserido o produto ou serviço ele deverá ser exibido ou não no marketplace. 1 = Sim e 0 = Não |
| quantidade_estoque            | int    | sim         |              | Quantidade de produtos ou serviços disponíveis. O próprio marketplace se engarrega se ir subtraindo conforme os itens forem sendo comprados |
| regra_promocao                | string | não         |              | Campo de texto livre para adicionar regras específica sobre a venda do produto ou serviço |
| peso_produto                  | float  | depende     |              | Valor do peso do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios. A precisão deste campo é de 3 casas decimais e a unidade de medida a ser considerada é Quilo Ex.: para você informar um peso de 159 gr, informe 0.159, para 1,500 kg informe 1.500 |
| altura_produto                | float  | depende     |              | Valor da altura do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios.  A unidade de medida utilizada é centímetros Ex.: para você informar uma altura de 29,64 cm, informe 29.64 |
| largura_produto               | float  | depende     |              | Valor da largura do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios.  A unidade de medida utilizada é centímetros Ex.: para você informar uma largura de 10,02 cm, informe 10.02 |
| profundidade_produto          | float  | depende     |              | Valor da profundidade do produto. Este campo se torna obrigatório somente quando o lojista escolher fazer entregas via Correios.  A unidade de medida utilizada é centímetros Ex.: para você informar uma profundidade de 15,00 cm, informe 15.00 |

# Categoria

## Listar Categorias

Lista dados das categorias pelos ID's informados.

> GET /v1/categoria/listar

```shell
curl -X GET \
-u USUARIO:CHAVE \
"https://api.ganhevoce.com.br/v1/categoria/listar?categoria_id=1,2,3,4,5,6,7,8,9,10,11,17,26,57,64,71,78,85,92,99&quantidade_por_pagina=5&numero_pagina=1&ordenacao=2
```

> Resposta 200 Ok.

```json
{
    "categorias": {
        "0": {
            "categoria_id": "8",
            "nome_categoria": "Serviços",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Serviços",
            "nivel_categoria": "1",
            "tipo_categoria": "Serviço",
            "exibe_categoria": "1",
            "facets": null
        },
        "1": {
            "categoria_id": "1",
            "nome_categoria": "Tecnologia",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Tecnologia",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        },
        "2": {
            "categoria_id": "2",
            "nome_categoria": "Casa e Decoração",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Casa e Decoração",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        },
        "3": {
            "categoria_id": "3",
            "nome_categoria": "Moda Infantil",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Moda Infantil",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        },
        "4": {
            "categoria_id": "4",
            "nome_categoria": "Saúde e Bem Estar",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Saúde e Bem Estar",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        }
    },
    "paginacao": {
        "total_encontrado": 20,
        "primeira_pagina": 1,
        "pagina_anterior": null,
        "pagina_atual": 1,
        "pagina_proxima": 2,
        "ultima_pagina": 4,
        "total_paginas": 4
    }
}
```

### Parâmetros
Parâmetro | Tipo  | Obrigatório | Valor Padrão | Descrição 
--------- | -------  | ------- | ----------- | -----------
categoria_id | int | sim |  | Lista de id's das categorias 
numero_pagina | int | não | 1 | Número da página
quantidade_por_pagina | int | não | 50 | Quantidade de categorias por página. O limite máximo é de 100 categorias por página. 
ordenacao | int | não | 1 | Determina a ordenação do resultado.<br /><br />1 = Ordem do cadastro crescente<br />2 = Ordem do cadastro decrescente<br />3 = Nome da categoria crescente<br />4 = Nome da categoria decrescente<br />5 = Nome da categoria encadeada crescente.<br />6 = Nome da categoria encadeada decrescente.<br />7 = Tipo categoria crescente.<br />8 = Tipo categoria decrescente. 


# Pedido

## Listar Pedidos Por ID's

Lista os pedidos pelos ID's informados.

> GET /v1/pedido/listar

```shell
curl -X GET \
-u USUARIO:CHAVE \
"https://api.ganhevoce.com.br/v1/pedido/listar-por-id?pedido_id=24795,6978,99&quantidade_por_pagina=5&numero_pagina=1&ordenacao=2
```

> Resposta 200 Ok.

```json
{
    "categorias": {
        "0": {
            "categoria_id": "8",
            "nome_categoria": "Serviços",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Serviços",
            "nivel_categoria": "1",
            "tipo_categoria": "Serviço",
            "exibe_categoria": "1",
            "facets": null
        },
        "1": {
            "categoria_id": "1",
            "nome_categoria": "Tecnologia",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Tecnologia",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        },
        "2": {
            "categoria_id": "2",
            "nome_categoria": "Casa e Decoração",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Casa e Decoração",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        },
        "3": {
            "categoria_id": "3",
            "nome_categoria": "Moda Infantil",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Moda Infantil",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        },
        "4": {
            "categoria_id": "4",
            "nome_categoria": "Saúde e Bem Estar",
            "pai_categoria_id": "0",
            "categoria_encadeada": "Saúde e Bem Estar",
            "nivel_categoria": "1",
            "tipo_categoria": "Produto",
            "exibe_categoria": "1",
            "facets": null
        }
    },
    "paginacao": {
        "total_encontrado": 20,
        "primeira_pagina": 1,
        "pagina_anterior": null,
        "pagina_atual": 1,
        "pagina_proxima": 2,
        "ultima_pagina": 4,
        "total_paginas": 4
    }
}
```

### Parâmetros
Parâmetro | Tipo  | Obrigatório | Valor Padrão | Descrição 
--------- | -------  | ------- | ----------- | -----------
status_pedido_id | int | sim |  | ID do status do pedido.<br /><br />1 = Pedido Pago<br />2 = Pedido Entregue<br />3 = Esperando Confirmação de Pagamento<br />4 = Pedido Cancelado<br />5 = Entrar Em Contato Com SAC<br />7 = Pagamento Expirado
numero_pagina | int | não | 1 | Número da página
quantidade_por_pagina | int | não | 50 | Quantidade de pedidos por página. O limite máximo é de 100 pedidos por página. 
ordenacao | int | não | 1 | Determina a ordenação do resultado.<br /><br />1 = Ordem do ID crescente<br />2 = Ordem do ID decrescente<br />3 = Nome da categoria crescente<br />4 = Nome da categoria decrescente<br />5 = Nome da categoria encadeada crescente.<br />6 = Nome da categoria encadeada decrescente.<br />7 = Tipo categoria crescente.<br />8 = Tipo categoria decrescente. 

## Listar Pedidos Por Status

Lista os pedidos pelos ID's dos status.


## Item do Pedido Entregue

Informa ao Ganhe Você que um item do pedido foi entregue ao cliente.
Se todos os itens do pedido foram entregues, este endpoint altera automaticamente o status do pedido para "Pedido Entregue" (status_pedido_id=2).






