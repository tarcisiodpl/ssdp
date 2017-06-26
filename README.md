# Introduction
SSDP is an evolutionary algorithm for Discriminative Pattern (DP) mining that focuses on high dimensional data sets.

# Reference: 
Tarcísio Lucas, Túlio C.P.B. Silva, Renato Vimieiro, Teresa B. Ludermir, A new evolutionary algorithm for mining top-k discriminative patterns in high dimensional data, Applied Soft Computing, Volume 59, October 2017, Pages 487-499, ISSN 1568-4946, https://doi.org/10.1016/j.asoc.2017.05.048.

Description folders:

# SSDP
Java implementation of SSDP.
Class Main is a self explanatory way how to run the algorithm:

        //====================================================================
        //== CONFIGURATION ===================================================
        //====================================================================
        //CSV database path
        String caminho = "C:\\Users\\Tarcisio  Lucas\\Documents\\NetBeansProjects\\SSDP\\pastas\\bases\\"; 
        //String nomeBase = "audiology_pn.CSV";
        String nomeBase = "alon-pn-freq-2.CSV";
        String caminhoBase = caminho + nomeBase;
       
        D.SEPARADOR = ","; //separator database
        Const.random = new Random(Const.SEEDS[0]); //Seed - 30 options
        
        //Parameters of the algorithm
        int k = 10; //number of DPs
        //String tipoAvaliacao = Avaliador.TIPO_WRACC; //Fitness
        String tipoAvaliacao = Avaliador.TIPO_QG; //Fitness
        //String tipoAvaliacao = Avaliador.TIPO_SUB; //Fitness
        D.valorAlvo = "p"; //target value of dataset
        
        //====================================================================
        //= END ==============================================================
        //====================================================================
               
        D.CarregarArquivo(caminhoBase, D.TIPO_CSV); //Loading database         
        Pattern.numeroIndividuosGerados = 0; //Initializing count of generated individuals by SSDP
                            
        //Rodando SSDP
        long t0 = System.currentTimeMillis(); //Initial time
        Pattern[] p = SSDP_MxC_Auto_3x3.run(k, tipoAvaliacao); //run SSDP
        double tempo = (System.currentTimeMillis() - t0)/1000.0; //time
        
        //Informations about top-k DPs:  
        System.out.println("### Base:" + D.nomeBase); //database name
        System.out.println("Average " + tipoAvaliacao + ": " + Avaliador.avaliarMedia(p, k));
        System.out.println("Time(s): " + tempo);
        System.out.println("Average size: " + Avaliador.avaliarMediaDimensoes(p,k));        
        System.out.println("Coverage of all k DPs in relation to D+: " + Avaliador.coberturaPositivo(p, k)*100 + "%");
        System.out.println("Number of individuals generated: " + Pattern.numeroIndividuosGerados);
        System.out.println("\n### Top-k DPs:");
        Avaliador.imprimirRegras(p, k);

# experiments:
Experiments results:

Confrontation between the 8 SSDP versions tested on 121 high-dimensional bases: BIO-126-8SSDP-Qg-Tabelao.csvs

Confrontation between SSDP, SD, Trivial and Random search 121 high-dimensional bases: BIO-126-SSDPauto3x3xSDxTrivialxRamdon3M-Qg-Tabelao-nomeClean.csv

Confrontation between SSDP and evolutionary approach on 20 traditional bases: UCI-20-SSDPxNMEEFxMESDIFxSDIGA-Tabelao.csv

# data:
10 microarray databases following the format accepted by the Java implementation. Basically they are .csv files where the label is in the last column.
