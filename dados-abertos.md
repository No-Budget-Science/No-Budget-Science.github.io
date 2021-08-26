


# Guia de boas práticas em uso de dados na ciência


## Um manual prático para você se atualizar


# Introdução


## O que são dados?

Texto como exemplo de parágrafo que deve ser claro e conciso. Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso.Texto como exemplo de parágrafo que deve ser claro e conciso. (Lucas)


## Porque você deveria se preocupar com seus dados?

Dados são o produto bruto da sua atividade como cientista. Esse motivo isolado deveria ser suficiente para lhe trazer preocupação sobre como você lida com eles, mas listamos alguns outros pontos importantes:



* Motivo 1
* Motivo 2
* Motivo 3
* Motivo 4


## Como usar este material

Este guia foi pensado para abarcar o maior número possível de cientistas brasileiros de diferentes níveis. Nesse sentido, ele foi proposto como um documento atualizável pela comunidade científica. 


# Gestão de dados


## Plano de Gestão de Dados


### O que é 


### Por que fazer


## Armazenamento


### Como armazenar os dados


### Onde armazenar os dados


### Organização de arquivos na prática



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



### Backup de dados

Os dados de pesquisa são a sua matéria-prima e devem ser armazenados levando em conta a sua importância. É imprescindível considerar os riscos de possível perda ou corrupção dos seus dados e, por isso, é necessário o desenvolvimento de um plano de backup: com que frequência pretende realizá-lo e se utilizará mídia física ou baseada em nuvem.

Um sistema de organização muito utilizado é o 3-2-1, em que você deve manter sempre três cópias dos seus dados; utilizar pelo menos dois tipos de armazenamento diferentes, e manter sempre um deles externamente e com segurança.


## Destino????


### Para onde o arquivo vai?


## Princípios FAIR


### O que são os princípios FAIR?


### Como posso me adequar a esses princípios?


# Documentação de dados


## Formatação de planilha

Uma das maiores dificuldades encontradas por pesquisadores é a documentação dos dados através de planilhas. Qual modelo utilizo e como organizo? são dúvidas frequentes durante um estudo. Para a construção da planilha ideal algumas questões devem ser consideradas:


    ·        Que tipo de dados serão inseridos?


    ·        Quais análises serão realizadas?


    ·        Outras pessoas conseguem entender os dados dessa planilha?

De forma geral, uma planilha de dados possui em suas linhas os registros ou observações (pacientes, municípios, animais, estudos (metanálise), etc.) e nas colunas as variáveis (gênero, idade, IDHM, dosagem de citocinas, etc.) (Figura X).

 

Figura X

 

Outro ponto importante nas planilhas é o processo de codificação dos dados, quando aplicado. Para variáveis qualitativas ou categóricas a codificação ocorre de acordo com o objetivo do estudo e das análises que serão realizadas. Geralmente variáveis categóricas binárias (não/sim; feminino/masculino) são convertidas em 0/1, onde 0 indica a não presença da característica pertencente à categoria correspondente. As variáveis categóricas não binárias são convertidas em valores sequenciais, por exemplo, raça/cor (branca, preta, parda, amarela e indígena), tais categorias podem ser codificadas da seguinte maneira: 1, 2, 3, 4 e 5, respectivamente (Figura XX).

Figura XX. 


## Detalhamento de dados


## A documentação dos seus dados de pesquisa é essencial para que outros compreendam suas variáveis de maneira simples e objetiva. Além disso é importante para que você, caso precise retornar aos dados após um longo período de tempo, não se sinta perdido ao encarar a famigerada planilha. Para uma documentação efetiva alguns princípios de boas práticas fazem-se necessários. Abordaremos alguns a seguir.


### Não mescle colunas no excel.

Por mais que mesclar colunas pareça tentador em algumas ocasiões evite essa prática. Caso alguém precise importar o seu banco para outro _software_ (RStudio, Phyton, SPSS, Jamovi, JASP etc.) alguns dados serão perdidos devido a formatação da tabela.


### Cuidado com caracteres especiais.

Este é um problema relativamente comum que atinge as pessoas que utilizam alguma linguagem de programação, o famoso erro de codificação. Alguns caracteres comuns na língua portuguesa (ç, ~, ^, etc.) não conseguem ser codificados por linguagens de programação, resultando em um texto estranho, como por exemplo: "São João" = "S?o Jo?o" ou "SÃ£o JoÃ£o", dentre outras possibilidades. Embora esse problema seja facilmente corrigido utilizando a codificação UTF-8 recomenda-se evitar o uso de tais caracteres.


### Separadores

Utilize algum símbolo, preferencialmente um "."" ou "_", para separar seu texto, principalmente no nome das colunas do seu banco de dados.


### Nome das variáveis

XXX


### Crie um índice para o seu banco de dados

xxxx


## Nomenclatura e padronização de nomes


### Caracteres proibidos

É possível que você já tenha se deparado com uma mensagem deste tipo:



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.jpg). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.jpg "image_tooltip")


Muitos arquivos têm limitação dos caracteres que podem ser usados e os motivos de tais limitações são diversos. Convém-se evitar de antemão utilizar alguns deles no seu dia-a-dia para que não ocorra incompatibilidade entre diferentes aparelhos. Além disso, vale comentar que não é todo aparelho que apresenta suporte para os acentos da língua portuguesa e, por isso, eles também não devem participar do nome de um arquivo.

Listamos aqui caracteres a se evitar:

/    (barra de endereço)

\

|


<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: Definition &darr;&darr; outside of definition list. Missing preceding term(s)? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


:    (dois pontos)

;    (ponto de vírgula)

*



(ponto de 


<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: Definition term(s) &uarr;&uarr; missing definition? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>






“

&lt;

>

ã, á, â, ä (til, agudo, crase, circunflexo e trema)


### Lidando com datas

É usual para brasileiros datar as coisas do dia-a-dia na ordem **_dia-mês-ano_**, porém esta prática é contraproducente para encontrarmos e ordenarmos arquivos em um diretório virtual. Internacionalmente se utiliza a estrutura **_ano-mês-dia_**, na qual…..



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



## Metadados


### O que é?

Apesar de pouco usual no dia a dia de grande parte dos pesquisadores brasileiros, o conceito de “metadados” é, na verdade, muito simples: são os dados que descrevem os seus dados. Mas, se este tipo de informação é tão pouco utilizada na ciência brasileira, qual seria a sua importância?

Os metadados são a forma de comunicação entre quem coletou e analisou primariamente os dados com a pessoa que irá analisar os dados de forma secundária. Este segundo agente pode ser alguém que busque replicar um estudo ou experimento, pode ser alguém que busca estudar a prática científica de um determinado campo de pesquisa a partir da análise de diferentes trabalhos, ou mesmo alguém que está tentando entender melhor a forma que seus resultados estão depositados no repositório de dados.


### Como devo disponibilizar os metadados da minha pesquisa?

Para que essa ampla gama de aplicações secundária de dados em pesquisa se torne viável, os metadados devem ser oferecidos de forma transparente e bem organizada. Dessa forma, tendo em vista a aplicabilidade dos resultados de pesquisas por terceiros, os metadados podem ser entendidos como um conjunto de documentação de dados de forma padronizada que contenha o máximo de informações sobre os seus resultados.

Os metadados contém, geralmente, informações sobre: origem, tempo na qual a coleta de dados foi feita, pessoa responsável pela coleta dos dados, termos de uso dos dados, condições de acesso, etc. Essas informações tendem a variar dependendo da área na qual o pesquisador esteja inserido. Por exemplo: caso seja relevante, pode-se incluir ou não informações acerca da localização geográfica da coleta dos dados.

Tendo em vista essa diversidade de áreas de pesquisa e as suas particularidades, é possível encontrar diferentes padrões para se disponibilizar metadados. O ICPSR (Inter-University Consortium for Political and Social Research), por exemplo, recomenda o uso de XML para criar documentação estruturada de forma compatível com a DDI (Data Documentation Initiative), que fornece certos padrões internacionais de metadados para documentação de pesquisas nas áreas sociais, comportamentais e econômicas. 

Você pode encontrar a melhor forma de oferecer essa informação da sua pesquisa para a sua área de estudo através de sites como o [Research Data Alliance Metadata Standards Directory](http://rd-alliance.github.io/metadata-directory/standards/) e o [Disciplinary Metadata | DCC](https://www.dcc.ac.uk/guidance/standards/metadata). 


## Rastreabilidade de dados


## Licenças de dados
