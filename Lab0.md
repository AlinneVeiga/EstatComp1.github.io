---
title: "Estatística Computacional 1"
author: "Professora Alinne Veiga"
date: "2021.1"
output: 
  html_document:
    toc: true
    toc_depth: 3
    toc_float: true
    number_sections: true
    self_contained: yes
    highlight: pygments
---

<img src="logo.png" alt="Ence logo"  style = 'position:absolute; top:0; right:0; padding:10px;' />
  
 

```{css, echo=FALSE}
.title {
  margin-top: 100px;
}
```

# Web-sites

> Acesse o link: <https://www.r-project.org/>.
 
* Você virá o site inicial do R. Ele está em inglês, mas se você estiver acessando pelo Chrome, é provável que você consiga a tradução *google style*.
 
* *Qual o nome da última versão do R? Qual o número da última versão?*

* Clique em **About R** leia o conteúdo.
 
* Vá em **Documentation** e clique em **FAQs**. Olhe algumas delas... 
 
> Volte para a página principal e clique em **CRAN** ou vá em <https://cran.r-project.org/mirrors.html>

* A partir daqui você pode clicar no local mais próximo ... Brazil... Fiocruz?  para poder ter acesso ao site que possui o instalável do R. Verifique que ainda está em inglês.

Para instalar num computador pessoal:   
 
 1. Clique em *Download R for...* escolhendo aquele para o seu sistema operacional.   
 2. Logo em seguida abrirá uma página e você pode clicar me *install R for the first time*.   
 3. E então, clicar em *Download R 4.0.4 for Windows (85 megabytes, 32/64 bit)*.   
 
 
* Clique em *Packages*.

*  Veja que os pacotes estão listados por data de publicação. Clique em algum deles.
  + Em cada um deles você irá encontrar documentação em `pdf` e arquivos com os instaláveis. Clique no PDF logo depois de *Reference manual* para cada um deles e olhe o que contém cada um desses manuais.
 
* **Visitar o manual de referência dos pacotes é sempre boa prática. Você encontrará instruções com grande nível de detalhes nesses manuais.**
 

# RGui

>  Abra o RGui.

* Vá em Todos os programas -> R e clique em "R i..." A janela do RGui abrirá , você virá os créditos e logo em seguida o prompt em vermelho `>`. 

* Antes de digitar qualquer coisa na linha de comando (logo em seguida ao promt) vamos explorar os menus e os botões. 

1. Posicione o mouse em "Edit" e clique em *Gui Preferences*. Nessa janela você pode alterar, por exemplo, o tipo de fonte, o tamanho, a cor de fundo, etc... 
2. Apertando `Ctrl + L`  você limpa o console 
3. Em "Misc" clique em "List Objects" - *Existe algum objeto já criado?*
4. Se você quiser, pode remover os objetos (caso haja algum), clicando em `Misc -> Remove all objects`. 
5. Clique em "Packages": você pode acionar um determinado pacote me `Load Package`, você também pode instalar ou atualizar pacotes

*Agora, explore os botões. Clique neles para ver o que acontece - tenha discernimento!

* Quando terminar de explorar os botões, digite o seguinte na linha de comando e logo aperte o `<ENTER>` 

```{r, eval=FALSE}
options(prompt = "R> ")
```
*O que acontece?*

* Vamos supor que agora você quer mudar novamente o prompt. Ao invés de `R>` , você quer que apareça suas iniciais seguida do `>`. Você não precisa redigitar o comando. Basta utilizar a seta para cima e mover com as setas para o lado e alterar o que você quiser... tente. O meu ficou assim:

```
adcv> 
```

*Qual é mesmo a versão que você tem aí instalada?* Digite:
```{r, eval=FALSE}
sessionInfo()
```

*Quais outras informações que você consegue após esse comando? Quais são os pacotes que estão ligados ("attached")?*

# RStudio

> Acesse o link <https://www.rstudio.com/>

* O download e a instalação do RStudio também é bastante simples e gratuito. Há outros produtos associados ao RStudio e alguns não são livres. 

* Há alguns pacotes associados ao RStudio como o `knitr` que permite a criação de documentos com associação do `TeX` e `Markdown` - esse documento, por exemplo, foi criado no RStudio.

* Um pacote que talvez mereça uma investigação mais detalhada no futuro de vocês é o `ggplot2` que é um pacote que permite a criação de gráficos bem sofisticados. Vamos ver um exemplo logo logo - mas antes disso:

> Abra o RStudio -- Primeiramente, verifique se o RStudio se encontra inslatado em sua máquina. Vá em "Todos os programas -> Aplicativos -> RStudio."

* Como visto em sala de aula, o Rstudio possui quatro janelas:

    * Janela Console: igual ao RGui onde podemos digitar nossos comandos logo após ao prompt.
    
    * Janela com o editor: onde podemos escrever nossos *scripts* - falaremos sobre isso em uma próxima aula. Nessa janela, não basta digitar o comando. Precisamos dar uma ordem para que esse comando seja avaliado - para rodar!
    
    * Janela com o histórico e o ambiente e a ajuda
    
    * Janela com pacotes, arquivos, janela para visualização dos gráficos

* Localize essas quatro janelas, uma pode estar minimizada. Navegue entre essas janelas e perceba a diferença entre elas. Duas das janelas têm abas - passeie entre elas.

* Assim como no RGui, podemos aqui mudar as preferências: modificar cores, e conteúdo de algumas das janelas. Para isso, vá em "Tools -> Global options". Para mudar a aparência, vá em "Appearance" e você pode alterar o Zoom , a fonte e o tamanho e o tema - Experimente!

* Para personalizar o conteúdo e a localização das janelas, vá em "Pane Layout" - escolha entre "source", "console", e nas outras duas pode-se clicar na distribuição das abas entre elas... tente!

* Quando você localizar as suas preferências, **Pare!!**

* Dê uma olhada rápida nos menus e botões do topo -- com tempo iremos aprender mais sobre os menus, mas é importante saber o que há disponível.

Algumas menus importantes:   

1. Session: nesse menu você tem como reiniciar ou terminar o R, salvar ou abrir um *workspace* já salvo numa outra sessão ou limpar, localizar ou estabelecer um novo diretório de trabalho.   
2. Em "File -> New" você poderá perceber os vários tipos de documentos que podem ser criados com o RStudio. Em tempo, veremos algumas dessas possibilidades.    

## Vamos agora utilizar o RStudio para entrar com alguns comandos. 

Entre com os seguintes comandos na linha de comando - uma linha por vez e aperte `<ENTER>` :

```{r, eval=FALSE}
d = c(1,2,3,4,5,6,7,8,9,10)

e = c(1,2,5,10,15,17,16,15,11,7)

plot(d,e)

plot(d,e, type = "l", col = "blue", lwd = 2)
```

*Qual a diferença entre os dois gráficos?*

*Você consegue entender o que cada comando fez? Caso não, não se preocupe. Iremos ver cada um desses comandos ao longo do curso.*

*O que aparece na janela "Console"*

*O que aparece na aba Environment? e na aba History?*

# Help!

* O que será que o comando `plot` faz? Nós sabemos que faz gráficos. Mas como posso mudar as opções desse comando. Vamos ver o que descobrimos acessando o Help!

Digite na linha de comando:
```{r, eval=FALSE}
help(plot)

#ou

?plot

```

E olhe a aba do "Help". *O que você vê?* As funções do R, em geral, tem muitas opções além de seus argumentos - `type` é umas das opções desse comando. O Help é bastante explicativo e no final você encontra exemplos - que são linhas de comandos em sequência. Também podemos acessar os exemplos digitando:

```{r, eval=FALSE}
example(plot)
```
Nesse caso o R já avalia os exemplos gerando gráficos na aba "Plots" - você precisa apertar o `<Enter>` para a reprodução dos exemplos continue.

As setas para cima e para baixo funcionam aqui da mesma forma que no RGui - para localizar o que já foi digitado sem precisar redigitar.

Digite agora
```{r, eval=FALSE}
?c()
```
Esta é a função `combine` - vai ser muito utilizada em entrada de dados, assim como foi utilizado acima. 


**Explore sempre o Help!** Um dos pontos fortes do R é a documentação que existe em cada uma de suas funções. O RStudio facilita a consulta desse material, **faça bom uso disto!**

# Pacotes

Vimos também que o R trabalha com uma coleção de pacotes que contêm as diversas funções da base do R.

Para saber quais os pacotes que estão ligados podemos pedir `sessionInfo()` assim com o RGui. Mas no RStudio possui uma aba chamada "Packages"  que possui os pacotes instalados, e para ligá-los basta clicar no quadradinho ao lado do nomes. 

Localize o pacote `stats4` e clique no seu botão e verifique o que acontece no console. Podíamos também ter digitado:
```{r, eval=FALSE}
library("stats4")
```

Não sabemos o que é esse pacote. Podemos então clicar sobre o seu nome e veja o que acontece na aba do help.

É um dos pacotes mais importantes do base. 

Voltando para a aba dos pacotes, podemos também utilizar o botão "Install" para instalar pacotes que ainda não se encontram listados.

Vamos tentar instalar o pacote `ggplot2`. Vá em "Install" escolha instalar do repositório e digite o nome do pacote ou simplesmente, da linha de comando, digite (precisa de internet):
```{r, eval=FALSE}
install.packages("ggplot2")
```
Esse pacote deve aparecer listado e basta clicar no seu quadradinho para deixá-lo ativo.


# Alguns comandos básicos

Antes de finalizarmos essa sessão, vamos ver alguns comandos básicos.

Vá em sua janela/aba de "Environment", *o que você vê?*

Pra lembrarmos o que é `d` podemos na digitar:
```{r, eval=FALSE}
print(d)

#ou

d
```
Podemos criar uma outra variável (chamarei aqui de variável, mas só por hoje!) utilizado a função de entrada de dados `c()`
```{r, eval=FALSE}
nomes = c("Alinne", "Bernardo", "Brendwon", "Caroline", "Renan", "Fábio", "Danilo", 
          "Isaac", "Thais")
print(nomes)
print
```
Reparem, como são palavras - ou melhor, sequência de caracteres texto - elas precisam estar entre aspas. Posso verificar o tamanho dessa variável e detalhes sobre ela.
```{r, eval=FALSE}
length(nomes)

str(nomes)
```

Para listar tudo que está na janela de "Environment"
```{r, eval=FALSE}
ls()
```
e se quisermos remover algum, basta
```{r, eval=FALSE}
rm(e)
```
Vamos descobrir qual o diretório de trabalho dessa sessão:
```{r, eval=FALSE}
getwd()
```
e podemos alterar:
```{r, eval=FALSE}
setwd("C:/Users/2127180/Desktop")
```

**Note: aqui você pode digitar qualquer endereço, mas o R não aceita a `\` e sim a barra invertida `/`. Se optar por usar a barra, então será preciso dupla barra `\\`**

Para encerrar, vamos olhar esse tal pacote `ggplot2`. Se você ainda não o instalou, instale!

```{r, eval=FALSE}
install.packages("ggplot2")
library(ggplot2)
```

Para vermos os exemplos de gráficos que esse pacote faz, podemos utilizar o comando `example`. Mas precisamos saber quais os comandos básicos para construção de gráficos desse pacote - veja `ggplot2` é o nome do pacote e ele vem com muitas funções e comandos. Há, pelo menos, três comandos básicos que podemos pedir exemplos: `qplot`, `ggplot` e `geom_histogram` .


```{r, eval=FALSE}
example(qplot)
example(ggplot)
example(geom_histogram)
```

> Antes e fechar o R e encerrar sua sessão, explore a aba de "Plots" e o menu com o mesmo nomo - veja como exportar ou salvar os gráficos gerados.

Para encerrar a sessão:
```{r, eval=FALSE}
q()
```

