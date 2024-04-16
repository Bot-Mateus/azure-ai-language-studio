# azure-ai-language-studio
Demonstração de uma solução para análise de textos construído com Azure Language Studio.

## Passo a passo, arquivos utilizados e resultados 
[Passo a passo](https://github.com/Bot-Mateus/azure-ai-language-studio/tree/main/passo%20a%20passo)

[Inputs](https://github.com/Bot-Mateus/azure-ai-language-studio/tree/main/inputs)

[Outputs](https://github.com/Bot-Mateus/azure-ai-language-studio/tree/main/outputs)


# Índice

1. [Resumo da Ferramenta para Análise de Sentimento](#resumo-da-ferramenta-para-análise-de-sentimento)
2. [Criando o recurso de Linguagem](#criando-o-recurso-de-linguagem)
3. [Testando as Possibilidades](#testando-as-possibilidades)
   1. [Testes de Análise de Sentimentos e Mineração de Opiniões](#testes-de-análise-de-sentimentos-e-mineração-de-opiniões)
      1. [Teste "Avaliação de Estúdio em Curitiba 1"](#teste-avaliação-de-estúdio-em-curitiba-1)
      2. [Teste "Avaliação de Estúdio em Curitiba 2"](#teste-avaliação-de-estúdio-em-curitiba-2)
      3. [Teste "Minha Avaliação Monte Serrat Santos"](#teste-minha-avaliação-monte-serrat-santos)
4. [Considerações e Ideias de Projeto](#considerações-e-ideias-de-projeto)
5. [IMPORTANTE: Limpeza](#importante-limpeza)
6. [Como me encontrar](#como-me-encontrar)
7. 

# Resumo da Ferramenta para Análise de Sentimento

A análise de sentimento e a mineração de opiniões são recursos que ajudam a descobrir as opiniões das pessoas sobre sua marca ou tópico, analisando texto para identificar sentimentos positivos, negativos ou neutros e associá-los a aspectos específicos do texto. A análise de sentimento fornece rótulos de sentimentos e pontuações de confiança para cada frase e documento, enquanto a mineração de opiniões oferece informações mais detalhadas sobre as opiniões relacionadas a palavras específicas no texto.

Para usar esses recursos, você pode seguir um fluxo de trabalho típico, que envolve a criação de um recurso da Linguagem de IA do Azure, o envio de dados para análise por meio da API REST ou bibliotecas de clientes, e o processamento da resposta no seu aplicativo. Existem várias maneiras de utilizar a análise de sentimento, incluindo o uso do Language Studio, API REST ou bibliotecas de clientes, e contêineres do Docker para implantação local.

Ao integrar esses recursos nos seus aplicativos, você pode consultar a documentação de referência e os exemplos disponíveis para diferentes opções de desenvolvimento e linguagens, como C#, Java, JavaScript e Python. Além disso, é importante considerar a responsabilidade na utilização de IA, incluindo o impacto nas pessoas e no ambiente em que é implantada, e garantir práticas responsáveis de uso, conforme descrito na nota de transparência sobre análise de sentimento e em artigos adicionais sobre o tema.

## Criando o recurso de Linguagem

Você pode usar as capacidades de análise de imagem do Azure AI Language com um recurso de serviços de IA do Azure. Se você ainda não o fez, crie um recurso de serviços de IA do Azure em sua assinatura do Azure.

1. Acesse o portal do Azure.
2. Clique em "+ Criar um recurso" e procure por "Análise de Texto".
   
![Criar um recurso](passo%20a%20passo/5.png)

3. Selecione "Criar".
4. Configure o recurso com as configurações necessárias.
5. Após isso basta selecionar "Examinar + criar"

Para acessar basta entrar na página do recurso de Linguagem [AQUI](https://language.cognitive.azure.com/home)
Nos testes nós iremos utilizar o serviço **Analyze sentiment and mine opinions**.

![Analyze sentiment and mine opinions](passo%20a%20passo/7.png) 

# Testando as Possibilidades

Nesta etapa eu irei mostrar os testes realizados com a IA de Linguagem da Azure e farei  alguns comentários.

Fiquem a vontade para replicar os testes utilizando os mesmos textos, os links estão na sessão [Passo a passo, arquivos utilizados e resultados](#passo-a-passo-arquivos-utilizados-e-resultados)

## Testes de Análise de Sentimentos e Mineração de Opiniões

Após ter feito todos esses passos está na hora de ver algo prático. Vamos começar testando a função para Detecção de Faces.

1. Acesse o **Language Studio**.
2. Selecione a guia "**Classify**" e "**Analyze sentiment and mine opinions**". 
3. Faça o upload do seu arquivo de texto e rode a análise **Run**.


### Teste "Avaliação de Estúdio em Curitiba 1":

Nesse teste eu utilizei uma avaliação que encontrei no Booking a respeito de uma das minhas possíveis hospedagens quando viajar para a Cidade. 

![Exemplo](passo%20a%20passo/13.png) 

Na minha opinião de mochileiro é uma hospedagem boa, o fato de ter uma cozinha completa já é muito bom. O ventilador e banheiro foram pontos negativos, mas não seriam uma dificuldade muito grande para mim. 

Vamos ver o que a análise de sentimento nos diz: 

![Exemplo](passo%20a%20passo/14.png) 

Na análise geral esse texto foi considerado positivo, mas notei que o lado negativo está bem baixo. Talvez com a criação de um modelo personalizado que se adeque ao meu cenário, esse detalhe possa ser resolvido.

[LINK JSON AQUI](https://github.com/Bot-Mateus/azure-ai-language-studio/blob/main/outputs/avaliacao-estudio-curitiba-positiva.json)

### Teste "Avaliação de Estúdio em Curitiba 2":

Resolvi utilizar outra avaliação da mesma hospedagem para ter uma base maior para minha tomada de decisão. 

![Exemplo](passo%20a%20passo/11.png) 

Essa avaliação traz mais detalhes e não foi muito boa, e a IA concorda com isso:
 
![Exemplo](passo%20a%20passo/12.png) 

Se estiverem curiosos sobre a **Mineração de Opinião** vejam o ***JSON*** desse teste.

[LINK JSON AQUI](https://github.com/Bot-Mateus/azure-ai-language-studio/blob/main/outputs/avaliacao-estudio-curitiba-negativa.json)


### Teste "Minha Avaliação Monte Serrat Santos":

Dessa vez o teste consiste na **minha** própria avaliação, que deixei no Google Maps sobre o **Cassino Monte Serrat** que fica na cidade de Santos em São Paulo. 

![Exemplo](passo%20a%20passo/17.png) 

Como autor dessa avaliação, concordo com o resultado que a IA alcançou. As vistas valem a pena, porém o Cassino e a Casa de Máquinas, que deveriam ser a atração, não corresponderam a minha expectativa, além de ter sido mal atendido.
 
![Exemplo](passo%20a%20passo/18.png) 

Se estiverem curiosos sobre a **Mineração de Opinião** vejam o ***JSON*** desse teste.

[LINK JSON AQUI](https://github.com/Bot-Mateus/azure-ai-language-studio/blob/main/outputs/avaliacao-monte-serrat-casino-elevador.json)

# Considerações e Ideias de Projeto

Como puderam ver, meus testes foram voltados para avaliações de lugares. Optei por isso porque sou uma pessoa que viaja muito, e no estilo mochileiro, então eu sempre planejo tudo com antecedência e uma parte do planejamento é ver a avaliação dos lugares que irei me hospedar e visitar. 

Pensei em criar uma automação para coletar as avaliações dos pontos turísticos e hospedagens na região e realizar a Análise de Sentimento, após coletar o resultado posso fazer uma média geral de todas as avaliações do lugar e mostrar no software os pontos mais positivos e negativos, por exemplo:

- Hotel Lagueto - 80% positivo
	- Internet rápida - 6 avaliações
	- Quarto limpo - 5 avaliações
	 - Hotel Caro - 5 avaliações

- Hotel Serrat - 70% negativo
	- Internet ruim - 4 avaliações
	 - Quarto Sujo - 4 avaliações
	  - Hotel Barato - 3 avaliações

Com certeza esse projeto irá agilizar o planejamento das minhas viagens, e utilizar o Language Studio da Azure irá agilizar o desenvolvimento da aplicação.

# IMPORTANTE: Limpeza

Se você não pretende fazer mais exercícios, exclua quaisquer recursos que não precise mais para evitar custos desnecessários.

Saiba mais: [Página do Azure AI Vision](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/03-image-analysis.html)

# Como me encontrar

<p align="left">
<!-- <a href="https://elbrusagency.com/"><img src="https://img.shields.io/badge/-elbrusagency.com-3423A6?style=flat&logo=Google-Chrome&logoColor=white"/></a> -->
<a href="https://www.linkedin.com/in/mateus-carvalho-da-silva/"><img src="https://img.shields.io/badge/-Mateus%20Carvalho-0077B5?style=flat&logo=Linkedin&logoColor=white"/></a>
<a href="mailto:carvalho.silva2001@gmail.com"><img src="https://img.shields.io/badge/-carvalho.silva2001@gmail.com-D14836?style=flat&logo=Gmail&logoColor=white"/></a>
<a href="https://www.instagram.com/mateusoaksilva/"><img src="https://img.shields.io/badge/-@mateusoaksilva-E4405F?style=flat&logo=Instagram&logoColor=white"/></a>
</p>
