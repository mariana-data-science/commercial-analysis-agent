# Radar de Franquia Agent

O foco do projeto é a criação de um agente de IA que analisa potencial de mercado para abertura de franquias de fast food, como McDonald's, Burger King, usando dados públicos para avaliar as melhores localidades e gerar insights para investidores.

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

<img width="1020" height="888" alt="Captura de tela da págica do Azure AI Factory, mais especificamente na página de arquivo de conhecimento, onde podemos subir arquivos. Para ilustrar subi um arquivo JSON" src="https://github.com/user-attachments/assets/2fcffc65-29b2-43ca-8fbc-e706585a178b" />

## 4. Testando o modelo no playground

Com tudo configurado, abri o playground para testar interações com o agente.



* Modelagem do Agente

<img width="691" height="567" alt="imagem de uma modelagem criada no site draw.io. O intuito dessa modelagem é mostrar o processo de treinamento do agente de IA" src="https://github.com/user-attachments/assets/dd69b67d-d6b8-44f4-a781-d57e2904c948" />


Criei um pipeline completo para desenvolver o agente, incluindo coleta, pré-processamento e treinamento de modelos usando dados reais e também dados fictícios. Depois do deploy, o agente pode ser alimentado pelo usuário final com diferentes fontes, como APIs externas, arquivos CSV, queries e bases próprias, permitindo gerar respostas específicas e adaptadas ao contexto de cada negócio.
A arquitetura integra o modelo treinado, a base de conhecimento e as fontes externas, garantindo que o agente processe, refine e entregue insights precisos, mantendo um ciclo contínuo de melhoria.


### Perguntas para fazer ao Agente e testar o modelo

Nessa última etapa, foquei em treinar o agente com dados ficticios e reais, e em seguida realizei as seguintes perguntas:

1. Olá! vou anexar um json com dados e gostaria que você realizasse algumas predições, ok?  
 
A primeira é, qual a melhor franquia para investir no Estado de Pernambuco e em qual cidade?

<img width="845" height="644" alt="image" src="https://github.com/user-attachments/assets/f83e890d-9f7f-4ee1-ae6c-00b1e9979ad9" />

Em resposta, o agente me devolveu o seguinte texto:

Obrigado — recebi os dados (cidades.json) e fiz uma análise inicial focada no Estado de Pernambuco. Resumo das conclusões e justificativas numéricas abaixo.

Resumo da recomendação
Melhor cidade para abrir uma unidade com marca já consolidada (baixo risco de adoção): Recife — maior mercado absoluto e maior renda média local. 
Dados: população ~1.650.000, renda mediana R$2.400, 15 unidades fast‑food já presentes; brand dominante: McDonalds; foot_traffic_index 920.

Melhor cidade para entrar com formato de menor investimento (menor concorrência relativa / bom tráfego por concorrente): Jaboatão dos Guararapes — bom equilíbrio entre população, tráfego e concorrência moderada. 
Dados: população ~720.000, renda mediana R$2.000, 7 unidades fast‑food, foot_traffic_index 1050.

Alternativa de oportunidade (nichos / formato delivery ou loja compacta): Olinda — menor número absoluto de concorrentes (3) e maior foot_traffic_index por concorrente, porém mercado menor e renda mediana R$2.100.
Cálculos-chave que sustentam a recomendação
População por unidade de fast‑food (indicador de saturação):
Recife ≈ 1.650.000 / 15 ≈ 110.000 habitantes por concorrente.
Jaboatão ≈ 720.000 / 7 ≈ 103.000 habitantes por concorrente.
Olinda ≈ 400.000 / 3 ≈ 133.000 habitantes por concorrente.
Foot‑traffic index por concorrente (proxy de demanda disponível por unidade):
Recife: 920 / 15 ≈ 61
Jaboatão: 1050 / 7 ≈ 150
Olinda: 780 / 3 ≈ 260
(valores mostram que, apesar de menor mercado absoluto, Olinda e Jaboatão têm maior tráfego "por concorrente", indicando espaço para captura de demanda local).
Interpretação prática
Recife: melhor para redes que precisam de escala, reconhecimento de marca e atraem consumo com ticket médio maior (renda mediana superior). Risco: competição maior (15 unidades).
Jaboatão: equilíbrio entre tráfego elevado e competição moderada — boa opção para marcas com foco em delivery + loja compacta ou para expansão de franquias regionais que buscam rápido payback.
Olinda: oportunidade para formatos de menor custo/alta eficiência (delivery/drive-thru/loja de bairro) ou conceitos diferenciados (food‑service premium casual) que capturem tráfego local com pouca concorrência direta.

Recomendações acionáveis
Se seu objetivo é reduzir risco e entrar com marca conhecida: buscar franquia da categoria já dominante (ex.: McDonalds, que aparece como marca mais forte nos municípios analisados) e priorizar Recife por escala.
Se procura retorno rápido com investimento menor: priorizar Jaboatão para loja compacta + forte operação de delivery; avaliar Olinda para teste piloto em formato enxuto.
Antes de decidir: obter dados adicionais (aluguel por m² por bairro, custos de implantação da franquia selecionada, mix de canais de venda — balcão vs delivery — e dados demográficos mais granulares por bairro). Posso montar uma simulação financeira (payback, margem, ticket médio estimado) se você subir esses dados.

Métricas que recomendo acompanhar e o porquê
População total e densidade: tamanho do mercado local.
Renda mediana: poder de compra / ticket potencial.
Número de fast‑food existentes e população por concorrente: saturação de mercado.
Foot‑traffic index e foot_traffic per competitor: demanda disponível e competição direta.
Consumption_out_of_home_pct: propensão a comer fora (impacta frequência de compra).
Custo de aluguel por m² e taxa de entrega média: influência direta na rentabilidade.

Quer que eu:
Gere um ranking detalhado de todas as cidades de PE presentes no arquivo,
Modele payback estimado para 2 opções de franquia (formato tradicional vs delivery/loja compacta) usando parâmetros que você indicar,
Ou filtre por cidades com renda mediana ≥ X ou tráfego ≥ Y?

Diga qual próximo passo prefere e, se tiver, envie o CSV/JSON com custos de franquia (taxa inicial, royalty), aluguel médio e ticket médio estimado para eu rodar as projeções.


<img width="843" height="636" alt="image" src="https://github.com/user-attachments/assets/6a17e05e-c4e4-4f7c-b4b0-4cdde1ee99c8" />


Minha próxima pergunta foi:

Então, das principais cidades do estado de Pernambuco, a que menos possui franquias de fast-food do McDonalds, por exemplo, é Olinda? então seria interessante investir?


<img width="849" height="640" alt="image" src="https://github.com/user-attachments/assets/4b5f84f6-81d2-468f-a686-0a999c750f62" />


E como resposta, o Agente me trouxe mais detalhes baseado em meu arquivo:

sim, entre as principais cidades de Pernambuco presentes no seu arquivo, Olinda tem o menor número total de unidades de fast‑food (3), enquanto Recife tem 15 e Jaboatão dos Guararapes 7 .

Pontos numéricos que importam (dados do arquivo)
Olinda: população 400.000, number_of_fastfood = 3, foot_traffic_index = 780, renda mediana R$2.100 .
Jaboatão dos Guararapes: população 720.000, number_of_fastfood = 7, foot_traffic_index = 1050, renda mediana R$2.000 .
Recife: população 1.650.000, number_of_fastfood = 15, foot_traffic_index = 920, renda mediana R$2.400 .

Métricas úteis e cálculos rápidos (proxies de oportunidade)
População por concorrente (menor → mais saturado):
Olinda ≈ 400.000 / 3 ≈ 133.333 hab/concorrente.
Jaboatão ≈ 720.000 / 7 ≈ 102.857 hab/concorrente.
Recife ≈ 1.650.000 / 15 ≈ 110.000 hab/concorrente.
Foot‑traffic index por concorrente (proxy de tráfego disponível por unidade — maior = mais demanda por loja):
Olinda: 780 / 3 = 260
Jaboatão: 1050 / 7 ≈ 150
Recife: 920 / 15 ≈ 61
Esses números indicam que, por unidade existente, Olinda apresenta muito mais “tráfego” disponível no agregado do que Recife ou Jaboatão (o que sinaliza espaço de captura local).
Limitação importante sobre “McDonalds”
O seu arquivo lista o número total de fast‑food por cidade e qual é a marca mais forte, mas não detalha quantas unidades cada marca (ex.: McDonalds) possui por cidade. Ou seja: podemos afirmar que Olinda tem menos unidades totais e que McDonalds aparece como marca forte na cidade, mas não temos a contagem específica de unidades McDonalds no arquivo .

Interpretação prática / recomendação
Por perfil (menor saturação por habitante e maior foot‑traffic por concorrente), Olinda é uma cidade atraente para testar uma nova unidade — especialmente em formatos enxutos (dark kitchen / delivery-first), lojas de bairro eficientes ou um piloto de baixo investimento. Os riscos são: mercado absoluto menor que Recife e renda mediana ligeiramente inferior, o que pode limitar ticket médio total .
Se o objetivo for escala e menor risco de adesão de marca (maior base de clientes de alto poder de compra), Recife continua sendo prioridade; se for payback rápido com menor número de concorrentes diretos por tráfego, Jaboatão e Olinda são opções melhores .

Próximos passos que eu recomendo (acionáveis)
Obter contagem por marca (número de unidades McDonalds, Burger King, etc.) por cidade/neighborhood — isso elimina incerteza sobre presença da marca.
Levantar aluguel/m² e custos operacionais por bairro em Olinda; modelar payback para formato loja completa vs. loja compacta/dark kitchen.
Validar mix canais (delivery x balcão) e penetração de apps de entrega na cidade.
Quer que eu:
monte um ranking completo das cidades de Pernambuco do seu arquivo por potencial (usando as métricas acima),
ou rode uma simulação de receita/payback para um piloto em Olinda se você informar custos de franquia, aluguel e ticket médio esperado?


<img width="843" height="545" alt="image" src="https://github.com/user-attachments/assets/0d8aa9e7-08f9-481a-b137-5adc00c8d261" />


E minha última pergunta, para evitar tornar o README ainda mais longo, foi:

Roda uma simulação de receita para um piloto em Olinda? consegue me trazer em formato de gráficos também? 

<img width="846" height="640" alt="image" src="https://github.com/user-attachments/assets/e3d2de07-0ab9-477c-86b0-ccee2cdd4a34" />


E por fim, após a troca de mensagens sobre o que exatamente busco nessa análise, o agente me retornou o que solicitei e a partir do playground peguei o código e gerei os gráficos no google colab:

<img width="1189" height="990" alt="image" src="https://github.com/user-attachments/assets/4d792ca4-cccc-437e-adca-19b0ea3ff241" />


O código

<img width="1117" height="649" alt="image" src="https://github.com/user-attachments/assets/abe12ec9-4784-41a4-a2ea-887a9c89e679" />







