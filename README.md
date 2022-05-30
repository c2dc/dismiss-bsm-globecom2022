# DISMISS-BSM: detection of position spoofing in Basic Safety Messages

Basic Safety Messages (BSMs) are crucial for Cooperative Intelligent Transport Systems (C-ITS) and enable the coordination between vehicles.  Further, malicious behavior that alters the content of BSMs can incur disastrous effects.  This paper presents DISMISS-BSM, an algorithm for detecting BSM forgery, implementing a novel misbehavior detection approach.  The messages received by the hosts are buffered and grouped to be passed to detection models, enhancing their proficiency when compared to previous approaches.  As a result of our feature engineering, we derive predictors considering the received signal strength and a movement pattern disruption indicator.   Moreover, we use different sliding window lengths (2, 3, 8, 13, 18, and 23), allowing a better prediction of the dynamic attacker behavior.  Our results outperform the state-of-the-art and indicate that decision trees were the better conformant among K-NN, RF, MLP, and LSTM, performing the average f1-score of 0.897, average of training time at 47.62 sec and average of testing time at 5.43 sec.

This repository contains the notebooks that were used for pre-processing the dataset and for building the detection models, as well as a link to an external repository that contains the CSV files that make up the VeReMi dataset.

This project was developed using Google's Colab and contains all the files necessary for its reproduction.

<!--ts-->
   * [Repository content](#repository-content)
   * [VeReMi dataset](#veremi-dataset)
<!--te-->

## Repository content

- `/preprocessing`: contains the notebooks used to combine the BSM and GPS information of each message received by the vehicles, in csv files; 
- `/models`: contains the notebooks used to configure and test the detection models conceived in this work.

## [VeReMi dataset](https://veremi-dataset.github.io/)

The [VeReMi dataset](https://veremi-dataset.github.io/) replicate several traffic scenarios in city of Luxembourg, utilizing the VEINS simulator,  encompassing 225 simulations, each containing a labeling file (ground truth) and a set of records of messages received by each vehicle that received messages.  The simulations have variations of three levels of vehicular density, three levels of attacker density, and five different types of attackers, and each combination of parameters was replicated five times, totaling 225 simulation rounds.  In addition, vehicle records have two types of messages, type 2 messages, vehicle telemetry data, and type 3 messages, containing Basic Safety Messages (BSM) data received from other vehicles by DSRC.

In order to facilitate the handling of the files and speed up the execution of the experiments, we transposed the VeReMi reports to .csv files, merging the type 2 (GPS) and 3 (BSM) messages. However, due to the size of the files, the resulting csv is stored in an [external repository](https://mega.nz/folder/5Bp2QCSY#TxAiyrJOmt9itJ12K6Lxlw).
