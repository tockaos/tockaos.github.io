![enter image description here](http://image.buscape.com/material/buscape.png)

# **Publicidade**



## **Índice**

- [Objetivo](#objetivo)
- [Processo Técnico](#processo-técnico)
	- [Inicio](#inicio)
	- [Código](#código)
- [Validação](#validação)
- [Outras tags](#outras-tags)



### **Objetivo**

O objetivo dessa documentação é mostrar o processo como o Buscapé insere as publicidades em seu site e como mantê-las funcionando.


### **Processo Técnico**

#### **Inicio**
São duas tags que fazem requisições para a AppNexus efetuar as "bidagens" e assim termos em nosso site as publicidades.

As 2 tags ativas para controlar as publicidades:
- AppNexus - AST
- AppNexus - Prebid
A tag AST tem sempre que ser disparada primeiro. Ela detêm de todos os códigos para cada div do site com publicidade.

#### **Código**

É necessário ter um código para cada área do site conforme exemplo abaixo:

```js
apntag.defineTag({
          invCode: 'home_mobile_half_p1',
          sizes: [[320,50],[300,50],[300,100]],
          targetId: 'home_BF_half_p1',
          disablePsa : true
        });
```

Nome | Formato |o que é?| Exemplo
--|--|--|--|
invCode|string|valor que deve ser igual ao que for programado pelo time de publicidade | home_mobile_half_p1
sizes | inteiro separado por virgula|Tem que ser igual ao tamanho das divs disponibilizadas|[[320,50],[300,50],[300,100]]
targetId|string|Tem que ser igual ao id da Div| home_BF_half_p1
disablePsa| bool| Configuração para se houver alguma publicidade de graça pode ou não ser inserida | true

Alguns invCodes dependem de uma keyword para serem inseridos:

```js
 apntag.defineTag({
          invCode: 'internas_' + 'mob_super_' + departamento + '_' + 'p1',
          sizes: [[320,50],[300, 50],[300,100]],
          targetId: 'OAS_Position2',
          disablePsa : true
        });
``` 

O que passamos em **departamento**  através da variavel do GTM **{{appnexus_departamento}}** é a categoria pai em que a página está situada. Ex:

Departamento |Categoria
-|-
Telefonia | Celular e Smartphone
Eletrodomésticos | Fogão
Alimentos e Bebidas | Vinhos

Outra informação que toda página precisa ter é a **keyword**, que nada mais é do que uma palavra-chave identificando o produto. Inserimos todas as informações do breadcrumb dentro de um array e passamos através da variavel do GTM **{{appnexus_keyword}}**.

### **Validação**

Para validar se a operação está correta, precisamos efetuar alguns passos:

 1. Abrir o  console do Chrome apertando F12 
 2. Ir até a aba de Network e procurar pela palavra **v3**
 3. Ir até a aba de Headers e abrir a chave de Tags
 4. Verificar se o **code** está correto.
 5. Ir até a aba **Preview**
 6. Verificar se há campanhas para essa div ( parâmetro nobid tem que estar false para ter campanha)

![enter image description here](http://tockaos.github.io/buscape/documentacao/publicidade/ast1.jpg)

![enter image description here](http://tockaos.github.io/buscape/documentacao/publicidade/ast2.jpg)

**OBS: Lembrando de validar, o InvCode, Size, targetId.**

### **Outras Tags**

Para termos informações suficientes para publicidade, utilizamos outras 2 tags. **Tail Target e Navegg** .

As duas tags alimentam nossas informações em forma de Cluster. Assim temos também uma inteligência de navegação do usuário.

