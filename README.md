# EDA no clima de João Pessoa, Campina Grande e Patos

João Pessoa, Campina Grande e Patos são 3 referências para entender o clima na Paraíba. A primeira cidade está no litoral, a segunda próximo ao topo da Serra da Borborema, e a terceira no Sertão. Nesse exercício, você experimentará com o processo de análise exploratória dos dados usando dados dessas 3 cidades. O resultado será um relatório em RMarkdown e publicado online (instruções para publicar mais abaixo).

## As perguntas
Nesse exercício, escolha pelo menos 2 das 4 perguntas abaixo e as responda no seu relatório:

1. Como foi o vento nessas 3 cidades no ano que já analisei (2019)? Como isso complementa a imagem que já temos de como foi o clima em 2019 nessas cidades?
1. Considerando apenas as semanas no período de janeiro e fevereiro (pico do verão), como foi o calor das 3 cidades nos últimos anos?
1. Como a umidade das 3 cidades varia ao longo do ano? 
1. Como você descreveria a temperatura das festas juninas das 3 cidades nos últimos anos?


## Instruções 

Use como ponto de partida o Notebook `reports/exploracao.Rmd`. Coloque no início do documento uma frase dizendo os números das questões que você respondeu, mas não copie as perguntas tal como estão aqui no seu relatório. Use títulos e texto para criar um relatório que possa ser compreendido por alguém que não está no curso e que não pareça um dever de casa de um livro texto :).  Mas me ajude colocando em negrito no relatório os trechos com suas conclusões para cada pergunta.

Importante: sempre que for programar no RStudio, abra o arquivo do projeto (`l1p1.Rproj`) na raiz do repositório. Isso abre o projeto com o diretório de trabalho correto, e facilita sua vida.

### Lembre que

> A estrutura que você seguirá para cada pergunta é: (1) formular uma pergunta, (2) dizer que dados usará para responder a pergunta -- se você filtrará, transformará, etc.os originais, (3) mostrar alguma visão construída com esses dados -- geralmente uma visualização e (4) interpretar com um ou dois parágrafos de texto essa evidência.

Além disso, esse é um exercício sobre descrição de distribuições de valores. Não queremos agora falar em média, mediana, nada disso. Queremos descrever distribuições de valores. Use os conceitos de faixa de valores, concentração, simetria, pontos extremos e cauda para descrever cada distribuiçào que você usar. No fim, a resposta sobre como chove nas 3 cidades por exemplo poderia comentar tanto que a cidade X é aquela que tem semanas com maiores chuvas quanto que essa mesmas cidade tem mais semanas sem chuva. 

Sendo um exercício sobre distribuições, exercite o uso de gráficos de pontos, histogramas e gráficos de densidade. Você pode usar gráficos de linha do tempo (colocando o tempo em um eixo), mas não use apenas ele para nenhuma pergunta.

Atenção para dados faltantes. É importante saber o que temos e o que não temos na hora de tirar conclusões.

Mande dúvidas à vontade nos canais públicos do slack. Assim todos nos ajudamos.

## Submissão

Há dois resultados desse exercício que serão avaliados:

* O código que está no seu repositório no final do prazo
* O link do seu relatório [em html publicado no rpubs](https://rpubs.com/about/getting-started) que deve ser enviado no google classroom.

Repare que o código não precisa ser submetido. Basta deixá-lo atualizado. 

## Os dados

Dados vêm do BDMEP: https://tempo.inmet.gov.br/ . Selecionei lá a estação convencional em João Pessoa, Campina Grande e Patos - PB, e baixei os csvs com dados desde 2010. 

Os dados brutos estão em `data/raw`. O código em `transform` faz ETL e o coloca em `data/`. Você não usará os dados raw, mas é bom saber de onde eles vêm.

No processo de ETL, calculamos as variáveis de interesse por semana. Isso porque há bastante medições vazias nas estações, e queremos deixar o dado mais fácil de ser trabalhado. Mas ainda há várias semanas onde alguma ou todas as medidas são NA.

Cada item nos dados é uma medição das condições de clima em uma semana em uma cidade. As colunas que cada item tem são as seguintes:

```
$ cidade      <chr> A cidade da medição
$ semana      <date> O primeiro dia da semana à qual a medição se refere
$ temp_max    <dbl> A maior temperatura máxima diária registrada nessa semana, em Celsius
$ temp_media  <dbl> A média das temperaturas médias diárias da semana, em Celsius
$ temp_min    <dbl> Menor temperatura registrada nessa semana, em Celsius
$ vento_medio <dbl> Média da velocidade do vento ao longo da semana, em m/s.
$ vento_max   <dbl> Maior velocidade média diária do vento ao longo da semana, em m/s.
$ umidade     <dbl> Médiia da umidade diária na semana, em %
$ chuva       <dbl> Total de precipicação na semana, em mm.
```
