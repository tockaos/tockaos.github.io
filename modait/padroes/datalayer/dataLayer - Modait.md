


![enter image description here](https://www.cupomdescontohoje.com.br/logomarcas/modait.png)



## **Implementação do dataLayer**



### **Índice**



- [O que é dataLayer?](#o-que-é-datalayer)

- [Utilização](#utilização)

	- [Exemplo](#exemplo)

- [Aplicação](#aplicação)

	- [Home](#home)
	- [Shop](#shop)
	- [Vista o Look](#vista-o-look)
	- [Moods](#moods)
	- [Dicas](#dicas)
	- [Tutoriais de Beleza](#tutoriais-de-beleza)
	- [Blogs](#blogs)
	- [Marcas](#marcas)
 
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

```JS

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
		'email': 'teste@teste.com.br'
	}
}]

<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src='https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);})(window,document,'script','dataLayer','GTM-KXWGLVC');</script>

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
		'email': 'teste@teste.com.br'
	}
}]
```

Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
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
usuario.email|string|email do usuario| teste@teste.com.br


#### **Shop**

```js

window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'shop',
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
		'email': 'teste@teste.com.br'
	}
}]
```

Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
pagina.template	| string| Definição da Página|shop
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuario| teste@teste.com.br

#### **Vista  o Look**

```js

window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'vista_o_look',
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
		'email': 'teste@teste.com.br'
	}
}]
```


Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
pagina.template	| string| Definição da Página|vista_o_look
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuario| teste@teste.com.br

#### **Moods**

```js

window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'shop',
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
		'email': 'teste@teste.com.br'
	}
}]
```


Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
pagina.template	| string| Definição da Página|shop
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuario| teste@teste.com.br


#### **Dicas**

```js

window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'dicas',
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
		'email': 'teste@teste.com.br'
	}
}]
```


Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
pagina.template	| string| Definição da Página|shop
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuario| teste@teste.com.br

#### **Tutoriais de Beleza**

```js

window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'tutoriais_de_beleza',
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
		'email': 'teste@teste.com.br'
	}
}]
```


Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
pagina.template	| string| Definição da Página|shop
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuario| teste@teste.com.br


#### **Blogs**

```js

window.dataLayer = window.dataLayer || [];
dataLayer = [{
	'pagina': {
		'template': 'blogs',
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
		'email': 'teste@teste.com.br'
	}
}]
```


Chave| Tipo de valor|Descrição |Exemplo
-------- | --- | ---|---|
pagina		| objeto| ||
pagina.template	| string| Definição da Página|shop
pagina.protocolo 	| string | Protocolo de requisição|https:// ou http://
pagina.referrer| string | referral do acesso|www.uol.com.br
pagina.dispositivo | string | Dispositivo de acesso|mobile, desktop, tablet
usuario|objeto|Objeto contendo informações do usuário|
usuario.id|string| ID atribuido ao usuario quando ele estiver logado | 3121312
usuario.tipo_login| string| Meio que o usuário acessou o site| facebook ou google ou email
usuario.idade| string | Idade do usuário | 26
usuario.sexo | string | Sexo do usuário | masculino ou feminino
usuario.status|string| Se está logado ou não| logado, nao_logado
usuario.email|string|email do usuario| teste@teste.com.br

