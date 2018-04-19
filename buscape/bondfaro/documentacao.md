



![enter image description here](https://alfredojunior.files.wordpress.com/2013/04/logo-bondfaro17.png)

## **Documentação**

### **Índice**

- [O que é dataLayer?](#o-que-é-datalayer)
- [Utilização](#utilização)
	- [Exemplo](#exemplo)
- [Aplicação](#aplicação)
	- [Home](#home)
	- [Produto](#pu)
	- [Categoria](#categoria)
	- [Busca](#busca)
- [Micro Conversões](#micro-conversões)
	- [Ir a Loja](#ir-a-loja)
	- [Produto](#produto)
- [Retiradas do Site](#retiradas-do-site) 




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

#### **Exemplo**:

**Home**
```js
window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'home',
		'protocol': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017'
	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino',
		'status':'logado',
		'email':'teste@teste.com.br'
	}
}]
</script><noscript><iframe style="display:none;visibility:hidden" width="0" height="0" src="//www.googletagmanager.com/ns.html?id=GTM-P8LTKP"></iframe></noscript><script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':newDate().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src='//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);})(window,document,'script','dataLayer','GTM-P8LTKP');</script>
```

### **Aplicação**

#### **Home**

```js
window.dataLayer = window.dataLayer || [];

dataLayer = [{
	'pagina': {
		'template': 'home',
		'protocol': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile'

	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino',
		'status':'logado',
		'email':'teste@teste.com.br'
	}
}]
```

Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|--
pagina		| objeto| 
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br



#### **Produto**

```js
dataLayer = [{
	'pagina': {
		'template': 'produto',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017'

	},
	'produto' : {
		'nome':'produto A',
		'departamento':'telefonia',
		'categoria':'celular_e_smartphone',
		'id_produto':'12345',
	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino',
		'status':'logado',
		'email':'teste@teste.com.br'
	}
}] 
```

Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---
pagina		| objeto| 
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
produto.nome|string|Nome do produto | produto_a
produto.departamento|string|Nome do Departamento do produto | telefonia
produto.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br


#### **Categoria**


```js
dataLayer = [{
	'pagina': {
		'template': 'categoria',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017'
	},
	'produto':{
		'departamento' : 'celulares',
		'categoria' : 'celular_e_smartphone',
	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino',
		'status':'logado',
		'email':'teste@teste.com.br'
	}
}]

```
Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|--
pagina		| objeto| |
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
pagina.departamento|string|Departamento |telefonia
pagina.categoria|string|Categoria|celular_e_smartphone
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
produto.departamento|string|Nome do Departamento do produto | telefonia
produto.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br


#### **Busca**


```js
dataLayer = [{
	'pagina': {
		'template': 'busca',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017'
	},
	'busca':{
		'termo_buscado' : 'celular',
		'quantidade_resultados' : '1231'
	},
	'usuario': {
		'id':'12345',
		'tipo_login':'facebook',
		'idade':'26',
		'sexo':'masculino',
		'status':'logado'
	}
}]

```
Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|--
pagina		| objeto| |
pagina.template	| string| Definição da Página|home
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
busca|objeto||
busca.termo_buscado|string|O que foi procurado no campo de busca|celular
busca.quantidade_resultados|string|Quantidade dos itens pesquisados| 12313
produto.departamento|string|Departamento |telefonia
produto.categoria|string|Categoria|celular_e_smartphone
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br


### **Micro conversões**

Para cada clique em ir a loja, deve-se disparar o **push** abaixo:


#### **Ir a Loja**

```js

dataLayer.push({"event":"micro_conversao",
"micro_ga_category":"produto",
"micro_ga_action":"micro_conversao:ir_a_loja",
"micro_ga_label":"ar_condicionado_split_hi_wall_electrolux_ecoturbo_12.000_btu_/_h_frio_r410_-_220_volts",
"micro_ga_idoferta":"252790505",
"micro_ga_nomelista":"veja_o_que_separamos_para_voce",
"micro_ga_departamento":"eletrodomesticos",
"micro_ga_categoria":"ar_condicionado",
"micro_ga_preco":"1499.9",
"micro_ga_marca":"electrolux",
"micro_ga_loja":"submarino",
"micro_ga_posicao":"1",
"micro_ga_idproduto":'12345',
"micro_ga_localdobotao":'topo'
});
```


#### **Produto**

```js

dataLayer.push({"event":"micro_conversao",
"micro_ga_category":"produto",
"micro_ga_action":"micro_conversao:produto",
"micro_ga_label":"ar_condicionado_split_hi_wall_electrolux_ecoturbo_12.000_btu_/_h_frio_r410_-_220_volts"
"micro_ga_nomelista":"veja_o_que_separamos_para_voce",
"micro_ga_departamento":"eletrodomesticos",
"micro_ga_categoria":"ar_condicionado",
"micro_ga_preco":"1499.9",
"micro_ga_marca":"electrolux",
"micro_ga_posicao":"1",
"micro_ga_idproduto":'12345',
"micro_ga_localdobotao":'vitrine'
});
```

### **Retiradas do Site**

Para não haver duplicações ou Tags do GA a mais dentro do site, devem ser retiradas os seguintes scripts:

```html
<script>		
			(function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
			(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
			m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
			})(window,document,'script','//www.google-analytics.com/analytics.js','ga');
			
			ga('create', 'UA-218756-20', 'bondfaro.com.br');
			ga('set', '&uid', '');
			ga('require', 'displayfeatures');
			ga('send', 'pageview', '/Home/?tipo-pagina=Home');
		</script>


```
