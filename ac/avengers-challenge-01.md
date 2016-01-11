![Alt text](http://lucida-brasil.github.io/public/Images/lucida-logo.png)

# **Avengers Challenge #01  **
** **

##**Descrever como você faz a validação de cada item abaixo:**


----------


 - Config do GA

Link do Adwords
Configuração das Views
Filtros
Metas
Custom Reports
Canais
Content Grouping
Display Features
Busca Interna
WebMaster Tools
Referres Exclusion
Custom Dimensions
Custom Metrics
Filtro de Bots
User ID
eCommerce
Enhanced eCommerce

 - Dados do GA

Eventos
Duplicação de URLs
Fontes de Tráfego
Relatórios demográficos
Domínios que estão enviando dados
Metas
** **

##**Respostas**

----------
**Link AdWords**

Verificando se a configuração da Interface está vinculando as contas de AdWords com o GA:

Administrador -- Propriedade -- Vinculação do Google AdWords

Depois conferindo os dados nos disparos de acordo com o código do adWords

----------
**Configuração das Views**

Essa configuração é feita na criação da View, mas qualquer problema que eu tiver verifico a seguinte tela:

Administrador -- Vista da Propriedade -- Visualizar Configurações

----------
**Filtros**

Verifico Filtros na seguinte tela:

Administrador -- Vista da Propriedade -- Filtros

Testo pelo validador do GA logo após editar ou criar um filtro, e depois em tempo real.

----------
**Metas**

Administrador -- Vista da Propriedade -- Metas

Verifico as metas em tempo real, ou utilizando o **Tag Assistant**

----------
**Custom Reports**

Menu -- Personalização

Relatórios que podem ser editados, então é bom sempre entrar nos relatórios e verificar se os dados estão funcionando.

----

**Canais**

Administrador -- Vista da Propriedade --Configurações do canal -- agrupamento de canais

Consigo gerenciar todos os canais que quero de acordo com algumas regras fornecidas pelo GA. 
Verifico no relatório :

Aquisição -- Todo o Tráfego -- Canais 

E vejo se as regras estão funcionando.

----

**Content Grouping**

Administrador -- Vista da Propriedade -- Agrupamento de Conteúdo.

Crio regras para colocar conteúdos dentro de um grupo, "juntando" assim informações e organizando de um jeito melhor.

----
**Display Features**

É preciso ativar essa configuração para utilizar alguns relatórios tanto no código quanto na interface.

No código é necessário utilizar o código para universal : 

**ga('require', 'displayfeatures');**

E na interface ir no caminho:

Administrador -- Propriedade -- Configuração da Propriedade -- Ativar os Relatórios demográficos e com base em interesses

Basta entrar nos relatórios que disponibilizam tais informações e verificar se estão com dados.

----

**Busca Interna**

Administrador -- Vista da Propriedade -- Configurações da pesquisa no Site

Verificar se as opções estão corretas depois verificar se os dados coincidem com os relatórios, por ex a eliminação de parâmentro de consulta.

----

**WebMaster Tools**

Entro no site do web master tools :  https://www.google.com/webmasters

Verifico se o site do projeto que trabalho está conectado e testo no GA pelo Relatório :
 
 Aquisição -- Otimização de mecanismos de pesquisa -- consultas 

E verificar se a conexão está funcionando.

----

**Referres Exclusion**

Administrador -- Propriedade -- Informações do Acompanhamento -- Lista de exclusão de referências.

Verifico quais os dominios colocados e depois vejo se os dominios em questão aparecem nos relatórios de caminho do GA.

----
**Custom Dimensions**

Administrador -- Propriedade -- Definições Personalizadas -- Dimensões Personalizadas 

Verifico se está criada e com o escopo correto e depois utilizo algum relatório que caiba dentro do escopo proposta afim de visualizar dados na Dimensão criada.

----
**Custom Metrics**

Administrador -- Propriedade -- Definições Personalizadas -- Métricas Personalizadas 

Verifico se está criada e com o escopo correto e testo em um relatório personalizado, pois não conseguimos ver em relatórios próprios do GA.

----
**Filtro de Bots**

Administrador -- Vista da Propriedade --  Filtragem de Bots

Ao marcar você impede os famosos bots indexadores de "sujar" o seu GA.

Para testar, entro no relatório de referências : 

Aquisição -- Todo o Tráfego -- Referências

E verifico se algum site "estranho" com taxa de rejeição de 100%

----

**User ID**

Primeiramente que para ter user ID é necessário criar uma view especifica para ele e ativar a configuração de user ID, após isso é necessário fornecer a numeração de User ID em seu código. 

Para testar, basta acessar os relatórios que utilizam essa informação poe ex:

Relatórios -- Publico Alvo -- Comportamento -- Engajamento do usuário.

----

**eCommerce**

Administrador -- Vista da Propriedade -- Configurações do Comércio Eletrônico


Verificar se está ativada.
Verificar se os relatórios de Comércio Eletrônico estão funcionando.

**Enhanced eCommerce**

No código ter a linha de comando  **ga('require', 'ec');**

E ter as diretrizes de acordo com as documentações do Enhanced Ecommerce do GA.

Para testar, basta visualizar nos disparos se está indo os dados de Enhanced Ecommerce colocados nos códigos e verificar se os relatórios de Enhanced Ecommerce estão funcionando.

----

**Eventos**

Relatórios -- Comportamento -- Eventos -- Eventos principais

Consigo visualizar os eventos e buscar pelos quais eu quiser.

----

**Duplicação de URLs**

Um jeito para não duplicar as URLs é fazer um filtro de domain + path, assim vemos que nem todas as entradas são iguais, pode ser verificado após a inclusão do filtro nos relatórios de Páginas.

----

**Fontes de Tráfego**

Relatórios -- Aquisição -- Todo o Tráfego -- Origem/Mídia

Mostra origens e mídia que vieram ao seu site por ex.

----

**Relatórios demográficos**

Relatórios -- Público Alvo -- Informações Demográficas.

Tem algumas opções de informações.

----

**Domínios que estão enviando dados**

Relatórios -- Comportamento -- Conteúdo do site -- Todas as páginas

----

**Metas**

Relatórios -- Conversões  -- Metas

Consigo visualizar diferentes informações sobre metas.

Quando se cria uma meta também é adicionada a visualização dentro de outros relatórios que não são específicos de metas como em:

Relatórios -- Conteúdo do site -- Páginas de Destino

No final das colunas, você pode escolher uma meta especifica para ver os dados referentes a ela.

