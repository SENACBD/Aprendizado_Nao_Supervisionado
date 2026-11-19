Projeto Executivo — Segmentação de Clientes do E-commerce Olist
PROJETO EXECUTIVO
Segmentação de Clientes do E-commerce Olist utilizando Aprendizado de Máquina Não Supervisionado
Área: Ciência de Dados e Aprendizado de Máquina
Base de dados: Brazilian E-Commerce Public Dataset by Olist
Período de análise: 01/01/2017 a 31/12/2017
Algoritmos experimentais: K-Means e DBSCAN
Linguagem: Python 3.13
Ambiente de desenvolvimento: Visual Studio Code
Memória RAM disponível: 8 GB
________________________________________
1. Apresentação
Este projeto tem como finalidade desenvolver uma solução de análise não supervisionada para identificar e caracterizar segmentos de clientes de uma plataforma de comércio eletrônico.
Será utilizado o Brazilian E-Commerce Public Dataset, disponibilizado pela Olist, que reúne informações sobre clientes, pedidos, produtos, pagamentos e avaliações.
A análise será delimitada aos pedidos realizados entre 1º de janeiro e 31 de dezembro de 2017. Essa delimitação permitirá trabalhar com um período anual completo, reduzir o volume de dados processados e concentrar a análise em comportamentos de consumo observados dentro de uma janela temporal definida.
Serão implementados dois algoritmos de agrupamento: K-Means e DBSCAN. Os algoritmos Gaussian Mixture Models (GMM) e Agrupamento Hierárquico serão abordados na fundamentação teórica, mas não farão parte da execução experimental.

3. Problema de pesquisa
Como técnicas de aprendizado de máquina não supervisionado podem identificar grupos de consumidores com comportamentos de compra semelhantes em uma plataforma de comércio eletrônico?
A investigação buscará identificar padrões relacionados à frequência de compras, valores gastos, características das transações e avaliações realizadas pelos consumidores.
4. Justificativa
A segmentação de clientes é uma atividade relevante para organizações que desejam compreender melhor seus consumidores e desenvolver estratégias comerciais orientadas por dados.
A utilização de algoritmos de aprendizado não supervisionado permite identificar agrupamentos sem a necessidade de categorias previamente definidas.
A escolha do período de 2017 e dos algoritmos K-Means e DBSCAN considera tanto os objetivos acadêmicos quanto os recursos computacionais disponíveis, especialmente a memória RAM de 8 GB.
A concentração em dois algoritmos permitirá aprofundar a análise comparativa e a interpretação dos segmentos identificados.
4. Objetivos
4.1 Objetivo geral
Desenvolver uma solução de segmentação de clientes utilizando técnicas de aprendizado de máquina não supervisionado, com base nos dados de comércio eletrônico da Olist referentes ao ano de 2017.

4.2 Objetivos específicos
•	Integrar as informações de clientes, pedidos, itens, pagamentos e avaliações.
•	Delimitar a base aos pedidos realizados durante o ano de 2017.
•	Construir indicadores que representem o comportamento de compra dos consumidores.
•	Realizar análise exploratória e tratamento dos dados.
•	Preparar e padronizar as variáveis utilizadas nos modelos.
•	Implementar os algoritmos K-Means e DBSCAN.
•	Avaliar a qualidade dos agrupamentos por meio de métricas estatísticas.
•	Identificar e interpretar os perfis de consumo encontrados.
•	Comparar os resultados dos dois algoritmos.
•	Produzir documentação técnica e conclusões sobre a aplicação dos modelos.

5. Delimitação e escopo
O projeto utilizará exclusivamente os pedidos cuja data de realização esteja compreendida entre 01/01/2017 e 31/12/2017.
A data de referência para o cálculo da recência será 01/01/2018.
Serão considerados pedidos com situação de entrega concluída, conforme o campo de status disponível na base.
A unidade de análise será o consumidor identificado pelo campo customer_unique_id, garantindo que diferentes pedidos realizados pelo mesmo consumidor sejam consolidados em um único registro.

5.1 Dentro do escopo
•	Integração das cinco fontes de dados selecionadas.
•	Filtragem temporal dos pedidos de 2017.
•	Consolidação das informações por consumidor.
•	Engenharia de atributos.
•	Análise exploratória.
•	Tratamento e preparação dos dados.
•	Implementação de K-Means e DBSCAN.
•	Avaliação estatística e interpretação dos agrupamentos.
•	Comparação dos resultados e elaboração do relatório final.

5.2 Fora do escopo experimental
Os algoritmos GMM e Agrupamento Hierárquico serão apresentados conceitualmente, incluindo seus fundamentos, características, vantagens e limitações.
Não serão treinados nem utilizados na comparação experimental.
Também não fazem parte do escopo a implantação de um sistema em produção, a integração com plataformas comerciais em tempo real ou a construção de um mecanismo de recomendação de produtos.

6. Fontes de dados
Serão utilizadas cinco fontes principais:
Arquivo	Informações
olist_customers_dataset.csv	Identificação e localização dos clientes
olist_orders_dataset.csv	Pedidos, datas e situação das entregas
olist_order_items_dataset.csv	Itens, preços e fretes
olist_order_payments_dataset.csv	Valores e condições de pagamento
olist_order_reviews_dataset.csv	Avaliações dos consumidores
As tabelas serão integradas por meio dos identificadores de pedidos e clientes.
Antes das junções, os dados de itens, pagamentos e avaliações deverão ser agregados por pedido, evitando multiplicação indevida dos registros durante os relacionamentos.

7. Engenharia de atributos
Será construída uma base analítica com um registro por consumidor.
As principais variáveis previstas são:
Variável	Descrição
recencia	Dias entre 01/01/2018 e a última compra realizada em 2017
frequencia	Quantidade de pedidos entregues no período
valor_total	Valor total gasto pelo consumidor
ticket_medio	Valor médio por pedido
total_itens	Quantidade total de itens adquiridos
valor_produtos_total	Soma dos valores dos produtos
frete_medio	Valor médio do frete por pedido
avaliacao_media	Média das avaliações realizadas
possui_avaliacao	Indicador de existência de avaliação
parcelas_media	Média de parcelas por pedido
As variáveis monetárias serão calculadas de maneira consistente, evitando duplicidade de valores decorrente das junções entre tabelas.
A avaliação ausente não será interpretada como nota zero. O tratamento dos valores ausentes será realizado na etapa de preparação, com imputação apropriada e preservação do indicador de existência de avaliação

8. Metodologia
O desenvolvimento seguirá uma abordagem baseada nas etapas do processo CRISP-DM:

8.1 Compreensão do negócio
Definição do problema de segmentação, dos objetivos analíticos e dos indicadores necessários para caracterizar os consumidores.

8.2 Compreensão dos dados
Identificação das fontes, análise de formatos, distribuição das variáveis, valores ausentes, duplicidades e consistência dos registros.

8.3 Preparação dos dados
•	Filtragem dos pedidos realizados em 2017.
•	Seleção dos pedidos entregues.
•	Integração das fontes.
•	Agregação dos dados por pedido e por consumidor.
•	Tratamento de inconsistências.
•	Construção das variáveis analíticas.
•	Imputação dos valores ausentes.
•	Padronização das variáveis numéricas.

8.4 Modelagem
Implementação dos algoritmos K-Means e DBSCAN, com experimentação de parâmetros e análise dos resultados.

8.5 Avaliação
Comparação da qualidade dos agrupamentos, análise dos segmentos e verificação da coerência dos resultados com o comportamento de consumo.
8.6 Implantação e apresentação
Organização dos modelos, relatórios, gráficos, documentação e resultados finais para apresentação acadêmica.

9. Algoritmos selecionados
    
9.1 K-Means
O K-Means será utilizado como algoritmo principal de segmentação.
Seu funcionamento consiste em dividir os consumidores em K grupos, buscando minimizar a distância entre os registros e os centroides dos respectivos agrupamentos.
Serão avaliados diferentes valores de K, inicialmente considerando uma faixa de 2 a 8 grupos.
A escolha final deverá considerar as métricas de avaliação, a estabilidade e a interpretabilidade dos segmentos

9.2 DBSCAN
O DBSCAN será utilizado como algoritmo complementar.
Seu funcionamento é baseado na densidade dos registros, identificando regiões com concentração suficiente de observações.
Os principais parâmetros serão:
•	eps: distância máxima para considerar vizinhos.
•	min_samples: quantidade mínima de observações para formar uma região densa.
O algoritmo também permitirá identificar observações classificadas como ruído, que não pertencem a nenhum agrupamento.
A seleção dos parâmetros será realizada por experimentação e análise da distribuição das distâncias entre vizinhos.

9.3 Algoritmos abordados teoricamente
Gaussian Mixture Models (GMM): será apresentado como método probabilístico de agrupamento, baseado em distribuições gaussianas.
Agrupamento Hierárquico: será apresentado como método que constrói uma estrutura hierárquica de agrupamentos, podendo ser representado por dendrogramas.
Esses dois algoritmos não serão executados experimentalmente.

10. Avaliação dos modelos
A avaliação utilizará métricas quantitativas e análise qualitativa dos agrupamentos.
Métrica	Interpretação
Silhouette Score	Quanto maior, melhor a separação e coesão dos grupos
Davies-Bouldin Index	Quanto menor, melhor a separação dos agrupamentos
Calinski-Harabasz Index	Quanto maior, melhor a relação entre dispersão entre grupos e dentro dos grupos
Taxa de ruído	Percentual de observações classificadas como ruído pelo DBSCAN
Tamanho dos clusters	Distribuição dos consumidores entre os agrupamentos
As métricas serão interpretadas em conjunto, pois nenhuma delas, isoladamente, garante a qualidade comercial da segmentação.
Para o DBSCAN, a taxa de ruído será analisada separadamente. As métricas de qualidade dos agrupamentos deverão explicitar que os registros classificados como ruído não participam do cálculo de separação entre clusters.
A comparação também considerará a quantidade de grupos encontrados e a possibilidade de interpretar seus perfis.

11. Recursos computacionais
O desenvolvimento será realizado em uma máquina com 8 GB de memória RAM, utilizando Python 3.13 e Visual Studio Code.
Para manter o processamento compatível com os recursos disponíveis, serão adotadas as seguintes medidas:
•	Processamento sequencial dos algoritmos.
•	Liberação de objetos intermediários após o uso.
•	Evitar cópias desnecessárias de grandes DataFrames.
•	Utilização de amostras para experimentos preliminares.
•	Cálculo da Silhouette Score por amostragem quando necessário.
•	Monitoramento do consumo de memória.
•	Ajuste dos parâmetros do DBSCAN conforme o comportamento da base.
O K-Means será executado sobre a base preparada completa, desde que a memória disponível permita.
O DBSCAN será inicialmente avaliado em amostras e, posteriormente, testado na base completa somente se o consumo de memória for compatível.

12. Arquitetura do projeto
A solução será organizada de maneira modular, separando as responsabilidades de cada etapa.
Projeto_Olist/
│
├── dados/
│   ├── original/
│   ├── processados/
│   └── preparados/
│
├── src/
│   ├── __init__.py
│   ├── config.py
│   ├── integrar_dados.py
│   ├── tratar_dados.py
│   ├── analise_exploratoria.py
│   ├── preparar_dados.py
│   ├── treinar_modelos.py
│   ├── avaliar_modelos.py
│   └── segmentar_clientes.py
│
├── modelos/
├── graficos/
├── relatorios/
├── README.md
└── requirements.txt
Os módulos de treinamento e avaliação serão ajustados para executar somente K-Means e DBSCAN.

13. Resultados esperados
Espera-se obter:
•	Uma base analítica consolidada e validada de consumidores com pedidos entregues em 2017.
•	Indicadores capazes de representar o comportamento de consumo.
•	Um modelo K-Means com segmentos interpretáveis.
•	Um modelo DBSCAN com agrupamentos baseados em densidade e identificação de ruídos.
•	Uma comparação fundamentada entre os resultados dos algoritmos.
•	Perfis de consumidores que possam orientar estratégias comerciais.
•	Documentação técnica e relatório acadêmico do desenvolvimento.
Os segmentos encontrados serão interpretados a partir das características observadas, sem presumir antecipadamente que determinados grupos de consumidores necessariamente existirão.

14. Cronograma de execução
Etapa	Atividade
1	Revisão do projeto e adequação do escopo
2	Validação das fontes e integração dos dados
3	Filtragem temporal e construção da base de 2017
4	Tratamento e análise exploratória
5	Engenharia de atributos e preparação
6	Implementação e experimentação do K-Means
7	Implementação e experimentação do DBSCAN
8	Avaliação e comparação dos resultados
9	Interpretação dos segmentos
10	Documentação e apresentação final

15. Riscos e medidas de controle
Risco	Medida de controle
Corrupção ou inconsistência dos arquivos CSV	Validação de estrutura, identificadores, dimensões e integridade após cada gravação
Alto consumo de memória	Processamento sequencial e experimentos com amostras
Sensibilidade do DBSCAN aos parâmetros	Experimentação sistemática de eps e min_samples
Desbalanceamento dos grupos	Análise do tamanho e da distribuição dos clusters
Valores ausentes	Imputação adequada e manutenção de indicadores auxiliares
Perda de informação na integração	Agregação prévia das tabelas de itens, pagamentos e avaliações
Dificuldade de interpretação	Perfilamento dos grupos com indicadores de negócio

16. Considerações finais
O projeto propõe uma aplicação prática de aprendizado de máquina não supervisionado para segmentação de consumidores de comércio eletrônico.
A delimitação temporal a 2017 e a escolha de K-Means e DBSCAN representam uma adequação do escopo aos recursos computacionais disponíveis, sem abandonar os objetivos científicos e acadêmicos da investigação.
A utilização de dois algoritmos com abordagens distintas permitirá comparar agrupamentos baseados em centroides com agrupamentos baseados em densidade.
O resultado esperado não é apenas a execução dos algoritmos, mas a produção de conhecimento sobre os diferentes comportamentos de consumo identificados na base Olist, considerando as limitações e características do conjunto de dados utilizado.

17. Uma decisão metodológica que precisamos preservar
Há um detalhe importante para a implementação: o filtro de 2017 deve utilizar order_purchase_timestamp, e não a data de entrega.
Assim, selecionaremos os pedidos realizados em 2017 e, depois, verificaremos quais foram efetivamente entregues. Isso evita incluir pedidos de outros anos apenas porque foram entregues durante 2017.
Também precisamos verificar a cobertura real do período e a quantidade de consumidores resultante antes de fixar o tamanho final da base.
