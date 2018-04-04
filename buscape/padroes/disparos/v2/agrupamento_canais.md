





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



### **Objetivo**

Para termos agilidade e precisão quando algum elemento precisa ser tagueado, enviaremos via back-end os disparos via  **dataLayer.push** ou cada elemento clicável terá atributos **data** informando ao GTM quais as variáveis a se passar . Assim, quando subir qualquer banner ou elemento novo no site, o GTM (Google Tag Manager) enviará automaticamente os dados coletados para o GA(Google Analytics). 



### **Observações**

 - Todas as informações devem ser em caixa baixa e separadas por "_" Ex: este_exemplo.

 - O disparo de impressões de Banners deve acontecer apenas na visualização do banner. Se o usuário sai do alcance do banner, não deve ser disparado mais.

-------

### **Padronização HTML**


#### **Qualquer Click do Site**

Para qualquer elemento do site que deverá ser tagueado, o HTML deverá conter os seguintes atributos:

 - data_ga_category
 - data_ga_action
 - data_ga_label
 - data_ga_event

O **data_gaevent** deve vir como **event**

Ex:

```html
<a class="brand__thumb" itemprop="url" data_ga_action="click:logo" data_ga_category="header" data_ga_event="event" title="Buscapé" href="/"><img itemprop="logo" alt="Buscapé" srcset="https://imagebuscape-a.akamaihd.net/material/logo-buscape.svg" src="https://imagebuscape-a.akamaihd.net/material/buscape.png"></a>

<a class="js-subnav--link nav--link" data_ga_label="tv" data_ga_action="menu_principal" data_ga_category="menu" data_ga_event="event" itemprop="url" log-cat-attribute="log-cat-attribute" log_id="2852" href="/tv"><span class="nav--link__line"></span><i class="nav--ico nav--ico-left nav--ico-large ico--tv"></i>TV<i class="nav--ico nav--ico-right ico--arrow fl-right"></i></a>
```

Assim o GTM entenderá automaticamente que esse elemento é um elemento tagueado, e enviará para o GA as informações do click.

Teremos um mapa de métricas dizendo o que será colocado em cada um desses atributos:

https://docs.google.com/spreadsheets/d/1ruAyiETsi8zgYMtXqMnReEVOkgohtqScmL8j2vTf_s8/edit?usp=sharing

Esse mapa de métricas deverá sempre ser atualizado quando algum elemento novo for inserido no site.

#### **Botões**

Em cada elemento onde for o clique de **Ir a Loja,  Compre Aqui ou Comprar**  deve-se conter os elementos:

 - data_ga_category (Categoria do evento do elemento clicado)
 - data_ga_action (Ação do evento do elemento clicado)
 - data_ga_label (Rótulo  do evento do elemento clicado)
 - data_ga_event (Tipo de evento do elemento clicado)
 - data_ga_idoferta (ID oferta do produto clicado)
 - data_ga_nomelista (Nome da Lista do produto clicado)
 - data_ga_departamento (Departamento do produto clicado)
 - data_ga_categoria (Categoria do produto clicado)
 - data_ga_preco (Preço do produto clicado)
 - data_ga_marca (Marca do produto clicado)
 - data_ga_loja (Loja do produto clicado)
 - data_ga_posicao (Posição do produto clicado)
 - data_ga_idproduto( ID do produto)
 - data_ga_selo(Selo informando algo do produto Ex: Selo de economize)
 - data_ga_localdobotao(Indicativo se o botão está no corpo da página ou no topo)

O **data_gaevent** deve vir como **micro_conversao** 

```html
Ir a Loja

<a href="/redirect_prod?id=3661&amp;prod_id=231682094&amp;emp_id=1149445&amp;pos=1&amp;pg=home&amp;cn=253113018&amp;nc=12700120161031105552&amp;az=9d847f29dafc0b1b9e4de8a43bb1627c" target="_blank" title="Ir a loja" class="card--product__link" data_ga_event="micro_conversao" data_ga_category="produto" data_ga_action="micro_conversao:ir_a_loja" data_ga_label="ar_condicionado_split_hi_wall_electrolux_ecoturbo_12.000_btu_/_h_frio_r410_-_220_volts" data_ga_idoferta="252790505" data_ga_nomelista="veja_o_que_separamos_para_voce" data_ga_departamento="eletrodomesticos" data_ga_categoria="ar_condicionado" data_ga_preco="1499.9" data_ga_marca="electrolux"  data_ga_loja="submarino" data_ga_posicao="1" data_ga_idproduto='12345' data_ga_selo='economize' data_ga_localdobotao='topo'>

Compre Aqui

<a data_ga_label="perfume_azzaro_masculino_200_ml" data_ga_action="Card de Produto | Result de busca" data_ga_category="compre aqui" title="" rel="nofollow external" data-e7click="true"  class="bui-product__link" href="/oferta/categoria/232010573/1156466" target="_blank" data_ga_event="micro_conversao" data_ga_category="produto" data_ga_action="micro_conversao:compre_aqui" data_ga_idoferta="1231231" data_ga_nomelista="busca" data_ga_departamento="perfumaria_e_cosmeticos" data_ga_categoria="perfume" data_ga_preco="149" data_ga_marca="azzaro"  data_ga_loja="netshoes" data_ga_posicao="12" data_ga_idproduto='12345' data_ga_selo='economize' data_ga_localdobotao='corpo_da_pagina'>

Comprar

<a data_ga_label="perfume_azzaro_masculino_200_ml" title=""  rel="nofollow external" data-e7click="true" data_ga_event="micro_conversao" data_ga_category="produto" data_ga_action="micro_conversao:comprar" data_ga_idoferta="1231231" data_ga_nomelista="oferta" data_ga_departamento="perfumaria_e_cosmeticos" data_ga_categoria="perfume" data_ga_preco="149" data_ga_marca="azzaro"  data_ga_loja="netshoes" data_ga_posicao="1" data_ga_idproduto='12345' data_ga_selo='economize' data_ga_localdobotao='topo'>


```



