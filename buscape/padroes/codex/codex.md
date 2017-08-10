#**Web: Buscapé - Implementação de GTM e Camada de Dados**
Manual de implementação da Camada de Dados para o ambiente Buscapé.

##**Geral**
Esse documento deve ser utilizado como guia para a criação da Camada de Dados.


##**Escopo**
Serão consideradas todas as páginas do ambiente de Buscapé Desktop.

##**Camada de Dados**
###**Geral**
Utilizamos um objeto JavaScript (notação JSON) com as informações sobre a página, como por exemplo: informações de usuários, informações de anúncios, etc. Ele deve ser inserido antes da chamada do GTM (Google Tag Manager) presente na página. Abaixo estão algumas características da Camada de Dados:

 - Contém informações sobre o portal, páginas e produtos relacionados a seção.
 - Por ser escrito em JavaScript, poderá ser utilizado por outros scripts da página.
 - Deve ser inserido em todas as páginas.
 - A estrutura do objeto pode evoluir no decorrer do projeto.

### **Funcionamento e fluxos de CPC, CPA e Buscapé Checkout**
 Em **CPC** ocorre um disparo com evento e transação juntos, ou seja, dispara um evento quando clicado em “Ir à Loja”, feito pelo redirecionamento, juntamente com a coleta de transação. Essas informações serão mandadas via disparo serverside.

Em **CPA** ocorrem no mínimo dois disparos, em momentos diferentes. O primeiro dispara um evento quando clicado em “Ir à Loja”, feito pelo redirecionamento, e o segundo disparo, que coleta a transação, só ocorre quando houver uma venda de fato no site do Lojista para o qual o usuário foi redirecionado. Ambos disparos deverão conter informações mandadas via disparo serverside. Há um período de latência considerado após o redirecionamento, podendo haver mais de um disparo de transação.

Em **Buscapé Checkout** ocorrem dois disparos, em momentos diferentes. O primeiro quando o fluxo de compra for concluído (via datalayer - apenas com o valor de exibição do produto) e o segundo quando o Buscapé confirmar o faturamento da transação (via serverside - com o valor de exibição do produto e a comissão recebida pelo Buscapé).

##**Funcionamento da variável dataLayer**
A variável da camada de dados instalada tem o nome de **dataLayer**, ela é um Objeto javascript.

Internamente, o Google Tag Manager faz a junção destes múltiplos objetos inseridos na camada de dados. No momento do disparo da tag, o valor utilizado para cada chave é o último valor inserido naquela chave.

##**Tipos dos dados utilizados**



Nome	|Descrição|	exemplo
--------|:---------|:----------|
String	|Um texto, entre aspas|	"um texto"
Number	|Um número, não utilizar texto no lugar, principalmente com separadores de milhar	|15.71
Bool	|true ou false|	true
Array	|Uma lista de elementos|	[1, 2, 3]
Object	|Um dado com subníveis	|{"nivel1": {"nivel2_item1": "valor1", "nivel2_item2": "valor2"}}

##**Implementação básica**
###**Configurações Gerais**
 - Container Web: GTM-W7LVSD
###**Exemplo**

``` html
<DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="main/css.css">
    <meta http-equiv="content-type" content="text/html;charset=utf-8">
    <title>Exemple</title>
    <script>
      window.dataLayer = window.dataLayer || [];
      dataLayer.push({
        usuario: {
          id: "123-456-789",
          tipo_login: "facebook"
        },
        pagina: {
          template: "busca",
          termo_busca: "refrigerador consul",
          quantidade_resultados: 84
        },
        listas: [{
          nome: "Você pode Gostar",
          items: [{
            nome: "Smartphone LG K10 K430TV",
            sku: "212984103",
            preco: 643.50,
            marca: "LG",
            lojista: "Casas Bahia",
            categoria_principal: "telefonia",
            subcategorias: ["celular e smartphone"]
          }]
        }]
      });
    </script>
  </head>
  <body>
    <!-- Google Tag Manager -->
    <noscript><iframe src="//www.googletagmanager.com/ns.html?id=GTM-W7LVSD"
    height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
    <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
    new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
    j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
    '//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
    })(window,document,'script','dataLayer','GTM-W7LVSD');</script>
    <!-- End Google Tag Manager -->
    <div class="container">
      <div class="header"></div>
      <div class="body"></div>
      <div class="footer"></div>
    </div>
  </body>
</html>

```

##**Chaves da Camada de Dados**
As chaves abaixo devem ser adicionadas ao objeto dataLayer em qualquer página em que o dado esteja disponível. O preenchimento do dataLayer deve ocorrer logo no início do carregamento da página.

###**Usuário**
Contém informações sobre o usuário que está utilizando o site. Deve estar presente em todas as páginas enquanto o usuário estiver logado.



Chave|	Tipo|	Descrição|	Exemplo
------|-----|----|----|
id	|String	|Identificador do usuário logado	|"123234345"
|tipo_login	|String	|Método de autenticação utilizada pelo usuário	|"email"

##**Valores de preenchimento para usuario.tipo_login**

Regras|	Valor esperado
--------|--------|
Não| logado	“nao_logado”
Logado| com email	“email”
Logado |com Facebook	“facebook”


**Observação: Os valores devem ser todos minúsculos, sem acentos e sem espaços**

```js

dataLayer.push({
  pagina: {
    template: "home"
  },
  usuario: {
    id: "123234345",
    tipo_login: "email"
  }
});
```

###**Página**
Contém informações sobre a página que está sendo exibida. Possui informações gerais e específicas para alguns tipos de templates.

Chave	|Tipo	|Descrição	|Exemplo
---|----|----|---
template	|String|	Template da página acessada|	"pu"
termo_busca	|String	|Termo buscado pelo usuário. Deve ser preenchido apenas nos momentos em que o usuário realizou uma pesquisa através da barra de busca.	|"bicicleta"
quantidade_resultados	|Number	|Quantidade de ofertas resultantes da pesquisa	|84
categoria_principal	|String	|Primeiro nível de categoria da página atual, seja ela navegação ou produto único	|"Esporte e Lazer
subcategorias	|Array de Strings	|Demais níveis de categoria da página atual	|["Ciclismo", "Bicicleta"]

###**Valores de preenchimento para pagina.template**

Ambiente / local	|Valor esperado
----|----
Página inicial	|“home”
Categoria Mãe	|“categoria”
Categoria Final|	“categoria”
Produto (PU)	|“pu”
Comparação de Produtos|	“?”
Checkout|	"checkout"
Oferta	|“?”
Usuário	|“?”
Busca	|“busca”
Lojas	|“?”
Páginas Especiais	|“?”
Páginas Sazonais	|“?”
Guia de Compra	|“?”
Matérias	|“?”
Livros	|“?”
Marcas	|“?”

**Observação: Os valores devem ser todos minúsculos, sem acentos e sem espaços.**

###**Exemplo P.U.**

``` js
dataLayer.push({
  pagina: {
    template: "pu",
    categoria_principal: "Esporte e Lazer",
    subcategorias: ["Ciclismo", "Bicicleta"]
  }
});

```
###**Exemplo Página de Busca**


```js

dataLayer.push({
  pagina: {
    template: "busca",
    termo_busca: "bicicleta",
    quantidade_resultados: 84
  }
});
```
###**Produto Único - P.U**

Nas páginas de produto único, será necessário termos um objeto contendo todas as informações do produto sendo exibido e uma lista com os detalhes de cada oferta.

Chave|	Tipo	|Descrição|	Exemplo
----|:-----|----|---
nome	|String	|Nome do produto	|"Caloi Star Wars Aro 24"
marca|	String	|Marca do fabricante do produto	|"Caloi"
categoria_principal|	String	|Categoria do produto	|"Esporte e Lazer"
subcategorias	|Array de String|	Demais subcategorias do produto	|["Ciclismo", "Bicicleta"]
ofertas	|Array de Objects	|Todas as ofertas disponíveis na página |Ver produto_unico.ofertas

###**produto_unico.ofertas**

Deve ser uma lista com as informações de cada oferta do produto.

Chave	|Tipo	|Descrição	|Exemplo
---|----|---|---
sku	|String	|SKU da oferta	|"628638"
preco	|Number	|Preço de exibição do produto	|509.99
lojista	|String	|Nome da loja da oferta	|Magazine Luiza

```js
dataLayer.push({
  pagina: {
    template: "pu",
    categoria_principal: "Esporte e Lazer",
    subcategorias: ["Ciclismo", "Bicicleta"],
  },
  produto: {
    nome: "Caloi Star Wars Aro 24",
    marca: "Caloi",
    ofertas: [{
      sku: "628638",
      preco: 509.99
      lojista: "Magazine Luiza"
    }]
  }
});
```
###**listas**

Tipo	|Páginas
---|---
Array de Objects	|Qualquer página com listas de ofertas
Todas as listas de produtos que aparecem na página devem ser identificadas com o nome da lista (ex: menor preço, você pode gostar, resultado de busca) e a lista de ofertas presentes na lista.

Cada um dos Objects do tipo Lista segue o formato:

Chave	|Tipo	|Descrição	|Exemplo
----|-----|-----|
nome	|String	|Nome da lista de exibição	|"Menor Preço"
items	|Array de Object	|Lista de ofertas na ordem apresentada	|ver Object Item

###**listas.items**

A chave itens é um Array de vários objetos do tipo Item, seguindo o seguinte formato:

Chave	|Tipo	|Descrição	|Exemplo
---|:---|:---|:---
nome	|String	|Nome do produto	|"Caloi Star Wars Aro 24"
sku	|String	|SKU da oferta exibida	|"628638"
preco	|Number	|Preço de exibição do produto	|509.99
marca	|String	|Marca do fabricante do produto	|"Caloi"
categoria_principal	|String	|Categoria do produto	|"Esporte e Lazer"
subcategorias	|Array de String	|Demais subcategorias do produto	|["Ciclismo", "Bicicleta"]
lojista	|String	|Nome da loja da oferta	|Magazine Luiza

``` js
dataLayer.push({
  pagina: {
    template: "home",
  },
  listas: [{
     nome: 'Menor Preço',
     items: [{
       nome: "Caloi Star Wars Aro 24",
       sku: "628638",
       preco: 509.99,
       marca: "Caloi",
       categoria_principal: "Esporte e Lazer",
       subcategorias: ["Ciclismo", "Bicicleta"],
       lojista:'magazine-luiza'
     }]
  }]
});

```
###**Buscapé Checkout**
Pelo fato de o Buscapé Checkout ser um one page checkout, ou seja, a página não é recarregada entre cada passo, precisaremos adicionar alguns eventos para indicar que o usuário alcançou um novo passo no processo.

Na abertura do checkout, deverá ser enviado um evento para a camada de dados contendo os dados do produto selecionado:

Chave	|Tipo	|Descrição	|Exemplo
---|:---|:---|:---
sku	|String	|SKU da oferta	|"628638"
nome	|String	|Nome do produto	|"Caloi Star Wars Aro 24"
marca	|String	|Marca do fabricante do produto	|"Caloi"
categoria_principal	|String|	Categoria do produto	|"Esporte e Lazer"
subcategorias	|Array de String	|Demais subcategorias do produto	|["Ciclismo", "Bicicleta"]
preco	|Number	|Preço de exibição do produto|	509.99
quantidade|	Number	|Quantidade do Produto|	2
loja	|String	|Nome da loja da oferta	|Magazine Luiza

####**Passo 1 (Autenticação)**

Neste momento deveria ser enviado para a camada de dados os produtos que estão sendo comprados e um identificador do passo.

É importante notar que a chave ofertas possui um Array, pois é possível ter mais de 1 produto no checkout. Mesmo que apenas 1 produto esteja sendo comprado, deve-se adicionar no dataLayer um Array.

```
dataLayer.push({
  pagina: {
    template: "checkout"
  },
  passo: '1 - Autenticação',
  ofertas: [{
    sku: "628638",
    nome: "Caloi Star Wars Aro 24",
    marca: "Caloi",
    categoria_principal: "Esporte e Lazer",
    subcategorias: ["Ciclismo", "Bicicleta"],
    preco: 509.99,
    quantidade: 1,
    loja: "Magazine Luiza"
  }, {
    sku: "194212566",
    nome: "JBL Flip 3 16W RMS",
    marca: "JBL",
    categoria_principal: "Informática",
    subcategorias: ["Periféricos", "Caixas de Som para PC"],
    preco: 559.94,
    quantidade: 2,
    loja: "Fast Shop"
  }]
});
```

Se o usuário retornar a este passo depois de ter ido para um seguinte, o evento deverá ser enviado novamente contendo apenas o nome do passo:
```
dataLayer.push({
  event: 'buscapeCheckout',
  passo: '1 - Autenticação'
});
```

####**Passos 2 (Entrega) e 3 (Pagamento)**
Para os outros passos, deverá ser enviado apenas o evento contendo o nome do passo:
```
dataLayer.push({
  event: 'buscapeCheckout',
  passo: '2 - Entrega'
});
```

```
dataLayer.push({
  event: 'buscapeCheckout',
  passo: '3 - Pagamento'
});
```

###**Mudança na quantidade**
Caso o usuário mude a quantidade de um dos produtos, ou remova algum produto do carrinho, um evento do tipo mudar_quantidade deve ser adicionado ao dataLayer.

Nome	|Tipo de Dado	|Descrição	|Exemplo
---|:----|:----|:---
mudar_quantidade	|Object	|Objeto onde a chave é o SKU do produto alterado e o valor é a nova quantidade de produtos	|{"123542": 2}

```js
dataLayer.push({
  event: "mudar_quantidade",
  mudar_quantidade: {
    "628638": 3,
    "194212566": 0
  }
});
```

**Remover um produto equivale a mudar a quantidade para zero.**

###**Conclusão de compra**

Para mantermos o sigilo das informações de negociação do Buscapé com as lojas, devemos enviar a conclusão de compra através do backend assim como em CPC/CPA (ver Coleta de Transações abaixo). Mesmo neste caso, ainda precisaremos de uma confirmação que a compra foi realizada para efeitos de tags de mídia, por exemplo.

####**transacao**
Sempre que uma compra for realizada com sucesso, deverá ser enviado um evento com as informações da transação:

Chave	|Tipo	|Descrição	|Exemplo
----|-----|----|---
id	|String	|ID |interno da transação	|"628638"
parcelas	|Number	|Quantidade de parcelas escolhidas pelo usuário	|6
frete	|Object	|Detalhes do frete escolhido pelo usuário	|ver transacao.frete

####**transacao.frete**

Chave|	Tipo	|Descrição	|Exemplo
---|---|----|--
modalidade	|String	|Modalidade do frete escolhido	|E-Sedex
valor	|Number	Valor do frete	|12.0
dias	|Number|	Dias úteis para a entrega da compra|	14

```js
dataLayer.push({
  event: 'buscapeCheckout',
  passo: 'Conclusão',
  transacao: {
    id: "628638",
    parcelas: 6,
    frete: {
      modalidade: "E-Sedex",
      valor 12.0,
      dias: 14
    }
  }
});
```
###**Coleta de Banners**
Iremos coletar as impressões e cliques nos banners promocionais exibidos no site, para isso precisamos que seja implementado um push no dataLayer contendo algumas informações.

####**Impressões**
No caso das impressões, a página contendo banners, deve dar push no dataLayer no carregamento da página, pois estes dados serão enviados juntamente com o pageview.

As impressões precisam do seguintes dados:

Chave	|Tipo	|Descrição	|Exemplo
---|---|---|---
id	|String	|Identificador do banner	|passagens_321
nome	|String	|Título ou nome do banner	|Passagens Nacionais
criativo	|String|	Imagem do banner	|banner_passagens_nacionais_321
posicao	|String	|Posição do banner	|banner_rodape_pos1

Estes dados devem ser enviados para a camada no seguinte formato:

```js
dataLayer.push({
 'event': 'navegacao',
 'banners': [{
    'id': 'smartphones_99',
    'nome': 'Smartphones com 10% de desconto',
    'criativo': 'iphone_promo_discount',
    'posicao': 'discount_list_1'
  },{
    'id': '	passagens_321',
    'nome': 'Passagens Nacionais',
    'criativo': 'banner_passagens_nacionais_321',
    'posicao': 'banner_rodape_pos1'
  }]
});
```
####**Cliques**
Quando o usuário clicar em algum banner, a página deve dar push no dataLayer com os dados do banner clicado e uma chave "event" com o valor "clique_banner" pois estes dados serão enviados juntamente com o evento do clique.

Os cliques precisam do seguintes dados:

Chave	|Tipo	|Descrição	|Exemplo
----|---|---|---
id	|String|	Identificador do banner	|passagens_321
nome	|String	|Título ou nome do banner	|String
criativo	|String	|Imagem do banner	|banner_passagens_nacionais_321
posicao	|String	|Posição do banner	|banner_rodape_pos1


Estes dados devem ser enviados para a camada no seguinte formato:

```js
dataLayer.push({
  'event': 'clique_banner',
  'clique_banner': {
    'id': 'passagens_321',
    'nome': 'Passagens Nacionais',
    'criativo': 'banner_passagens_nacionais_321',
    'posicao': 'banner_rodape_pos1'
  }
});
```
###**Coleta de Transações**
Para realizarmos a mensuração dos valores recebidos pelo Buscapé a cada lead (CPC, CPA ou Buscapé Checkouts), utilizaremos o Measurement Protocol através de uma implementação do lado do servidor da Buscapé. Isto permitirá que a coleta seja realizada sem abrir estes números para os usuários do site.

####**Fluxo**
Conforme explicado no início deste documento, o envio de informações via servidor acontece em momentos diferentes, dependendo do tipo de lead:

**CPC** - O envio ocorre logo após o clique no botão, durante o redirect para a página do parceiro [segue tabela 1].

**CPA** - O envio acontece em 2 momentos diferentes:

 - Primeiro logo após o clique no botão de redirect, assim como acontece com o caso do CPC [segue tabela 2] .
 - O segundo acontece após o usuário efetuar uma compra no site parceiro, e deve possuir os dados do produto e transação do clique (não da compra no parceiro), este segundo disparo pode acontecer mais de uma vez caso o usuário faça mais compras dentro do período de atribuição acordado com o cliente [segue tabela 1].

**Checkout** - O envio acontece após a aprovação da compra [segue tabela 1].

####**Implementação**
O Measurement Protocol é uma API para envio de informações para o Google Analytics que permite que hits sejam enviados mesmo fora do contexto do site, como por exemplo um evento disparado diretamente pelo backend.

O método de disparo é uma requisição HTTP, que pode ser feita via GET ou POST para o endpoint https://www.google-analytics.com/collect. O endpoint retorna um pixel GIF transparente, não há uma mensagem de retorno de sucesso ou erro.

Para testar a implementação recomendamos enviar o payload para https://www.google-analytics.com/debug/collect, que retornará um JSON com os problemas encontrados. Também é possível apontar o parâmetro **tid** para uma propriedade vazia do Google Analytics e observar os dados na ferramenta, após um período de espera.

Exemplo:

```
 <?php
  $endpoint = "https://www.google-analytics.com/collect"
  $cid = $_GET["cid"];
  $dr = $_GET["referrer"];
  $dl = $_SERVER["HTTP_REFERER"];
  $uip = $_SERVER["REMOTE_ADDR"];
  $random = rand();
  $ea = $_GET["tipo_pagina"];
  $el = $_GET["nome_lista"];
  ```
  // ... demais valores a serem preenchidos podem estar na própria requisição, mas alguns talvez tenham que vir de outras fontes

  $url = "$endpoint?v=1&tid=UA-1827174-80&cid=$cid&uid=$userID&ua=$ua&dr=$dr&dl=$dl&uip=$uip&ec=Conversao&ea=CPC&el=Clique&z=$random";

  $response = file_get_contents($url);
?>
```
Os parâmetros a seguir devem ser todos preenchidos para transações que ocorrerem devido a um clique no botão Ir a Loja (no caso de negociação CPC), ou quando houver a confirmação de compra (no caso de negociação CPA ou Buscapé Checkout). Deve-se garantir que todas as informações necessárias estarão disponíveis no momento da transação.

####**tabela 1**

Parâmetro	|Nome	|Obrigatório	|Descrição|	Exemplo
---|:----|:----|:---
v	|Versão	|Sim	|Versão do protocolo, sempre igual à 1	|v=1
cid	|Id do Cliente	|Sim	|ClientID (CID), obtido a partir dos dois últimos juntos de número do cookie _ga. Caso o cookie não esteja definido, deve ser criado e salvo um valor no formado UUID v4	|cid=597491310.1483470579
tid	|Id de Acompanhamento	|Sim	|UA da propriedade do Analytics	|tid=UA-1827174-80
uid	|Id do Usuário	|Não	|Identificador do usuário logado	|uid=123234345
ua	|User Agent	|Não	|Identificador do navegador do usuário, obtido pelos headers da requisição ao servidor	|ua=Opera%2F9.80%20%28Windows%20NT%206.0%29%20Presto%2F2.12.388%20Version%2F12.14
uip	|Endereço de IP	|Sim	|Endereço de IP do usuário. Atenção! Não confundir com o endereço de IP do servidor	|uip=178.123.1.22
t|	Tipo de disparo|	Sim	|Para este caso, será sempre "event"	|t=event
dl|	Localizador do Documento	|Não	|URL da página atual	|dl=http%3A%2F%2Fwww.buscape.com.br%2Fredirect_prod
dr	|Referenciador do Documento	|Não	|URL da página anterior	|dr=https%3A%2F%2Fwww.buscape.com.br
ec	|Categoria do Evento|	Sim|	Ver a tabela de eventos	|ec=Conversao
ea	|Ação do Evento|	Sim	|Ver a tabela de eventos|	ea=CPC
el|	Rótulo do Evento	|Sim	|Ver a tabela de eventos|	el=Clique
pa	|Ação do Produto|	Sim	|Sempre igual a purchase para este evento	|pa=purchase
pr1br	|Marca do Produto	|Não	|Marca do produto |clicado	pr1br=Caloi
pr1ca	|Categoria do Produto	|Não|	Categoria e subcategorias do produto concatenadas com /, utilizar no máximo 5 níveis. Caso alguma categoria possua / em seu nome, remover antes de concatenar neste campo.|	pr1ca=Esporte%20e%20Lazer%2FCiclismo%2FBicicleta
pr1cd2	|Dimensão Personalizada 2	|Não	|Nome do lojista	|pr1cd2=Submarino
pr1cd5	|Dimensão Personalizada 5	|Sim	|Indicação se o método acordado de faturamento é CPC, CPA ou Checkout	|pr1cd5=CPC
pr1cm6	|Métrica Personalizada 6|	Sim|	Valor de exibição para o preço da oferta	|pr1cm6=509.99
pr1id	|SKU do Produto	|Sim	|Id da oferta clicada	|pr1id=628638
pr1nm|	Nome do Produto	|Sim	|Nome do produto clicado|	pr1nm=Caloi Star Wars Aro 24
pr1pr	|Preço do Produto	|Sim	|Valor do CPC ou CPA acordado para esta oferta	|pr1pr=0.50
pr1ps	|Posição do Produto|	Não|	Posição da oferta na lista onde foi clicada	|pr1ps=2
pr1qt	|Quantidade do Produto	|Sim	|Quantidade, para CPC e CPA será sempre igual a 1	|pr1qt=1
ti|	ID da Transação|	Sim	|Código único que representa a transação deste produto|	ti=14l33478
tr	|Receita	|Sim	|Valor total da transação, deve ser igual ao Preço do Produto vezes a Quantidade	|tr=0.50
cm1|	Métrica Personalizada 1	|Sim	|Contador de cliques em ofertas com negociação CPC, deve ser 1 quando CPC, 0 caso CPA ou Checkout	|cm1=1
cm2	|Métrica Personalizada 2	|Sim	|Contador de transações em ofertas com negociação CPA, deve ser 1 quando CPA, 0 caso CPC ou Checkout	|cm2=0
z	|Cache Buster	|Sim	|Deve conter uma sequência aleatória de números e estar sempre ao final da URL enviada	|z=79214683215

No caso do Checkout, onde podem haver mais de um produto na transação, os valores relativos aos produtos (pr1ca, pr1cd2, pr1cm6, pr1nm, pr1id, pr1pr, pr1ps e pr1qt) devem ser repetidos variando o prefixo pr1 (pr2, pr3, pr4, etc) para cada um dos produtos.

**tabela 2 (somente para o primeiro evento do CPA)**

Parâmetro	|Nome	|Obrigatório	|Descrição	|Exemplo
---|:----|:----|:----|:----
v	|Versão	|Sim	|Versão do protocolo, sempre igual à 1	|v=1
cid	|Id do Cliente	|Sim	|ClientID (CID), obtido a partir dos dois últimos juntos de número do cookie _ga. Caso o cookie não esteja definido, deve ser criado e salvo um valor no formado UUID v4	|cid=597491310.1483470579
tid	|Id de Acompanhamento	|Sim	|UA da propriedade do Analytics	|tid=UA-1827174-80
uid	|Id do Usuário	|Não	|Identificador do usuário logado|	uid=123234345
ua	|User Agent	|Não	|Identificador do navegador do usuário, obtido pelos headers da requisição ao servidor	|ua=Opera%2F9.80%20%28Windows%20NT%206.0%29%20Presto%2F2.12.388%20Version%2F12.14
uip	|Endereço de IP|	Sim	|Endereço de IP do usuário. Atenção! Não confundir com o endereço de IP do servidor	|uip=178.123.1.22
t	|Tipo de disparo	|Sim	|Para este caso, será sempre "event"	|t=event
dl|	Localizador do Documento	|Não	|URL da página atual	|dl=http%3A%2F%2Fwww.buscape.com.br%2Fredirect_prod
dr|	Referenciador do Documento	|Não|	URL da página anterior	|dr=https%3A%2F%2Fwww.buscape.com.br
ec|	Categoria do Evento|	Sim	|Ver a tabela de eventos	|ec=Conversao
ea	|Ação do Evento	|Sim	|Ver a tabela de eventos	|ea=CPA
el	|Rótulo do Evento	|Sim|	Ver a tabela de eventos	|el=Clique
pr1br|	Marca do Produto|	Não|	Marca do produto clicado	|pr1br=Caloi
pr1ca	|Categoria do Produto	|Não	|Categoria e subcategorias do produto concatenadas com /, utilizar no máximo 5 níveis. Caso alguma categoria possua / em seu nome, remover antes de concatenar neste campo.	|pr1ca=Esporte%20e%20Lazer%2FCiclismo%2FBicicleta
pr1cd2	|Dimensão Personalizada 2	|Não	|Nome do lojista	|pr1cd2=Submarino
pr1cd5	|Dimensão Personalizada 5	|Sim	|Indicação se o método acordado de faturamento é CPC, CPA ou Checkout	|pr1cd5=CPA
pr1cm6	|Métrica Personalizada 6	|Sim|	Valor de exibição para o preço da oferta	|pr1cm6=509.99
pr1id	|SKU do Produto|	Sim|	Id da oferta clicada	|pr1id=628638
pr1nm|	Nome do Produto	|Sim	|Nome do produto clicado	|pr1nm=Caloi Star Wars Aro 24
pr1ps	|Posição do Produto	|Não	|Posição da oferta na lista onde foi clicada	|pr1ps=2
pr1qt|	Quantidade do Produto	|Sim	|Quantidade será sempre igual a 1	|pr1qt=1
cm1	|Métrica Personalizada 1	|Sim|	Contador de cliques em ofertas com negociação CPC, deve ser 1 quando CPC, 0 caso CPA ou Checkout	|cm1=0
cm2	|Métrica Personalizada 2	|Sim|	Contador de transações em ofertas com negociação CPA, deve ser 1 quando CPA, 0 caso CPC ou Checkout	|cm2=1
z	|Cache Buster|	Sim|	Deve conter uma sequência aleatória de números e estar sempre ao final da URL enviada|	z=79214683215

Os parâmetros ec, ea e el acima, devem ser preenchidos segundo os valores da tabela de eventos:

####**tabela de eventos**

Tipo de Lead	|Categoria (ec)	|Ação (ea)	|Rótulo (el)
---|----|----|----
CPC	|Conversao	|CPC	|Clique
CPA (no redirect)	|Conversao	|CPA	|Clique
CPA (após a compra)	|Conversao	|CPA	|Compra
Checkout|	Conversao|	Checkout	|Compra

####**Exemplo de envio**
Estes dados podem ser enviados tanto via GET quanto via POST. Devido ao tamanho da requisição, recomendamos que sempre seja enviado via POST. Utilizando os dados exemplo acima, deveria ser enviado o seguinte disparo:



```
POST /collect HTTP/1.1
Host: www.google-analytics.com

v=1&cid=597491310.1483470579&tid=UA-1827174-80&uid=123234345&ua=Opera%2F9.80%20%28Windows%20NT%206.0%29%20Pres&o%2F2.12.388%20Version%2F12.14&uip=178.123.1.22&t=event&dl=http%3A%2F%2Fwww.buscape.com.br%2Fredirect_prod&dr=https%3A%2F%2Fwww.buscape.com.br&ec=Conversao&ea=CPC&el=Clique&pa=purchase&pr1br=Caloi&pr1ca=Esporte%20e%20Lazer%2FCiclismo%2FBicicleta&pr1cd2=Submarino&pr1cd5=CPC&pr1cm6=509.99&pr1id=628638&pr1nm=Caloi%20Star%20Wars%20Aro%2024&pr1pr=0.50&pr1ps=2&pr1qt=1&ti=14l33478&tr=0.50&cm1=1&cm2=0&z=79214683215

```
