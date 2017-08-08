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

-------

###**Banners**

![enter image description here](http://tockaos.github.io/buscape/padroes/html/img/banner.jpg)

No momento do clique do usuário em algum banner deve-se disparar:


    dataLayer.push({'event':'banner', 'local-banner':'home', 'posicao-banner', 'topo-esquerda','nome-banner':'dia-dos-pais','url-banner':'http://www.buscape.com.br/geladeira-refrigerador'});


Chave| Tipo de valor| Exemplo
-------- | --- | ---
event		| string | banner
lobal-banner| string | home, p.u, categoria
posicao-banner 	| string | topo-esquerda, meio-esquerda, rodape-direita
url-banner |string| http://www.buscape.com.br/geladeira-refrigerador

####**Conclusão da implementação do atributos HTML dos banners**

Com a implementação desses atributos, quando subir o banner, teremos automaticamente os dados indo para o GA. Assim podemos ver qual campanha de  qual página está trazendo mais interesse(menor bounce rate, maior tempo de visualização da página, etc.)


-------
### **Botões**

####**Ir a Loja**

![Ir a Loja](http://tockaos.github.io/buscape/padroes/html/img/ir-a-loja.jpg)

No momento do clique do usuário em Ir a loja em **qualquer lugar do site**, deve-se disparar:


    dataLayer.push({'event':'botao', 'tipo-botao':'ir-a-loja', 'id-oferta', '123456'});



Chave| Tipo de valor| Exemplo
-------- | --- | ---
event		| string | botao
tipo-botao	| string | ir-a-loja
id-oferta 	| string | 123456 



####**Compre Aqui**

![Compre Aqui](http://tockaos.github.io/buscape/padroes/html/img/compre-aqui.jpg)

No momento do clique do usuário em compre aqui em **qualquer lugar do site**, deve-se disparar:



    dataLayer.push({'event':'botao', 'tipo-botao':'compre-aqui', 'id-oferta', '123456'});


Chave| Tipo de valor| Exemplo
-------- | --- | ---
event		| string | botao
tipo-botao	| string | compre-aqui
id-oferta 	| string | 123456 



####**Comprar**

![Comprar](http://tockaos.github.io/buscape/padroes/html/img/comprar.jpg)

No momento do clique do usuário em comprar aqui em **qualquer página de oferta**, deve-se disparar:

    dataLayer.push({'event':'botao', 'tipo-botao':'comprar', 'id-oferta':'123456'});


Chave| Tipo de valor| Exemplo
-------- | --- | ---
event		| string | botao
tipo-botao	| string | comprar
id-oferta 	| string | 123456 



####**Conclusão de implementação do disparo de sucesso de clique dos botões Ir a Loja, Compre-aqui e Comprar**

Com esses disparos implementados, teremos um inicio de funil de pessoas que clicaram em determinado produto, qual a marca que as pessoas mais clicam e param na 2 página por exemplo, ou a categoria que mais passa, ou o lojista que menos é clicado, entre outros.

OBS:

 - Teremos esses dados se o dataLayer de lista for implementado

----------


###**Login**

Adicionar os seguintes disparos quando o usuário se logar:


    dataLayer.push({'event':'sucesso', 'tipo-sucesso':'login', 'tipo-login':'facebook'});



###**Cadastro**

Adicionar os seguintes disparos quando o usuário se cadastrar:


    dataLayer.push({'event':'sucesso', 'tipo-sucesso':'cadastro'});




####**Conclusão implementação de disparo de sucesso de Login e Cadastro**

Com os disparos de sucesso de login e cadastro, poderemos acompanhar o fluxo do usuário e saber mais sobre ele. Devemos passar na camada a **idade, o sexo, o estado**, etc, para fazer listas de remarketing segmentadas:

**Ex:  Produto tal é mais visto por pessoas do sexo masculino de 20-30 anos**