
![enter image description here](http://image.buscape.com/material/buscape.png)

##**Implementação do dataLayer**

###**Índice**

- [O que é dataLayer?](#o-que-é-datalayer)
- [Utilização](#utilização)
	- [Exemplo](#exemplo)
- [Aplicação](#aplicação)
	- [Home](#home)
	- [P.U](#pu)
	- [Oferta](#oferta)
	- [Categoria](#categoria)
	- [Busca](#busca)




### **O que é dataLayer?**

A variável da camada de dados instalada tem o nome de **dataLayer**, ela é um Objeto javascript. Ela é uma variavel global criada pelo GTM(Google Tag Manager)

Utilizamos esse objeto para obter as informações sobre a página, produtos e informações diversas como por exemplo: informações de usuários, informações de anúncios, etc.  

### **Utilização**


 - A camada de Dados deve ser inserida em todas as páginas.
 - A camada de Dados deve ser preenchida com as informações corretas, assegurando assim a qualidade dos dados.
 - A camada de dados **deve sempre ser inserida antes do carregamento do GTM conforme exemplo abaixo**, pois assim, conseguimos passar as informações para o GA(Google Analytics) já que estão carregadas.
 - Todos os valores passados na camada de dados devem ser passados em caixa baixa e separados por **underline** ("**_**")
 - Ofertas são vários preços para um mesmo item
 - Itens são produtos diferentes que podem aparecer em uma lista de recomendação por exemplo

####**Exemplo**:

**Home**

```js

window.dataLayer = window.dataLayer || [];

dataLayer = [{
	'pagina': {
		'template': 'home',
		'protocol': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile'

	},
	'listas': [{
			'nome_lista':'lista_de_ofertas_da_home',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
			},
			{	
			'nome_lista':'buscape_para_voce',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
		}],
	'usuario': {
		'id':'12345',
		'tipo-login':'facebook',
		'idade':'26',
		'sexo':'masculino'
	}
}]
<noscript><iframe src="//www.googletagmanager.com/ns.html?id=GTM-W7LVSD" height="0" width="0" style="display: none; visibility: hidden;"></iframe></noscript><script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],j=d.createElement(s),dl=l!='dataLayer'?'&amp;l='+l:'';j.async=true;j.src='//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);})(window,document,'script','dataLayer','GTM-W7LVSD');</script>
```

###**Aplicação**

####**Home**

```js
window.dataLayer = window.dataLayer || [];

dataLayer = [{
	'pagina': {
		'template': 'home',
		'protocol': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile'

	},
	'listas': [{
			'nome_lista':'lista_de_ofertas_da_home',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
		},
		{	
			'nome_lista':'buscape_para_voce',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
	}],
	'usuario': {
		'id':'12345',
		'tipo-login':'facebook',
		'idade':'26',
		'sexo':'masculino'
	}
}]
```

Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---
pagina		| objeto| 
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
listas| objeto | Objeto contendo itens|
listas.lista1.nome_lista | objeto | Nome da Lista| lista_de_ofertas_da_home
listas.lista1.itens | array | |Listas contendo informações de itens|
listas.lista1.itens.nome|string|Nome do produto | produto_a
listas.lista1.itens.departamento|string|Nome do Departamento do Produto | telefonia
listas.lista1.itens.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
listas.lista1.itens.id_produto|string| número de identificação do produto | 12345
listas.lista1.itens.id_oferta|string| Número da identificação da oferta | 54321
listas.lista1.itens.sku|string| Número do SKU do Produto|a1b2c3
listas.lista1.itens.preco|string| Preço sem desconto do produto separado por ponto|53.00
listas.lista1.itens.preco_final|string|Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
listas.lista1.lista1.itens.marca|string| Marca do produto | samsumg
listas.lista1.itens.loja|string| Loja que o produto está sendo vendido| submarino
listas.lista1.itens.tem_review|boolean| Tem ou não review | **true** ou **false**
listas.lista1.itens.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
listas.lista1.itens.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
listas.lista1.itens.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
listas.lista1.itens.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
listas.lista1.itens.posicao_item|string| Posição que a oferta aparece. Se a lista for reordenada, a posição terá que seguir a ordernação. | 3
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino

####**P.U**

```js
dataLayer = [{
	'pagina': {
		'template': 'pu',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile'

	},
	'listas': [{
			'nome_lista':'lista_de_ofertas_da_pu',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
		},
		{	
			'nome_lista':'buscape_para_voce',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
	}],
	'produto' : {
		'nome':'produto A',
		'departamento':'telefonia',
		'categoria':'celular_e_smartphone',
		'id_produto':'12345',
		'ofertas': [{
			'nome':'produto A',
			'departamento':'telefonia',
			'categoria':'celular_e_smartphone',	
			'id_produto':'12345',
			'id_oferta':'abcde',
			'sku':'1a2b3c',
			'preco':'35.00',
			'preco_final':'28.00',
			'marca':'samsumg',
			'loja':'submarino',
			'tem_review': true,
			'qtd_review':'23',
			'porcentagem_avaliacao':'95%',
			'participa_promocao': true,
			'nome_promocao' : 'submarino_day',
			'posicao_oferta' : '1'
		},
		{
			'nome':'produto A',
			'departamento':'telefonia',
			'categoria':'celular_e_smartphone',
			'id_produto':'12345',
			'id_oferta':'abcde',
			'sku':'1a2b3c',
			'preco_real':'37.00',
			'preco_final':'25.00',
			'marca':'samsumg',
			'loja':'fast_shop',
			'tem_review': false,
			'qtd_review':'0',
			'porcentagem_avaliacao':'',
			'participa_promocao': false,
			'nome_promocao' : '',
			'posicao_oferta' : '2'
		}]
	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino'
	}
}] 


```


Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---
pagina		| objeto| 
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
listas| objeto | Objeto contendo itens|
listas.lista1.nome | objeto | Nome da Lista| lista_de_ofertas_da_home
listas.lista1.itens | array | |Listas contendo informações de itens|
listas.lista1.itens.nome|string|Nome do produto | produto_a
listas.lista1.itens.departamento|string|Nome do Departamento do Produto | telefonia
listas.lista1.itens.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
listas.lista1.itens.id_produto|string| número de identificação do produto | 12345
listas.lista1.itens.id_oferta|string| Número da identificação da oferta | 54321
listas.lista1.itens.sku|string| Número do SKU do Produto|a1b2c3
listas.lista1.itens.preco|string| Preço sem desconto do produto separado por ponto|53.00
listas.lista1.itens.preco_final|string| Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
listas.lista1.itens.marca|string| Marca do produto | samsumg
listas.lista1.itens.loja|string| Loja que o produto está sendo vendido| submarino
listas.lista1.itens.tem_review|boolean| Tem ou não review | **true** ou **false**
listas.lista1.itens.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
listas.lista1.itens.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
listas.lista1.itens.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
listas.lista1.itens.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
listas.lista1.itens.posicao_item|string| Posição que a oferta aparece. Se a lista for reordenada, a posição terá que seguir a ordernação. | 3
produto.nome|string|Nome do produto | produto_a
produto.departamento|string|Nome do Departamento do produto | telefonia
produto.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
produto.ofertas|string|Objeto contendo ofertas de produtos|
produto.ofertas.id_produto|string| número de identificação do produto | 12345
produto.ofertas.id_oferta|string| Número da identificação da oferta | 54321
produto.ofertas.sku|string| Número do SKU do Produto|a1b2c3
produto.ofertas.preco|string| Preço sem desconto do produto separado por ponto|53.00
produto.ofertas.preco_final|string| 
Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
produto.ofertas.marca|string| Marca do produto | samsumg
produto.ofertas.loja|string| Loja que o produto está sendo vendido| submarino
produto.ofertas.tem_review|boolean| Tem ou não review | **true** ou **false**
produto.ofertas.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
produto.ofertas.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
produto.ofertas.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
produto.ofertas.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
produto.ofertas.posicao_oferta|string| Posição que a oferta aparece. Se a lista for reordenada, a posição terá que seguir a ordernação.
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino


####**Oferta**

```js
dataLayer = [{
	'pagina': {
		'template': 'oferta',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile'

	},
	'listas': [{
			'nome_lista':'lista_de_ofertas_da_oferta',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
		},
		{	
			'nome_lista':'buscape_para_voce',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
	}],
	'produto' : {
		'nome':'produto A',
		'departamento':'',
		'categoria':'',
		'id_produto':'12345',
		'id_oferta':'abcde',
		'sku':'1a2b3c',
		'preco':'35.00',
		'preco_final':'28.00',
		'marca':'samsumg',
		'loja':'submarino',
		'tem_review': true,
		'qtd_review':'23',
		'porcentagem_avaliacao':'95%',
		'participa_promocao': true,
		'nome_promocao' : 'submarino_day',
		'posicao_oferta' : '1'
	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino'
	}
}]
```



Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---
pagina		| objeto| 
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
listas| objeto | Objeto contendo itens|
listas.lista1.nome | objeto | Nome da Lista| lista_de_ofertas_da_home
listas.lista1.itens | array | |Listas contendo informações de itens|
listas.lista1.itens.nome|string|Nome do produto | produto_a
listas.lista1.itens.departamento|string|Nome do Departamento do Produto | telefonia
listas.lista1.itens.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
listas.lista1.itens.id_produto|string| número de identificação do produto | 12345
listas.lista1.itens.id_oferta|string| Número da identificação da oferta | 54321
listas.lista1.itens.sku|string| Número do SKU do Produto|a1b2c3
listas.lista1.itens.preco|string| Preço sem desconto do produto separado por ponto|53.00
listas.lista1.itens.preco_final|string| 
Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
listas.lista1.itens.marca|string| Marca do produto | samsumg
listas.lista1.itens.loja|string| Loja que o produto está sendo vendido| submarino
listas.lista1.itens.tem_review|boolean| Tem ou não review | **true** ou **false**
listas.lista1.itens.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
listas.lista1.itens.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
listas.lista1.itens.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
listas.lista1.itens.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
listas.lista1.itens.posicao_item|string| Posição que a oferta aparece. Se a lista for reordenada, a posição terá que seguir a ordernação. | 3
produto.nome|string|Nome do produto | produto_a
produto.departamento|string|Nome do Departamento do produto | telefonia
produto.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
produto.id_produto|string| número de identificação do produto | 12345
produto.id_oferta|string| Número da identificação da oferta | 54321
produto.sku|string| Número do SKU do Produto|a1b2c3
produto.preco|string| Preço sem desconto do produto separado por ponto|53.00
produto.preco_final|string| Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
produto.marca|string| Marca do produto | samsumg
produto.loja|string| Loja que o produto está sendo vendido| submarino
produto.tem_review|boolean| Tem ou não review | **true** ou **false**
produto.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
produto.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
produto.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
produto.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino

#### **Categoria**


```js
dataLayer = [{
	'pagina': {
		'template': 'categoria',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'departamento' : 'telefonia',
		'categoria' : 'celular_e_smartphone',
	},
	'listas': [{
			'nome_lista':'lista_de_ofertas_da_categoria',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
		},
		{	
			'nome_lista':'buscape_para_voce',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
	}],
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino'
	}
}]

```
Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---
pagina		| objeto| |
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
pagina.departamento|string|Departamento |telefonia
pagina.categoria|string|Categoria|celular_e_smartphone
listas| objeto | Objeto contendo itens|
listas.lista1.nome | objeto | Nome da Lista| lista_de_ofertas_da_home
listas.lista1.itens | array | |Listas contendo informações de itens|
listas.lista1.itens.nome|string|Nome do produto | produto_a
listas.lista1.itens.departamento|string|Nome do Departamento do Produto | telefonia
listas.lista1.itens.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
listas.lista1.itens.id_produto|string| número de identificação do produto | 12345
listas.lista1.itens.id_oferta|string| Número da identificação da oferta | 54321
listas.lista1.itens.sku|string| Número do SKU do Produto|a1b2c3
listas.lista1.itens.preco|string| Preço sem desconto do produto separado por ponto|53.00
listas.lista1.itens.preco_final|string| Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
listas.lista1.itens.marca|string| Marca do produto | samsumg
listas.lista1.itens.loja|string| Loja que o produto está sendo vendido| submarino
listas.lista1.itens.tem_review|boolean| Tem ou não review | **true** ou **false**
listas.lista1.itens.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
listas.lista1.itens.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
listas.lista1.itens.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
listas.lista1.itens.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
listas.lista1.itens.posicao_item|string| Posição que a oferta aparece. Se a lista for reordenada, a posição terá que seguir a ordernação. | 3
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino


#### **Busca**


```js
dataLayer = [{
	'pagina': {
		'template': 'busca',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile'
	},
	'busca':{
		'termo_buscado' : 'celular',
		'quantidade_resultados' : '1231'
	},	
	'listas': [{
			'nome_lista':'lista_de_ofertas_da_categoria',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
		},
		{	
			'nome_lista':'buscape_para_voce',
			'itens': [{
				'nome':'produto C',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',	
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco':'35.00',
				'preco_final':'28.00',
				'marca':'apple',
				'loja':'submarino',
				'tem_review': true,
				'qtd_review':'23',
				'porcentagem_avaliacao':'95%',
				'participa_promocao': true,
				'nome_promocao' : 'submarino_day',
				'posicao_oferta' : '1'
			},
			{
				'nome':'produto D',
				'departamento':'telefonia',
				'categoria':'celular_e_smartphone',
				'id_produto':'54321',
				'id_oferta':'edcba',
				'sku':'c3b2a1',
				'preco_real':'37.00',
				'preco_final':'25.00',
				'marca':'samsumg',
				'loja':'fast_shop',
				'tem_review': false,
				'qtd_review':'0',
				'porcentagem_avaliacao':'',
				'participa_promocao': false,
				'nome_promocao' : '',
				'posicao_oferta' : '2'
			}]
	}],
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino'
	}
}]

```
Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---
pagina		| objeto| |
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
pagina.departamento|string|Departamento |telefonia
pagina.categoria|string|Categoria|celular_e_smartphone
busca|objeto||
busca.termo_buscado|string|O que foi procurado no campo de busca|celular
busca.quantidade_resultados|string|Quantidade dos itens pesquisados| 12313
listas| objeto | Objeto contendo itens|
listas.lista1.nome | objeto | Nome da Lista| lista_de_ofertas_da_home
listas.lista1.itens | array | |Listas contendo informações de itens|
listas.lista1.itens.nome|string|Nome do produto | produto_a
listas.lista1.itens.departamento|string|Nome do Departamento do Produto | telefonia
listas.lista1.itens.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
listas.lista1.itens.id_produto|string| número de identificação do produto | 12345
listas.lista1.itens.id_oferta|string| Número da identificação da oferta | 54321
listas.lista1.itens.sku|string| Número do SKU do Produto|a1b2c3
listas.lista1.itens.preco|string| Preço sem desconto do produto separado por ponto|53.00
listas.lista1.itens.preco_final|string| Preço com desconto se houver. Senão é passo o valor normal Separado por ponto|28.00
listas.lista1.itens.marca|string| Marca do produto | samsumg
listas.lista1.itens.loja|string| Loja que o produto está sendo vendido| submarino
listas.lista1.itens.tem_review|boolean| Tem ou não review | **true** ou **false**
listas.lista1.itens.qtd_review|string| Quantidade de reviews. Se não tiver, é passado o valor 0 | 7
listas.lista1.itens.porcentagem_avaliacao|string| Porcentagem de avaliação . Se não tiver, é passado 0 | 97
listas.lista1.itens.participa_promocao|boolean| Verificação se o produto participa ou não de uma promoção | true
listas.lista1.itens.nome_promocao|string| Nome da Promoção que o produto participa. Se não houver participação é passado em branco |submarino_day
listas.lista1.itens.posicao_item|string| Posição que a oferta aparece. Se a lista for reordenada, a posição terá que seguir a ordernação. | 3
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino