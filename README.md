# INSTRUÇÕES

Esse repositório consiste de um desafio técnico. Foram fornecidos 5 arquivos csv contendo informações relevantes para a escolha de novas unidades de uma rede de laboratórios dos EUA.
Os dados deveriam ser tratados, uma análise exploratória dos dados deveria ser realizada e a escolha de 3 locais para novas unidades da rede deveria ser justificada.

# DATASET

O dataset é composto pelos arquivos: test_data.csv , EconomicData_ZCTAs.csv , df_geocode.csv , DemographicData_ZCTAs.csv e transactional_data.csv .

test_data contém informações sobre os testes, como custo de aplicação e nome do teste.

df_geocode contém as informações geográficas sobre cada um dos laboratórios da rede.

EconomicData_ZCTAs contém as informações econômicas de cada zipcode (equivalente ao CEP) dos Estados Unidos.

DemographicData_ZCTAs contém as informações demográficas de cada zipcode dos EUA.

Por fim transactional_data contém as informações sobre mais de 2 milhões de transações realizadas pelas diversas unidades do laboratório.
Esse é um arquivo de mais de 100mb e por isso não pode ser compartilhado no github. Para tal vou disponibilizar ele através desse link:

https://drive.google.com/drive/folders/1beZQEtr7E4V_hmOp2bV3_yGfWZlYQRhq?usp=sharing

# ANÁLISE EXPLORATÓRIA DOS DADOS

Primeiramente foram necessários fazer varios tratamentos dos dados como: remover duplicados, colocar as colunas em snake case, colocar as variáveis com o tipo correto, procurar por valores vazios ou nulos, procurar por outliers ou valores absurdos, entre outros...

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/1af8aa48-8715-4fb9-a9af-db91b4704ae4)

Após a realização dos tratamentos foram realizados os primeiros cálculos, como de idade dos consumidores, lucro de cada teste e lucro de cada unidade do laboratório.

O objetivo era de descobrir quais o parametros que eram mais determinantes para o lucro utilizando uma matriz de correlação e mapas de calor.

As colunas acima mencionadas foram acionadas ao dataframe df_geocode que continha as informações dos laboratórios, a esse novo df foi realizado um merge unindo a esse df as informações economicas e demograficas contidas em  EconomicData_ZCTAs e DemographicData_ZCTAs.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/a37cd410-e957-4bff-a4cc-e5042b980129)

Esse mapa de calor mostra uma relação forte entre lucro e população total.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/91b84c11-1215-44b9-9e30-6ab8138362d2)

Essa ideia é reforçada por esse mapa de dispersão de população total x lucro.

Foram realizados também a correlação entre lucro x diversas faixas hetárias. E também a correlação entre lucro x diversas faixas de renda.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/3fc3748b-7d3e-4c8a-87e7-a30f89bd980a)

Desses gráficos é possível ver que a renda ideal varia entre 25mil à 100mil

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/9485de5a-d54d-4c6f-9102-de21b8d38334)

Da correlação relativa à demografia é possivel perceber que:

As faixas etárias que apresentaram melhores resultados para o lucro são as crianças até 14 anos e os adultos de 35 a 60 anos

Com isso tenho agora a segmentação do público alvo:

Pessoas nas faixas hetárias de 0 a 14 anos e de 35 a 60 anos, possuindo renda familiar variando de 25mil à 100mil.

Quanto maior a população melhor

O ideal é que a proporção de mulheres seja levemente maior

Com isso peguei as df que continham as informações demográficas e economicas. Deixei apenas as populações alvo e obtive um novo df contendo apenas os 30 melhores ZIPCODES de acordo com o critério economico e outro df apenas com os 30 melhores ZIPCODES demográficos.

Detalhe que eu tomei o cuidado de remover os locais que já possuem os laboratórios.

Cruzei os dois e obtive os 10 melhores ZIPCODES que atendiam ambos os critérios.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/5c85437b-f244-44bc-bbad-1c45fc4d5657)


![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/dfa7d8f8-edb5-423f-83aa-366a8bf0527d)

Nesse mapa acima de vermelho estão todas as unidades já existentes do laboratório.
Enquanto que de azul estão as 10 candidatas.

A primeira coisa que podemos notar é que as 10 candidatas não estão em cidades que já possuem unidades do laboratório. Em seguida é possível notar que Nova York tem 4 candidatas e Houston possui 2. As outras cidades são Los Angeles, Chicago, Nashville e El Paso.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/d90ca340-a1f2-4a8b-847a-00548954a063)

A cidade de Houston no Texas apresentou 2 pontos muito próximos um do outro, oque provavelmente significa que, escolhendo um endereço correto proximo da divisa desses dois zipcodes é possível que se venda testes de laboratório para ambos as populações.

O zipcode 77449 aprensentou os melhores dados para a demografia e renda familiar alvo dentre os 10 candidatos, e vai ser a 1 das minhas escolhas.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/2b5ca786-9cee-4006-97ba-ef6bb8f323ce)

A primeira vista 11368 (O ponto mais a norte mostrado na imagem acima) apresenta os melhores números para a cidade, mas olhando o mapa da para ver que ele está mais afastado dos outros candidatos além disso a proporção de homens para mulheres não está ideal (uma vez que o ideal é que a população femina seja levemente superior).

Já o ponto 11385 (Retirando o ponto mais ao norte, é o ponto que fica no meio dos pontos restantes) apresenta os 2 melhores números para a cidade de NY e fica relativamente próximo dos pontos 11368 e 11208, oque pode significar uma capacidade de atrir os públicos desses bairros vizinhos que também apresentam bons números.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/a81f1dd0-134f-40d8-9f8c-5d11aa43c1e4)

Por fim analisando os ultimos 4 zipcodes:
60629 (Chicago) apresenta a segunda maior população dentre as 4, tendo também o maior número de pessoas dentro da faixa etária desejada(representado por populacao_alvo_x).
Porém, aprensentou o pior número entre os 4 de familias dentro da faixa de renda alvo (representado por populacao_alvo_y).

90250 (Los Angeles) apresenta números ruins tanto de população, renda familiar e de população dentro da faixa etária.

Por fim, sobraram 79936 (El Paso) e 37013 (Nashville) que apresentaram números sólidos tanto de renda familiar e faixa etária adequadas.

Minha escolha final será El Paso por apresentar maior população total, o fator que apresentou maior correlação com a varivél lucro, além disso ficou em 2 dentre os 4 tanto nos critérios econômicos como demográficos.

![image](https://github.com/RafaelGuisso/AED_elogroup/assets/108840079/e93f1a25-a8be-431b-8a92-f4285b7f57d4)


# CONCLUSÃO

No final foram escolhidos Zipcodes com bom número de população que atendem tanto o critério econômico quanto o demográfico. Além disso são em estados que ainda não possuiam laboratórios da rede e que apresentaram multiplas opções de candidatos para serem escolhidos, evidenciando como essas eram opções fortes. 

A utilização de um gráfico de correlação foi determinante para descobrir quais as principais variaveis que deveriam ser observadas para maximizar o lucro. Além disso, utilizar a visualização do mapa permitiu visualizar a proximidade dos pontos e evitar que dois pontos em uma mesma cidade fossem escolhidos. Mas ao mesmo tempo permitiu também perceber que mesmo estando no mesmo estado, El Paso e Houston estão bem distantes uma da outra, fazendo com que uma unidade não competisse com a outra.





