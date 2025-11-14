# Radar de Franquia Agent

O foco do projeto é a criação de um agente de IA que analisa potencial de mercado para abertura de franquias de fast food, como McDonald`s, Burger King, usando dados públicos para avaliar as melhores localidades e gerar insights para investidores.

## O que o Produto faz

* Avalia cidades com alto potencial para fast food
* Identifica os melhores bairros dentro de uma cidade
* Detecta oportunidades não exploradas
* Classifica riscos e oportunidades

## Dados

Os dados trazidos são públicos e disponíveis nas bases do IBGE, Prefeituras, ABIA, INMETRO.

## Valor para o negócio

Investidores podem tomar decisões com mais confiança e com base em dados.


# Passo a Passo da Criação do Agente

Abaixo resolvi trazer um registro completo do processo de construção do agente no Azure AI Foundry,conforme os pré-requisitos, contendo prints, explicação de cada solução e registro do fluxo de execução. 

## 1. Criação do Agente

No Azure AI Foundry, acessei a área de AI Agents e iniciei a criação de um novo agente. 
Eu escolhi o modelo GPT-5 Mini, por ser leve, rápido, também levei em questão o custo, além de ser adequado para análises comerciais. 

<img width="748" height="717" alt="image" src="https://github.com/user-attachments/assets/5917e93b-c599-4925-a88b-3bf2838a170f" />

## 2. Definição das instruções

Como o agente criado, adicionei as instruções principais que definem o comportamento dele, incluindo o foco do agente que é na análise comercial e a avaliação do portencial de mercado e recomendações baseadas em dados.


<img width="1651" height="922" alt="image" src="https://github.com/user-attachments/assets/48852bd2-a742-4631-9762-d6c9ea729f10" />


## 3. Upload do Arquivo de Conhecimento

Na seção de conhecimento, se eu tivesse escolhido um outro tipo de modelo, carregaria um arquivo que nomeei franchiseradar.json, contendo dados estruturados de cidades, população, densidade, concorrencia e presença de franquias de fast food. 

Como o modelo não comporta, e se trata de um projeto para fins de conhecimento, apenas inclui um print mostrando um pouco de como funciona esse processo e os tipos de arquivos que podem alimentar esse agente. 

<img width="1020" height="888" alt="image" src="https://github.com/user-attachments/assets/2fcffc65-29b2-43ca-8fbc-e706585a178b" />

## 4. Testando o modelo no playground

Com tudo configurado, abri o playground para testar interações com o agente.


