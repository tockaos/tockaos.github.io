




![enter image description here](http://image.buscape.com/material/buscape.png)

## **Implementação do dataLayer**

### **Índice**

- [O que é dataLayer?](#o-que-é-datalayer)
- [Utilização](#utilização)
	- [Exemplo](#exemplo)
- [Aplicação](#aplicação)
	- [Home](#home)
	- [Especiais](#especiais)
	- [P.U](#pu)
	- [Oferta](#oferta)
	- [Categoria](#categoria)
	- [Busca](#busca)
	- [Carrinho](#carrinho)




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
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'
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
<noscript><iframe src="//www.googletagmanager.com/ns.html?id=GTM-W7LVSD" height="0" width="0" style="display: none; visibility: hidden;"></iframe></noscript><script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],j=d.createElement(s),dl=l!='dataLayer'?'&amp;l='+l:'';j.async=true;j.src='//www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);})(window,document,'script','dataLayer','GTM-W7LVSD');</script>
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
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'

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
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br

#### **Especiais**

```js
window.dataLayer = window.dataLayer || [];

dataLayer = [{
	'pagina': {
		'template': 'paginas_especiais',
		'protocol': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'

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
pagina.template	| string| Definição da Página|paginas_especiais
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br

#### **P.U**

```js
dataLayer = [{
	'pagina': {
		'template': 'pu',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'

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
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
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


#### **Oferta**

```js
dataLayer = [{
	'pagina': {
		'template': 'oferta',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'mobile',
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'

	},
	'produto' : {
		'nome':'produto A',
		'departamento':'telefonia',
		'categoria':'celular_e_smartphone',
		'id_produto':'12345',
		'preco_boleto':'35.00',
		'preco_a_vista':'34.00'
		'marca':'samsumg',
		'loja':'submarino'
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
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
produto.nome|string|Nome do produto | produto_a
produto.departamento|string|Nome do Departamento do produto | telefonia
produto.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
produto.id_produto|string| número de identificação do produto | 12345
produto.preco_boleto|string| Preço sem desconto do produto separado por ponto|53.00
produto.preco_a_vista|string| Preço sem desconto do produto separado por ponto|52.00
produto.marca|string| Marca do produto | samsumg
produto.loja|string| Loja que o produto está sendo vendido| submarino
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
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'
	},
	'produto':{
		'departamento' : 'telefonia',
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
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
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
		'tipo' : 'dia_dos_pais_2017',
		'origem_busca':'chaordic'
	},
	'busca':{
		'termo_buscado' : 'celular',
		'quantidade_resultados' : '1231'
	},
	'produto':{
		'departamento' : 'telefonia',
		'categoria' : 'celular_e_smartphone',
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
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
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



####  **Carrinho**

```js
dataLayer = [{
	'pagina': {
		'template': 'carrinho',
		'protocolo': 'http:',
		'referrer': 'www.uol.com.br',
		'dispositivo'  : 'desktop',
		'tipo' : '',
		'origem_busca':'chaordic'

	},
	'produto' : {
		'nome':'produto A',
		'departamento':'telefonia',
		'categoria':'celular_e_smartphone',
		'id_produto':'12345',
		'preco_boleto':'35.00',
		'preco_a_vista':'34.00'
		'marca':'samsumg',
		'loja':'submarino'
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
pagina.tipo| string| Qual o tipo da página quando ela for especial.| dia_dos_pais_2017, dia_das_criancas
pagina.origem_busca| string | Se passou pela busca da Chaordic ou do Buscapé | chaordic, buscape
produto.nome|string|Nome do produto | produto_a
produto.departamento|string|Nome do Departamento do produto | telefonia
produto.categoria|string| Nome da Categoria do Produto | celular_e_smarthphone
produto.id_produto|string| número de identificação do produto | 12345
produto.preco_boleto|string| Preço sem desconto do produto separado por ponto|53.00
produto.preco_a_vista|string| Preço sem desconto do produto separado por ponto|52.00
produto.marca|string| Marca do produto | samsumg
produto.loja|string| Loja que o produto está sendo vendido| submarino
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuário|teste@teste.com.br
