# ssdp
SSDP is an evolutionary algorithm for Discriminative Pattern (DP) mining that focuses on high dimensional data sets. A friendly black box version for SSDP usage is being developed.

# Description of the folders

#experiments
Experiments results.
Confrontation between the 8 SSDP versions tested on 121 high-dimensional bases: BIO-126-8SSDP-Qg-Tabelao.csvs
Confrontation between SSDP, SD, Trivial and Random search 121 high-dimensional bases: BIO-126-SSDPauto3x3xSDxTrivialxRamdon3M-Qg-Tabelao-nomeClean.csv
Confrontation between SSDP and evolutionary approach on 20 traditional bases: UCI-20-SSDPxNMEEFxMESDIFxSDIGA-Tabelao.csv

#ssdp
Java implementation of SSDP.
Class Main: it is a self explanatory way how to run the algorithm.

#data
10 microarray databases following the format accepted by the Java implementation. Basically they are .csv files where the label is in the last column.
