O objetivo do desafio é classificar desastres a partir de tweets.

O dataset foi obtido através da plataforma kaggle, no link https://www.kaggle.com/c/nlp-getting-started/overview.

No livro Data Science para Negócios são comentados alguns conceitos que podem ser utilizados em problemas focados em NLP. O objetivo era verificar as etapas de preparação dos dados focando em:

1. Tokenização
2. Remover stop words (palavras com frequencia muito alta e de pouco significado de contexto)
3. Lematização (reduzir palavras para não haver diferenciação entre palavras como "causa" e "causas", por exemplo)

Outra etapa importante também seria identificar substantivos, pronomes, verbos, afim de categorizar melhor os tokens obtidos do texto e reduzir o número de features, porém não foi levado em consideração nesse desafio, pois alguns termos podem ser utilizados em situações de desastre.

As bibliotecas utilizadas foram spacy e sklearn, no geral. Apesar de ser possível tokenizar e preprocessar com o feature_extraction.text, utilizei o spacy para entender melhor o processo de tratamento de dados de texto.

Na etapa de stop words, achei necessário retirar as palavras iniciadas com o caracter '@', que identifica marcações de usuários na maioria das vezes, além de pontuações e palavras que não configurassem apenas caracteres do alfabeto.

Como representação do problema, utilizei 3 tipos de vetorização, sem utilizar o preprocessamento, pois já havia tokenizado anteriormente para entender o processo melhor. Os tipo de vetorização foram "bag of words" com 1 e com 2 palavras, além de "tf-idf", que eram tipos sugeridos no livro Data Science para Negócios.

Por se tratar de uma transformação matemática, os algoritmos de modelos mais baseados em funções para classificar os elementos, tiveram melhor performance.

Além disso, por não conhecer muito algumas ferramentas, dei uma olhada na utilização do Keras utilizando um modelo pré-treinado do google de sentenças e utilizando uma CNN desenvolvida em https://arxiv.org/abs/1408.5882 e adaptada em https://github.com/hundredblocks/concrete_NLP_tutorial/blob/master/NLP_notebook.ipynb, na classificação de sentenças para confrontar com os resultados obtidos através de técnicas mais simples que eu utilizei no problema.

Com isso, os dois três melhores modelos foram tfidf_logistic, bow_1x1_svc e tfidf_sgdc, que foram testados na API do kaggle e obtiveram os resultados: 0.77045, 0.79007 e 0.78884, respectivamente. Em contrapartida o resultado do CNN obteve a pontuação de 0.74808. Mesmo sendo uma rede neural mais complexa, a técnica não obteve resultado superior as outras com o tratamento manual usando o spacy, mostrando a importância de uma preparação minuciosa do tratamento dos dados.

