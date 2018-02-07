![enter image description here](http://image.buscape.com/material/buscape.png)

# **Google Analytics**

## **Padronização de disparos**

### **Índice**

- [Objetivo](#objetivo)
- [dataLayer](#datalayer)
- [Observações](#observações)
- [Qualquer Click do Site](#qualquer-click-do-site)
- [Banners](#banners)
	- [Impressão do Banner](#impressão-do-banner)
	- [Click do Banner](#click-do-banner)
- [Botões](#botões)
- [Impressão de Listas](#impressão-de-listas)




### **Objetivo**

Para termos agilidade e precisão quando algum elemento precisa ser tagueado, enviaremos via back-end os disparos via  **dataLayer.push**. Assim, quando subir qualquer banner ou elemento novo no site, o GTM (Google Tag Manager) enviará automaticamente os dados coletados para o GA(Google Analytics). 


### **dataLayer**

dataLayer é uma variável global criada dentro do GTM. Ela é a camada de dados que usaremos para obter as informações de cada página, produto, listas, etc
Usaremos o disparo de dataLayer.push para enviar dados de cliques, acessos ou interações para camada de dados. Ex:


   ```js
dataLayer.push({'event':'ga_event','eventCategory':'header','eventAction':'click:logo','eventLabel':''});
```


### **Observações**

 - Todas as informações devem ser em caixa baixa e separadas por "_" Ex: este_exemplo.

 - O disparo de impressões de Banners deve acontecer apenas na visualização do banner. Se o usuário sai do alcance do banner, não deve ser disparado mais.

-------

### **Qualquer Click do Site**

Para qualquer elemento do site que deverá ser tagueado, o HTML deverá conter os seguintes atributos:

 - data_gacategory
 - data_gaaction
 - data_galabel
 - data_gaevent

Ex:

```html
<a class="brand__thumb" itemprop="url" data-gaaction="click:logo" data-gacategory="header" data-gaevent="event" title="Buscapé" href="/"><img itemprop="logo" alt="Buscapé" srcset="https://imagebuscape-a.akamaihd.net/material/logo-buscape.svg" src="https://imagebuscape-a.akamaihd.net/material/buscape.png"></a>

<a class="js-subnav--link nav--link" data-galabel="tv" data-gaaction="menu_principal" data-gacategory="menu" data-gaevent="event" itemprop="url" log-cat-attribute="log-cat-attribute" log_id="2852" href="/tv"><span class="nav--link__line"></span><i class="nav--ico nav--ico-left nav--ico-large ico--tv"></i>TV<i class="nav--ico nav--ico-right ico--arrow fl-right"></i></a>
```

Assim o GTM entenderá automaticamente que esse elemento é um elemento tagueado, e enviará para o GA as informações do click.

Teremos um mapa de métricas dizendo o que será colocado em cada um desses atributos:

https://docs.google.com/spreadsheets/d/1ruAyiETsi8zgYMtXqMnReEVOkgohtqScmL8j2vTf_s8/edit?usp=sharing

Esse mapa de métricas deverá sempre ser atualizado quando algum elemento novo for inserido no site.

### **Banners**

No momento do clique do usuário em algum banner deve-se disparar:

#### **Impressão do Banner** 

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
 


#### **Click do Banner**



```js
dataLayer.push({'event':'banner_click', 'banner_nome':'dell', 'banner_creative':'verao_notebooks','banner_posicao':'1', 'banner_nome_lista':'melhores_ofertas_home'});

dataLayer.push({'event':'banner_click', 'banner_nome':'gradiente', 'banner_creative':'gradiente_voltou','banner_posicao':'2', 'banner_nome_lista':'melhores_ofertas_home'});

dataLayer.push({'event':'banner_click', 'banner_nome':'magazine_luiza', 'banner_creative':'lu_com_voce','banner_posicao':'1', 'banner_nome_lista':'promocoes_da_lu'});
 
dataLayer.push({'event':'banner_click', 'banner_nome':'magazine_luiza', 'banner_creative':'lu_e_sua_cozinha','banner_posicao':'2', 'banner_nome_lista':'promocoes_da_lu'});
```

Chave| Tipo de valor| Definição |Exemplo
-------- | --- | ---|---
event		| string | nome do evento |banner_click
banner_nome | string | nome do banner clicado|magazine_luiza
banner_creative | string | nome da promoção ou criativo | Lu_e_sua_cozinha 
banner_local |string | Local onde o banner está | topo, rodape, meio, meio_esquerda
banner_posicao 	| string |posicao do banner na lista | 1, 2, 3
banner_nome_lista | string | Nome da lista onde o banner está inserido | promocoes_da_lu, melhores_ofertas_home, sem_lista(Se não estiver em nenhuma lista)
 

-------
### **Botões**

No momento do clique do usuário em **Ir a Loja,  Compre Aqui ou Comprar**  em **qualquer lugar do site**, deve-se disparar:

```js
dataLayer.push({'event':'botao','tipo_botao':'ir_a_loja', 'id_oferta':'12345','nome_lista':'notebook_imperdivel','departamento':'telefonia', 'categoria':'celular_e_smartphone', 'preco':'69.00','marca':'samsumg','loja':'submarino','posicao':'30',''});

dataLayer.push({'event':'botao','tipo_botao':'compre_aqui', 'id_oferta':'12345','nome_lista':'notebook_imperdivel','departamento':'telefonia', 'categoria':'celular_e_smartphone', 'preco':'69.00','marca':'samsumg','loja':'submarino','posicao':'30',''});

dataLayer.push({'event':'botao','tipo_botao':'comprar', 'id_oferta':'12345','nome_lista':'notebook_imperdivel','departamento':'telefonia', 'categoria':'celular_e_smartphone', 'preco':'69.00','marca':'samsumg','loja':'submarino','posicao':'1',''});
```

Chave| Tipo de valor| Definição |Exemplo
-------- | --- | ---|--
event		| string | Evento disparado 		|botao
tipo_botao	| string | Tipo de botão clicado 		|ir_a_loja
id_oferta 	| string | ID da oferta do item disparado |123456
nome_lista | string | Nome da lista em que o produto está inserido.
departamento | string | Departamento do produto clicado | telefonia
categoria | string | categoria do produto clicado | celular_e_smartphone

----------


### **Impressão de Listas**

- Deve ser disparada quando a lista aparece no campo visual do usuário.
- Só deve ser disparada uma vez
- Se o usuário "scrollar" até uma lista, deve acontecer o disparo igual exemplo abaixo.

```js
 dataLayer.push({'event':'lista_impressao', 'nome_lista':'lista_de_ofertas_da_home'});
 
 dataLayer.push({'event':'lista_impressao', 'nome_lista':'ofertas_magazine_luiza'});

