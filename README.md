# Credit-score
# Projeto 01 - Concessão de Cartões de Crédito

Bem-vindo ao projeto de concessão de cartões de crédito! Este projeto foi desenvolvido com o objetivo de criar um modelo preditivo capaz de identificar o risco de inadimplência de proponentes de cartões de crédito. Utilizamos a metodologia CRISP-DM para guiar o desenvolvimento deste projeto.

## Sumário

- [Descrição do Projeto](#descrição-do-projeto)
- [Objetivos](#objetivos)
- [Metodologia CRISP-DM](#metodologia-crisp-dm)
  - [Entendimento do Negócio](#entendimento-do-negócio)
  - [Entendimento dos Dados](#entendimento-dos-dados)
  - [Preparação dos Dados](#preparação-dos-dados)
  - [Modelagem](#modelagem)
  - [Avaliação](#avaliação)
  - [Implantação](#implantação)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Como Executar o Projeto](#como-executar-o-projeto)
- [Contribuições](#contribuições)
- [Licença](#licença)

## Descrição do Projeto

Este projeto foi publicado no Kaggle, uma plataforma que promove desafios de ciência de dados. O objetivo é construir um modelo preditivo para identificar o risco de inadimplência em proponentes de cartão de crédito. A base de dados utilizada contém informações detalhadas dos proponentes, como sexo, posse de bens, estado civil, tipo de renda, entre outros.

## Objetivos

### Objetivos do Negócio

O modelo deve auxiliar o mutuário (cliente) a tomar decisões informadas sobre sua própria concessão de crédito, avaliando o risco de inadimplência.

### Objetivos da Modelagem

Desenvolver o melhor modelo preditivo possível para identificar proponentes com alto risco de inadimplência.

## Metodologia CRISP-DM

### Entendimento do Negócio

A primeira etapa do CRISP-DM foca em entender os objetivos e requisitos do negócio. Aqui, nosso foco é criar um modelo que ajude os clientes a avaliarem suas decisões de crédito.

### Entendimento dos Dados

Nesta etapa, exploramos e compreendemos os dados disponíveis. A base de dados inclui 15 variáveis explicativas e uma variável resposta, `mau`, que indica inadimplência.

#### Dicionário de Dados

| Nome da Variável         | Descrição                                          | Tipo   |
| ------------------------ | -------------------------------------------------- | ------ |
| sexo                     | M = 'Masculino'; F = 'Feminino'                    | M/F    |
| posse_de_veiculo         | Y = 'possui'; N = 'não possui'                     | Y/N    |
| posse_de_imovel          | Y = 'possui'; N = 'não possui'                     | Y/N    |
| qtd_filhos               | Quantidade de filhos                               | inteiro|
| tipo_renda               | Tipo de renda (ex: assalariado, autônomo etc)      | texto  |
| educacao                 | Nível de educação (ex: secundário, superior etc)   | texto  |
| estado_civil             | Estado civil (ex: solteiro, casado etc)            | texto  |
| tipo_residencia          | Tipo de residência (ex: casa/apartamento etc)      | texto  |
| idade                    | Idade em anos                                      | inteiro|
| tempo_de_emprego         | Tempo de emprego em anos                           | inteiro|
| possui_celular           | Indica se possui celular (1 = sim, 0 = não)        | binária|
| possui_fone_comercial    | Indica se possui telefone comercial (1 = sim, 0 = não)| binária|
| possui_fone              | Indica se possui telefone (1 = sim, 0 = não)       | binária|
| possui_email             | Indica se possui e-mail (1 = sim, 0 = não)         | binária|
| qt_pessoas_residencia    | Quantidade de pessoas na residência                | inteiro|
| **mau**                  | Indicador de mau pagador (True = mau, False = bom) | binária|

### Preparação dos Dados

Nesta etapa, realizamos as seguintes operações:

- **Seleção**: Os dados já estão pré-selecionados.
- **Limpeza**: Identificação e tratamento de dados faltantes.
- **Construção**: Nenhuma nova variável foi construída neste exercício.
- **Integração**: Temos apenas uma fonte de dados.
- **Formatação**: Os dados já se encontram em formatos úteis.

### Modelagem

Utilizamos a técnica de Random Forest para construir nosso modelo preditivo. O processo de modelagem inclui a divisão dos dados em conjuntos de treino e teste, a construção do modelo e a avaliação da acurácia.

python
´´´from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn import metrics´´´

### Carregar os dados
´´´df = pd.read_csv('demo01.csv')´´´

### Divisão dos dados em treino e teste
´´´
x = df.drop("mau", axis=1)
y = df["mau"]
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.3, random_state=42)´´´

### Treinamento do modelo Random Forest
´´´
clf = RandomForestClassifier(n_estimators=100)
clf.fit(x_train, y_train)´´´

### Avaliação do modelo
´´´
y_pred = clf.predict(x_test)
acc = metrics.accuracy_score(y_test, y_pred)
print('Acurácia: {0:.2f}%'.format(acc*100))´´´

### Avaliação
A avaliação do modelo é realizada através da acurácia, mas futuros projetos podem incluir métricas adicionais para avaliar o impacto do modelo no negócio.

### Implantação
Na etapa final, colocamos o modelo em produção, implementando-o em um sistema que automatiza a aprovação ou rejeição de proponentes de cartão de crédito com base no risco de inadimplência.

## Tecnologias Utilizadas
- Python
- Pandas
- Seaborn
- Matplotlib
- Scikit-learn

## Como Executar o Projeto
Clone este repositório:´´´ git clone https://github.com/seu-usuario/seu-projeto.git´´´
Navegue até o diretório do projeto: ´´´cd seu-projeto´´´
Instale as dependências: ´´´pip install -r requirements.txt´´´
Execute o notebook Jupyter:´´´ jupyter notebook´´´

### Contribuições: 
Contribuições são bem-vindas! Por favor, envie um pull request ou abra uma issue para discutirmos melhorias.


Este README.md fornece uma visão geral clara e estruturada do projeto, facilitando o entendimento e a execução para qualquer pessoa interessada. Ele inclui seções detalhadas sobre o projeto, a metodologia utilizada, e como executar o código, tornando-o acessível e didático.
