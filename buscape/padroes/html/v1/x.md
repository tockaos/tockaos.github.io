![enter image description here](http://image.buscape.com/material/buscape.png)

#**Google Analytics**

-------------------
##**Padronização de HTML**


###**Objetivo**

Para termos agilidade e precisão quando algum elemento precisa ser tagueado, padronizaremos o HTML para conter atributos informando qual seu tipo de elemento e disparos **dataLayer.push**. Assim, quando subir qualquer banner ou elemento novo no site, o GTM (Google Tag Manager) tagueará automaticamente esses elementos. 


####**dataLayer**

dataLayer é uma váriavel global criado dentro do GTM. Ela é a camada de dados que usaremos para obter as informações de cada página, produto, listas. 
Usaremos o disparo de dataLayer.push para enviar dados de cliques, acessos para essa camada. Ex:

```s
dataLayer.push({'event':'sucesso', 'tipo-sucesso':'transacao'});
```


###**Banners**

Adicionar em todos os banners os seguintes atributos:

```html
<img 
data-gtm-type=banner
data-gtm-category=[local-do-banner]
data-gtm-action=banner:[nome-do-banner]
data-gtm-label=[url-do-banner]
</img>
```

####**Conclusão dos banners**

Com a implementação desses atributos, quando subir o banner, teremos automaticamente os dados indo para o GA. Assim podemos ver qual campanha de  qual página está trazendo mais interesse(menor bounce rate, maior tempo de visualização da página, etc.)



![enter image description here](http://tockaos.github.io/buscape/padroes/html/img/banner.jpg)



### **Botões**

Adicionar os seguintes disparos aos botoes:

####**Ir a Loja**

```js
dataLayer.push({'event':'botao', 'tipo-botao':'ir-a-loja', 'lojista', 'magazine-luiza'});

```

####**Compre Aqui**

![Compre Aqui](http://tockaos.github.io/buscape/padroes/html/img/compre-aqui.jpg)

> Quando tivermos esse disparo e a camada de dados de lista, podemos cruzar o SKU passado o disparo com todos os outros disparos, ou seja, iremos ter:

 - Produtos mais clicados
 - Categorias mais clicadas (Se a categoria estiver sendo passada nas listas) 
 - Lojistas mais clicados (Se o lojista estiver sendo passada nas listas)

```js

dataLayer.push({'event':'botao', 'tipo-botao':'ir-a-loja', 'lojista', 'magazine-luiza', 'sku':'[SKU-DO-PRODUTO]'});

```

####**Comprar**

![Comprar](http://tockaos.github.io/buscape/padroes/html/img/comprar.jpg)

>Quando tivermos esse disparo e a camada de dados de lista, podemos cruzar o SKU passado o disparo com todos os outros disparos, ou seja, iremos ter:

  - Produtos mais clicados
  - Categorias mais clicadas (Se a categoria estiver sendo passada nas listas) 
  - Lojistas mais clicados (Se o lojista estiver sendo passada nas listas)

```js
dataLayer.push({'event':'botao', 'tipo-botao':'ir-a-loja', 'lojista', 'magazine-luiza', 'sku':'[SKU-DO-PRODUTO]'});

```

####**Conclusão dos botões Compre-aqui e Comprar**

Com esses disparos implementados, teremos um inicio de funil de pessoas que clicaram em determinado produto e teremos dados de qual a marca que as pessoas mais clicam e param na 2 página, ou a categoria que mais passa, ou o lojista que menos é clicado, entre outros.

OBS:

 - Não temos SKU em todos os nossos produtos, é necessário ser implementado para ligarmos os produtos clicados aos da camada de dados.

----------


###**Login**

Adicionar os seguintes disparos quando o usuário se logar:

```js
dataLayer.push({'event':'sucesso', 'tipo-sucesso':'login', 'tipo-login':'facebook'});

```

###**Cadastro**

Adicionar os seguintes disparos quando o usuário se cadastrar:

```js
dataLayer.push({'event':'sucesso', 'tipo-sucesso':'cadastro'});

```


####**Conclusão de Login e Cadastro**

Com os disparos de sucesso de login e cadastro, poderemos acompanhar o fluxo do usuário e saber mais sobre ele. Devemos passar na camada a **idade, o sexo, o estado**, etc, para fazer listas de remarketing segmentadas:

**Ex:  Produto tal são mais vistos por pessoas do sexo masculino de 20-30 anos**