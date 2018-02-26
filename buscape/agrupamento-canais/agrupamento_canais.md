
![enter image description here](http://image.buscape.com/material/buscape.png)



# **Agrupamento Padrão de Canais**

Última atualização: 26/02 

## **Índice**

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
	 - [Retargeting](#retargeting)

## **UTMs**

UTMs são parâmetros que podem ser adicionados a URL para identificar uma origem, mídia, campanha. Adicionando esses parâmetros a URL, você fornece ao Google Analytics informações sobre a visita.

### **Parâmetros**

 - **utm_source(Origem):** identifica o anunciante, o site, a publicação etc. que envia tráfego para a sua propriedade 
 >Ex: google, facebook, twitter.
 - **utm_medium(Mídia):** a mídia de publicidade ou marketing 
 > Ex:  cpc, social, email, newsletter.
 - **utm_campaign(Campanha):** o nome da campanha individual, o slogan, o código promocional, etc. 
 > Ex: black_friday, dia_do_consumidor, intel_verao
 > 
 - **utm_content(Conteúdo):** usado para diferenciar conteúdo semelhante ou links do mesmo anúncio. Por exemplo, se tiver dois links de call-to-action na mesma mensagem de e-mail, você poderá usar "utm_content" e definir valores diferentes para cada um. Assim, você saberá qual versão é a mais eficiente.

> Ex: notebook, celular,  

 - **utm_term(Termo):** identifica palavras-chave de pesquisa paga. Se você estiver codificando manualmente campanhas de palavras-chave pagas, também deverá usar o parâmetro utm_term para especificar a palavra-chave.
 > Ex: galaxy_s8, notebook_lenovo_i3, iphone_x

**Exemplo**

https://www.buscape.com.br/?utm_source=facebook&utm_medium=social&utm_campaign=black_friday&utm_term=notebook&utm_content=i7_7_geracao

**utm_source =** *facebook* para identificar o tráfego 
**utm_medium =** *social* para identificar a mídia do tráfego 
**utm_campaign =** *black_friday* para identificar a campanha especifica de black friday
**utm_term =** *notebook* para diferenciar de outras campanhas de outros produtos
**utm_content=** *i7_7_geracao* para identificar produtos diferentes dentro de um mesmo termo.

**Observações:**

> É importante sempre deixarmos todos os parâmetros em caixa baixa para não haver diferença no GA ja que o Google diferencia maiúsculo de minusculo.


## **Canais e Regras do Google Analytics**

- Direct
- Organic Search
- Social
- Email
- Affiliates
- Referral
- Paid Search
- Other Advertising
- Display
- Retargeting

### **Direct**

>  A origem deve ser exatamente "Direto".
>  A Mídia deve ser exatamente "(not set)" ou seja, não tem.
> **Ou** 
> A Mídia deve ser exatamente (none)


###  **Organic Search**

> Mídia deve ser exatamente "Orgânica"

### **Social**

> 	Referência da rede social de origem corresponde exatamente a "Sim"
> **Ou**
> A Mídia bate com a Regex ^(social|social-network|social-media|sm|social network|social media)$

### **Email**

> A Mídia deve ser exatamente "E-mail" ou "email"

### **Affiliates**

>A Mídia deve ser exatamente "Afiliado"

### **Referral**

> A Mídia deve ser exatamente "Referência"

### **Paid Search**

> A Mídia deve bate com a Regex ^(cpc|ppc|paidsearch)$
> **E**
> Ad Distribution Network(adWords) NÃO deve ser "Conteúdo"

### **Other Advertising**

> A Mídia bate com a Regex ^(cpv|cpa|cpp|content-text)$

### **Display**

> A Mídia bate com a Regex ^(display|cpm|banner)$
> **OU**
> Rede de distribuição do anúncio deve ser exatamente "Conteúdo"

### **Retargeting**
> A Mídia contém "retargeting"
> 

---------------------
>Referência:  https://support.google.com/analytics/answer/3297892?hl=pt-BR
