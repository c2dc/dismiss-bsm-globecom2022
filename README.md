# DISMISS-BSM: uma arquitetura para detecção de falsifição de Basic Safety Messages

Basic Safety Messages (BSMs) são cruciais para sistemas de transportes inteligentes e cooperativos (C-ITS) e habilitam o sincronismo entre os veículos no sistema.   No entanto, a identificação adaptativa da falsificação do conteúdo das BSMs com baixo tempo de aprendizado e inferência é um desafio.  Neste trabalho apresenta-se (i) DISMISS-BSM, uma arquitetura para detecção de falsificação de BSM, e (ii) a especificação dos atributos preditores de potência do sinal recebido, ruptura do padrão de deslocamento e janela deslizante com 3 mensagens.  Foram testados os modelos SVM, MLP e LSTM e k-NN, este último obtendo a melhor adequação com treinamento médio de 70 e 30 segundos para os preditores potência do sinal e conformidade de deslocamento (feature 1 e 2), respectivamente.

Este repositório contém os notebooks que foram utilizados para o pré-processamento do dataset e para construção dos modelos de detecção, além de um link para um repositório externo que contém os arquivos CSV que constituem o dataset VeReMi.

Este projeto foi desenvolvido utilizando-se o Colab, do Google, e contém todos os arquivos necessários para sua reprodução.

<!--ts-->
   * [Conteúdo do repositório](#conteúdo-do-repositório)
   * [dataset VeReMi](#dataset-veremi)
<!--te-->

## Conteúdo do repositório

- `/preprocessing`: contém os notebooks utilizados para unir as informações das BSM e do GPS de cada mensagem recebida pelos veículos, em arquivos csv; 
- `/models`: contém os notebooks utilizados para configuração e teste dos modelos de detecção concebidos neste trabalho;
  - Os códigos dos pré-processamentos do dataset, conforme as features 1 e 2, estão incluídos nos notebooks `mlpfeat1` e `mlpfeat2`;
  - Os arquivos csv pré-processados das features 1 e 2, estão disponíveis em repositório externo, nos links [feat1](https://mega.nz/folder/1Io20AiA#JyVkFM97zrJVOfMyqsPSrw) e [feat2](https://mega.nz/folder/8YIXQY7b#ivBcMXLcT5lpo_yic-TBaw).

## Dataset [VeReMi](https://veremi-dataset.github.io/)

O conjunto de dados [VeReMi](https://veremi-dataset.github.io/) é composto por 225 simulações, cada uma contendo um arquivo de rotulação *ground truth* e um conjunto de registros das mensagens recebidas por cada veículo que recebeu mensagens. As simulações possuem variações de três níveis de densidade veicular, três níveis de densidade de atacantes e cinco diferentes tipos de atacantes, tendo cada combinação de parâmetros sido replicada cinco vezes, totalizando 225 rodadas de simulações. Os registros dos veículos possuem dois tipos de mensagens, as mensagens de tipo 2, que são dados de telemetria do veículo (GPS), e as mensagens do tipo 3, contendo os dados das Basic Safety Messages (BSM) recebidas dos demais veículos por DSRC.

De modo a facilitar o manejo dos arquivos e acelerar a execução dos experimentos, transpusemos os relatórios do VeReMi para arquivos .csv, unindo as mensagens do tipo 2 (GPS) e 3 (BSM). No entanto, devido ao tamanho dos arquivos, os csv resultantes estão armazenados em um [repositório externo](https://mega.nz/folder/kZxyRaja#A4oPyqyR4-Sl4hd5jf_MzQ).