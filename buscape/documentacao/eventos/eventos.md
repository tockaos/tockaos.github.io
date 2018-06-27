![enter image description here](http://image.buscape.com/material/buscape.png)

# **Google Analytics**

## **Eventos**

### **Índice**

- [Objetivo](#objetivo)
- [Processo Técnico](#processo-técnico)
- [De onde vem as informações que estão nos atributos?](#de-onde-vem-as-informações-que-estão-nos-atributos)
- [Implementação e Validação](#implementação-e-validação)
- [Como posso achar o tagueamento no GA?](#como-posso-achar-o-tagueamento-no-ga)



### **Objetivo**

O objetivo dessa documentação é mostrar o processo como o Buscapé envia os eventos par o GA (Google Analytics).


### **Processo Técnico**

Foi criado no GTM (Google Tag Manager) uma tag que é disparada quando um elemento que possui o atributo  **data_ga_event="event"**. 

Essa tag irá enviar ao GA as informações de outros 3 atributos:
**data_ga_category**
**data_ga_action**
**data_ga_label**

Ex: O elemento abaixo é um menu :
 
 ```
<a class="menu_topo" data_ga_event="event" data_ga_category="header" data_ga_action="click:menu_principal" data_ga_label="celulares" href="/celular-e-smartphone"></a>
```

Todo elemento que tiver que ser tagueado, deverá possuir esses atributos listados acima.


### **De onde vem as informações que estão nos atributos?**

As informações vem de um mapa de métricas criado para identificar todos os eventos tagueados dentro do site, assim os desenvolvedores terão acesso a ver o que precisa ser tagueado e qualquer funcionário do buscapé terá acesso para procurar a nomenclatura de determinado evento e procura-lo no GA. 

O Mapa de métricas citado é:

https://docs.google.com/spreadsheets/d/1ruAyiETsi8zgYMtXqMnReEVOkgohtqScmL8j2vTf_s8/edit?usp=sharing

Os usuários a seguir podem editar esse documento:

- Ana Labritz
- Amanda Ueda
- Fernando Lugó (Owner do arquivo)
- Rafael Baialuna

Sempre que um novo elemento for implementado no site do Buscapé, deverá também ser implementado nesse mapa de métricas para mantermos todos elementos tagueados.

**É de suma importância que os P.Os incluam os novos elementos nesse documento e que sigam o padrão de nomenclatura.**

###  **Implementação e Validação**

A partir do momento que for subir um novo elemento no site, o desenvolvedor deverá verificar se o mapa de métricas ja contempla o novo elemento, e se elemento não estiver na lista, o P.O deverá adiciona-lo.

O desenvolvedor, após implementar, deverá informar ao P.O que está tudo ok. O P.O deverá então editar o documento informando que o elemento está implementado e validado conforme imagem baixo:

![enter image description here](http://tockaos.github.io/buscape/documentacao/eventos/validação_evento.jpg)


### Como posso achar o tagueamento no GA?

Basta abrir o mapa de métricas, identificar o tagueamento que você procura, abrir o ga e no menu de **comportamento** dentro do GA:

**Comportamento -> Eventos -> Principais Eventos**

No campo de busca no meio da tela na direita, basta procurar a categoria descrita no mapa de métricas do evento  que procura:

![enter image description here](http://tockaos.github.io/buscape/documentacao/eventos/mapa_de_metricas_categoria.jpg)

![enter image description here](http://tockaos.github.io/buscape/documentacao/eventos/ga_busca.jpg)



