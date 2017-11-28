![enter image description here](http://image.buscape.com/material/buscape.png)



##**Agrupamento Padrão de Canais**

Última atualização: 28/11 - 14:30

###**Índice**

 - [UTMs](#utms) 
	 - [Parâmetros](#parâmetros)
 - [Canais e Regras do Google Analytics](#canais-e-regras-do-google-analytics)
	 - [Direct](#direct)
	 - [Organic Search](#organic-search)
	 - [Social](#social)
	 - [Email](#email)
	 - [Affiliates](#affiliates)
	 - [Referral](#referral)
	 - [Paid Search](#paid-search)
	 - [Other Advertising](#other-advertising)
	 - [Display](#display)
 - [Exemplos para cada canal no Buscapé](#exemplos-para-cada-canal-no-buscapé)

###**UTMs**

UTMs são parâmetros que podem ser adicionados a URL para identificar uma origem, mídia, campanha. Adicionando esses parâmetros a URL, você fornece ao Google Analytics informações sobre a visita.

####**Parâmetros**

 - **utm_source(Origem):** identifica o anunciante, o site, a publicação etc. que envia tráfego para a sua propriedade (por exemplo, google, newsletter4, billboard).
 - **utm_medium(Mídia):** a mídia de publicidade ou marketing (por exemplo: cpc, banner, email newsletter).
 - **utm_campaign(Campanha):** o nome da campanha individual, o slogan, o código promocional etc. de um produto.
 - **utm_term(Termo):** identifica palavras-chave de pesquisa paga. Se você estiver codificando manualmente campanhas de palavras-chave pagas, também deverá usar o parâmetro utm_term para especificar a palavra-chave.
 - **utm_content(Conteúdo):** usado para diferenciar conteúdo semelhante ou links do mesmo anúncio. Por exemplo, se tiver dois links de call-to-action na mesma mensagem de e-mail, você poderá usar "utm_content" e definir valores diferentes para cada um. Assim, você saberá qual versão é a mais eficiente.

**Exemplo**

https://www.buscape.com.br/?utm_source=facebook&utm_medium=social&utm_campaign=intel_verao&utm_term=notebook&utm_content=i7_7_geracao

**utm_source =** *facebook* para identificar o tráfego 
**utm_medium =** *social* para identificar a mídia do tráfego 
**utm_campaign =** *intel_verao* para identificar a campanha especifica de Intel
**utm_term =** *notebook* para diferenciar de outras campanhas de outros produtos
**utm_content=** *i7_7_geracao* para identificar produtos diferentes dentro de um mesmo termo.

**Observações:**

> É importante sempre deixarmos todos os parâmetros em caixa baixa para não haver diferença no GA ja que o Google diferencia maiúsculo de minusculo.


### **Canais e Regras do Google Analytics**

- Direct
- Organic Search
- Social
- Email
- Affiliates
- Referral
- Paid Search
- Other Advertising
- Display

####**Direct**

>  A origem deve ser exatamente "Direto".
>  A Mídia deve ser exatamente "(not set)" ou seja, não tem.
> **Ou** 
> A Mídia deve ser exatamente (none)


#### **Organic Search**

> Mídia deve ser exatamente "Orgânica"

####**Social**

> 	Referência da rede social de origem corresponde exatamente a "Sim"
> **Ou**
> A Mídia bate com a Regex ^(social|social-network|social-media|sm|social network|social media)$

####**Email**

> A Mídia deve ser exatamente "E-mail" ou "email"

####**Affiliates**

>A Mídia deve ser exatamente "Afiliado"

#### **Referral**

> A Mídia deve ser exatamente "Referência"

#### **Paid Search**

> A Mídia deve bate com a Regex ^(cpc|ppc|paidsearch)$
> **E**
> Ad Distribution Network(adWords) NÃO deve ser "Conteúdo"

####**Other Advertising**

> A Mídia bate com a Regex ^(cpv|cpa|cpp|content-text)$

#### **Display**

> A Mídia bate com a Regex ^(display|cpm|banner)$
> **OU**
> Rede de distribuição do anúncio deve ser exatamente "Conteúdo"

---------------------
>Referência:  https://support.google.com/analytics/answer/3297892?hl=pt-BR

###**Exemplos para cada canal no Buscapé**

####**Social**

https://www.buscape.com.br/?utm_source=twitter&utm_medium=social&utm_campaign=celebridades&utm_term=dia_da_toalha&utm_content=venda_de_livro

**Como colocamos Social hoje:**

https://www.buscape.com.br/?utm_source=facebook&utm_medium=categoria

####**Email**

https://www.buscape.com.br/?utm_source=email_marketing&utm_medium=E-mail&utm_campaign=pessoas_que_compraram_iphones&utm_term=iphone&utm_content=iphone7

https://www.buscape.com.br/?utm_source=email_retargeting&utm_medium=E-mail&utm_campaign=pessoas_que_visualizaram_celulares&utm_term=iphone&utm_content=iphone7

**Como colocamos Email hoje:**

https://www.buscape.com.br/?utm_source=transacional&utm_medium=email

####**Affiliates**

https://www.buscape.com.br/?utm_source=criteo&utm_medium=Afiliado&utm_campaign=pessoas_da_criteo&utm_term=criteo&utm_content=criteo

**Como colocamos Afiliados hoje:**

Não temos

#### **Paid Search**

https://www.buscape.com.br/?utm_source=google&utm_medium=cpc&utm_campaign=bp_institucional&utm_term=eletronicos&utm_content=tv

**Como colocamos Paid Search hoje:**

A discutir

####**Other Advertising**

https://www.buscape.com.br/?utm_source=adnet&utm_medium=cpv&utm_campaign=campanha_nova&utm_term=teste&utm_content=teste

**Como colocamos Other ADS hoje:**

A discutir

#### **Display**

https://www.buscape.com.br/?utm_source=lomadee&utm_medium=display&utm_campaign=Conteudo&utm_term=teste&utm_content=teste


**Como colocamos Display hoje:**

https://www.buscape.com.br/?utm_source=google&utm_medium=cpc&utm_campaign=Blast13.11&ad_distribution_network=Content
