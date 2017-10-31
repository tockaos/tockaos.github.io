![enter image description here](http://image.buscape.com/material/buscape.png)

#**Google Analytics**

-------
##**Padronização de disparos**


###**Objetivo**

Para termos agilidade e precisão quando algum elemento precisa ser tagueado, enviaremos via back-end os disparos via  **dataLayer.push**. Assim, quando subir qualquer banner ou elemento novo no site, o GTM (Google Tag Manager) enviará automaticamente os dados coletados para o GA(Google Analytics). 


###**dataLayer**

dataLayer é uma variável global criada dentro do GTM. Ela é a camada de dados que usaremos para obter as informações de cada página, produto, listas, etc
Usaremos o disparo de dataLayer.push para enviar dados de cliques, acessos ou interações para camada de dados. Ex:


    dataLayer.push({'event':'sucesso', 'tipo-sucesso':'transacao'});

Esse disparo acima, seria enviado quando o usuário chegasse a tela de Transação efetuada. O GTM receberia esse evento e dispararia dados para o GA informando que a transação foi efetuada.

###**Observações**

 - Todas as informações devem ser em caixa baixa e separadas por "_" Ex: este_exemplo.
 - Para que os dados de disparos de clicks funcionem é necessário que seja implementada a camada de dados de lista.
 - O disparo de impressões de Banners deve acontecer apenas na visualização do banner. Se o usuário sai do alcance do banner, não deve ser disparado mais.

-------

###**Banners**

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

####**Ir a Loja**

No momento do clique do usuário em Ir a loja em **qualquer lugar do site**, deve-se disparar:

```js
dataLayer.push({'event':'botao','tipo_botao':'ir_a_loja', 'id_oferta':'12345'});

dataLayer.push({'event':'botao','tipo-botao':'ir_a_loja', 'id_oferta':'123123145'});
```

Chave| Tipo de valor| Definição |Exemplo
-------- | --- | ---
event		| string | Evento disparado 		|botao
tipo_botao	| string | Tipo de botão clicado 		|ir-a-loja
id_oferta 	| string | ID da oferta do item disparado |123456




####**Compre Aqui**


No momento do clique do usuário em compre aqui em **qualquer lugar do site**, deve-se disparar:


```js
      
dataLayer.push({'event':'botao','tipo_botao':'compre_aqui', 'id_oferta':'12345'});

dataLayer.push({'event':'botao','tipo-botao':'compre_aqui', 'id_oferta':'312123'});
```

Chave| Tipo de valor| Definição |Exemplo
-------- | --- | ---
event		| string | Evento disparado 		|botao
tipo_botao	| string | Tipo de botão clicado 		|compre_aqui
id_oferta 	| string | ID da oferta do item disparado |123456



####**Comprar**

No momento do clique do usuário em comprar aqui em **qualquer página de oferta**, deve-se disparar:

```js
dataLayer.push({'event':'botao','tipo_botao':'comprar', 'id_oferta':'12345'});

dataLayer.push({'event':'botao','tipo-botao':'comprar', 'id_oferta':'1233123145'});
```
Chave| Tipo de valor| Definição |Exemplo
-------- | --- | ---
event		| string | Evento disparado 		|botao
tipo_botao	| string | Tipo de botão clicado 		|comprar
id_oferta 	| string | ID da oferta do item disparado |123456



----------


###**Login**

Adicionar os seguintes disparos quando o usuário se logar:

```html
dataLayer.push({'event':'sucesso', 'tipo-sucesso':'login', 'tipo-login':'facebook'});
```


###**Cadastro**

Adicionar os seguintes disparos quando o usuário se cadastrar:

```js
dataLayer.push({'event':'sucesso', 'tipo-sucesso':'cadastro'});
```



