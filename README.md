# Experimentações com Splunk

Então consagrado, nesse repo eu vou desbravar essa ferramenta marvada que é o splunk.

![](/static/pink.gif)

## Introdução

Em poucas palavras o splunk é uma ferramenta bem poderosa, para armazenar logs. É possível desenhar as mais diversas arquiteturas com splunk, desde um único servidor executando todas as funções até clusters inteiros executando funções isoladas.


## Componentes
O splunk pode ser subdividido em componentes sendo alguns deles:

Nome | função
---|---
Indexer| Armazena os dados em índices, isso aumenta a velocidade de busca e análise dos dados.
Search Head| Permite que os usuários usem <span id="a1">[[1]](#f1)</span> SPL para buscar os dados armazenados nas Indexers.
Fowarder| Consomem os dados e encaminham para as indexers, geralmente ficam onde os dados são gerados.
Deployer| Gerencia e distribui os aplicativos para um cluster de Search Heads
License| Gerencia as licenças do cluster

## Cursos Recomendados
Esses cursos são da splunk e são gratuitos (Verificado 31/07/2022 às 16:40)  
[What is Splunk?](https://education.splunk.com/course/what-is-splunk)  
[Intro to Splunk](https://education.splunk.com/course/intro-to-splunk-elearning)  
[Using Fields](https://education.splunk.com/course/using-fields)  
[Introduction to Knowledge Objects](https://education.splunk.com/course/intro-to-knowledge-objects-elearning)  
[Splunk infrastructure overview](https://education.splunk.com/course/splunk-infrastructure-overview)

## Instalação

Quando a instalação é feita de forma descentralizada, as indexer precisam ter um alto desempenho de disco e muito espaço para escrita, por outro lado as Search Heads precisam de mais CPU

## Executar ambiente de teste StandAlone
No modo standAlone uma  única instancia do splunk executa a função de todos os componentes
> **_Aviso:_**  Para subir esse laboratório, você precisa ter instalado o vagrant e o virtualbox.

Primeiro edite o arquivo [**standalone/Vagrantfile**](standalone/Vagrantfile) e informe as URL's de download do pacotes RPM do splunk enterprise e splunk fowarder

![](/static/urls.gif)

Acesse diretório [**standalone**](standalone/) e execute o comando abaixo
```shell
$ cd standalone
$ vagrant up
```
Agora você pode acessar o ambiente através da url http://192.168.165.30:8000 usando as credencias abaixo:  
username: admin  
password: splunk@123  
Você pode alterar a senha no arquivo Vagrantfile alterando a variável **PASS_ADMIN**

![](/static/acesso.gif)

Esse repo também sobe uma aplicação simples que pode ser acessada através da url http://192.168.165.40

![](/static/app.gif)

Você já deve ser capaz de ver os logs da aplicação no splunk.

![](/static/pesquisa.png)
### Notas  
<span id="f1"></span> [**S**earch **P**rocessing **L**anguage](https://docs.splunk.com/Documentation/Splunk/latest/Search/Aboutthesearchlanguage) [$\hookleftarrow$](#a1)