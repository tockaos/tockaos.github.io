



![enter image description here](http://image.buscape.com/material/buscape.png)

# **Google Analytics**

## **Padronização de disparos**

### **Índice**

- [Objetivo](#objetivo)
- [dataLayer](#datalayer)
- [Observações](#observações)
- [Padronização HTML](#padronização-html)
	- [Qualquer Click do Site](#qualquer-click-do-site)
	- [Botões](#botões) 
- [Disparos](#disparos)
	- [Banners](#banners)
		- [Impressão do Banner](#impressão-do-banner)
		- [Click do Banner](#click-do-banner)
		- [Impressão de Listas](#impressão-de-listas)




### **Objetivo**

Para termos agilidade e precisão quando algum elemento precisa ser tagueado, enviaremos via back-end os disparos via  **dataLayer.push** ou cada elemento clicável terá atributos **data** informando ao GTM quais as variáveis a se passar . Assim, quando subir qualquer banner ou elemento novo no site, o GTM (Google Tag Manager) enviará automaticamente os dados coletados para o GA(Google Analytics). 



### **Observações**

 - Todas as informações devem ser em caixa baixa e separadas por "_" Ex: este_exemplo.

 - O disparo de impressões de Banners deve acontecer apenas na visualização do banner. Se o usuário sai do alcance do banner, não deve ser disparado mais.

-------

### **Padronização HTML**


#### **Qualquer Click do Site**

Para qualquer elemento do site que deverá ser tagueado, o HTML deverá conter os seguintes atributos:

 - data_gacategory
 - data_gaaction
 - data_galabel
 - data_gaevent

O **data_gaevent** deve vir como **event**

Ex:

```html
<a class="brand__thumb" itemprop="url" data_gaaction="click:logo" data_gacategory="header" data_gaevent="event" title="Buscapé" href="/"><img itemprop="logo" alt="Buscapé" srcset="https://imagebuscape-a.akamaihd.net/material/logo-buscape.svg" src="https://imagebuscape-a.akamaihd.net/material/buscape.png"></a>

<a class="js-subnav--link nav--link" data_galabel="tv" data_gaaction="menu_principal" data_gacategory="menu" data_gaevent="event" itemprop="url" log-cat-attribute="log-cat-attribute" log_id="2852" href="/tv"><span class="nav--link__line"></span><i class="nav--ico nav--ico-left nav--ico-large ico--tv"></i>TV<i class="nav--ico nav--ico-right ico--arrow fl-right"></i></a>
```

Assim o GTM entenderá automaticamente que esse elemento é um elemento tagueado, e enviará para o GA as informações do click.

Teremos um mapa de métricas dizendo o que será colocado em cada um desses atributos:

https://docs.google.com/spreadsheets/d/1ruAyiETsi8zgYMtXqMnReEVOkgohtqScmL8j2vTf_s8/edit?usp=sharing

Esse mapa de métricas deverá sempre ser atualizado quando algum elemento novo for inserido no site.

#### **Botões**

Em cada elemento onde for o clique de **Ir a Loja,  Compre Aqui ou Comprar**  deve-se conter os elementos:

 - data_gacategory (Categoria do evento do elemento clicado)
 - data_gaaction (Ação do evento do elemento clicado)
 - data_galabel (Rótulo  do evento do elemento clicado)
 - data_gaevent (Tipo de evento do elemento clicado)
 - data_gaidoferta (ID oferta do produto clicado)
 - data_ganomelista (Nome da Lista do produto clicado)
 - data_gadepartamento (Departamento do produto clicado)
 - data_gacategoria (Categoria do produto clicado)
 - data_gapreco (Preço do produto clicado)
 - data_gamarca (Marca do produto clicado)
 - data_galoja (Loja do produto clicado)
 - data_gaposicao (Posição do produto clicado)
 - data_gaidproduto( ID do produto)
 - data_gaselo(Selo informando algo do produto Ex: Selo de economize)
 - data_galocaldobotao(Indicativo se o botão está no corpo da página ou no topo)

O **data_gaevent** deve vir como **micro_conversao** 

```html
Ir a Loja

<a href="/redirect_prod?id=3661&amp;prod_id=231682094&amp;emp_id=1149445&amp;pos=1&amp;pg=home&amp;cn=253113018&amp;nc=12700120161031105552&amp;az=9d847f29dafc0b1b9e4de8a43bb1627c" target="_blank" title="Ir a loja" class="card--product__link" data_gaevent="micro_conversao" data_gacategory="produto" data_gaaction="micro_conversao:ir_a_loja" data_galabel="ar_condicionado_split_hi_wall_electrolux_ecoturbo_12.000_btu_/_h_frio_r410_-_220_volts" data_gaidoferta="252790505" data_ganomelista="veja_o_que_separamos_para_voce" data_gadepartamento="eletrodomesticos" data_gacategoria="ar_condicionado" data_gapreco="1499.9" data_gamarca="electrolux"  data_galoja="submarino" data_gaposicao="1" data_gaidproduto='12345' data_gaselo='economize' data_galocaldobotao='topo'>

Compre Aqui

<a data_galabel="perfume_azzaro_masculino_200_ml" data_gaaction="Card de Produto | Result de busca" data-gacategory="compre aqui" title="" data-position="12" data-preco="209.19" rel="nofollow external" data-e7click="true" data-id="164480" class="bui-product__link" href="/oferta/categoria/232010573/1156466" target="_blank" data_gaevent="micro_conversao" data_gacategory="produto" data_gaaction="micro_conversao:compre_aqui" data_gaidoferta="1231231" data_ganomelista="busca" data_gadepartamento="perfumaria_e_cosmeticos" data_gacategoria="perfume" data_gapreco="149" data_gamarca="azzaro"  data_galoja="netshoes" data_gaposicao="12" data_gaidproduto='12345' data_gaselo='economize' data_galocaldobotao='corpo_da_pagina'>

Comprar

<a data_galabel="perfume_azzaro_masculino_200_ml" data_gaaction="Card de Produto | Result de busca" data-gacategory="compre aqui" title="" data-position="12" data-preco="209.19" rel="nofollow external" data-e7click="true" data-id="164480" data_gaevent="micro_conversao" data_gacategory="produto" data_gaaction="micro_conversao:comprar" data_gaidoferta="1231231" data_ganomelista="oferta" data_gadepartamento="perfumaria_e_cosmeticos" data_gacategoria="perfume" data_gapreco="149" data_gamarca="azzaro"  data_galoja="netshoes" data_gaposicao="1" data_gaidproduto='12345' data_gaselo='economize' data_galocaldobotao='topo'>




```


### **Disparos**

#### **Banners**

No momento do clique do usuário em algum banner deve-se disparar:

##### **Impressão do Banner** 

```js
 dataLayer.push({'event':'banner_impressao', 'banner_nome':'dell', 'banner_creative':'verao_notebooks','banner_posicao':'1', 'banner_nome_lista':'melhores_ofertas_home'});

 dataLayer.push({'event':'banner_impressao', 'banner_nome':'gradiente', 'banner_creative':'gradiente_voltou','banner_posicao':'2', 'banner_nome_lista':'melhores_ofertas_home'});

 dataLayer.push({'event':'banner_impressao', 'banner_-nome':'magazine_luiza', 'banner_creative':'lu_com_voce','banner_posicao':'1', 'banner_nome_lista':'promocoes_da_lu'});

 dataLayer.push({'event':'banner_impressao', 'banner_nome':'magazine_luiza', 'banner_creative':'lu_e_sua_cozinha','banner_posicao':'2', 'banner_nome_lista':'promocoes_da_lu'});
```
Chave| Tipo de valor| Definição |Exemplo
-------- | --- | ---|---
event		| string | nome do evento |banner_impressao
banner_nome | string | nome do banner impresso|magazine_luiza
banner_creative | string | nome da promoção ou criativo | Lu_e_sua_cozinha 
banner_local |string | Local onde o banner está | topo, rodape, meio, meio_esquerda
banner_posicao 	| string |posicao do banner na lista | 1, 2, 3
banner_nome_lista | string | Nome da lista onde o banner está inserido | promocoes_da_lu, melhores_ofertas_home, sem_lista(Se não estiver em nenhuma lista)
 


##### **Click do Banner**



```js
dataLayer.push({'event':'banner_click', 'banner_nome':'dell', 'banner_creative':'verao_notebooks','banner_posicao':'1', 'banner_nome_lista':'melhores_ofertas_home'});

dataLayer.push({'event':'banner_click', 'banner_nome':'gradiente', 'banner_creative':'gradiente_voltou','banner_posicao':'2', 'banner_nome_lista':'melhores_ofertas_home'});

dataLayer.push({'event':'banner_click', 'banner_nome':'magazine_luiza', 'banner_creative':'lu_com_voce','banner_posicao':'1', 'banner_nome_lista':'promocoes_da_lu'});
 
dataLayer.push({'event':'banner_click', 'banner_nome':'magazine_luiza', 'banner_creative':'lu_e_sua_cozinha','banner_posicao':'2', 'banner_nome_lista':'promocoes_da_lu'});
```

Chave| Tipo de valor| Definição |Exemplo
--|--|--|--
event		| string | nome do evento |banner_click
banner_nome | string | nome do banner clicado|magazine_luiza
banner_creative | string | nome da promoção ou criativo | Lu_e_sua_cozinha 
banner_local |string | Local onde o banner está | topo, rodape, meio, meio_esquerda
banner_posicao 	| string |posicao do banner na lista | 1, 2, 3
banner_nome_lista | string | Nome da lista onde o banner está inserido | promocoes_da_lu, melhores_ofertas_home, sem_lista(Se não estiver em nenhuma lista)
 

-------


#### **Impressão de Listas**

- Deve ser disparada quando a lista aparece no campo visual do usuário.
- Só deve ser disparada uma vez
- Se o usuário "scrollar" até uma lista, deve acontecer o disparo igual exemplo abaixo.

``` js
 dataLayer.push({'event':'lista_impressao', 'nome_lista':'lista_de_ofertas_da_home'});
 
 dataLayer.push({'event':'lista_impressao', 'nome_lista':'ofertas_magazine_luiza'});

```



