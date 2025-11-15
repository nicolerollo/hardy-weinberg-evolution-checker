# hardy-weinberg-evolution-checker
A Java-based Hardy–Weinberg equilibrium and evolution-detection tool.

Hardy–Weinberg Evolution Checker
A population-genetics analysis tool implemented in Java
________________________________________
Overview
This project implements a generic Hardy–Weinberg equilibrium analyzer and evolution detector.
Given recessive phenotype counts across multiple generations, the program:
•	Calculates phenotype frequency (q²)
•	Estimates allele frequencies (p and q)
•	Computes Hardy–Weinberg genotype frequencies (p², 2pq, q²)
•	Tracks allele-frequency changes over time
•	Automatically determines whether evolution has occurred
This tool is trait-agnostic and works for any diploid organism with a simple dominant–recessive trait.
________________________________________
Scientific Background
Under Hardy–Weinberg equilibrium:
p + q = 1
p² + 2pq + q² = 1
Where:
•	p = dominant allele frequency
•	q = recessive allele frequency
•	q² = frequency of recessive phenotype (aa)
•	p² = AA genotype frequency
•	2pq = Aa genotype frequency
From phenotype data:
q² = (# recessive phenotype) / N
q = √(q²)
p = 1 – q
If either p or q changes across generations, the population is not in equilibrium and evolution is occurring.

This reflects real analytical tasks in population genetics and bioinformatics, such as:
•	Evaluating deviations from Hardy–Weinberg equilibrium in variant data
•	Monitoring allele-frequency shifts in longitudinal studies
•	Identifying selection, drift, or non-random mating
________________________________________
Program Features
•	User inputs phenotype data per generation
•	Supports any number of generations
•	Automatically computes:
o	q², q, p
o	p², 2pq, q² (genotype frequencies)
o	Δp, Δq (allele-frequency changes)
•	Provides an evolution verdict
•	Includes a run-again loop for repeated analyses
________________________________________
Example Output
Number of generations to analyze: 3

Generation 1:
  Total population size (N): 100
  Number with recessive phenotype (aa): 25

Generation 2:
  Total population size (N): 100
  Number with recessive phenotype (aa): 20

Generation 3:
  Total population size (N): 100
  Number with recessive phenotype (aa): 15

--- Table 1: Phenotype Data ---
Gen    Total(N)   Recessive(aa)      q^2       
1            100             25                           0.2500    
2            100             20                           0.2000    
3            100             15                           0.1500    

--- Table 2: Allele & Genotype Frequencies ---
Gen    p^2(AA)    2pq(Aa)    q^2(aa)    p                 q         
1          0.2500       0.5000      0.2500     0.5000     0.5000    
2          0.3056       0.4944      0.2000     0.5528     0.4472    
3          0.3754       0.4746      0.1500     0.6127     0.3873    

--- Allele Frequency Changes ---
Gen    p                 q                 Δp              Δq        
1          0.5000     0.5000     0.0000     0.0000    
2          0.5528     0.4472     0.0528     -0.0528   
3          0.6127     0.3873     0.1127     -0.1127   

--- Evolution Verdict ---
Evolution is occurring: allele frequencies change across generations.
________________________________________
How to Interpret the Output
The program uses the recessive phenotype frequency (q²) to reconstruct allele frequencies (p and q). Across generations, it compares changes in these frequencies.
In the example above:
•	Generation 1 begins with p = 0.50 and q = 0.50.
•	In Generation 2, q drops to 0.4472, and p rises to 0.5528.
•	By Generation 3, q falls further to 0.3873, while p increases to 0.6127.
Because allele frequencies are not constant, the population is not in Hardy–Weinberg equilibrium.
This indicates that evolution is occurring, driven by some evolutionary force such as selection, drift, migration, or non-random mating.
This mirrors real analyses used in bioinformatics and genomics, such as:
•	Detecting selection signals
•	Analyzing allele frequency trajectories in cohorts
•	Performing quality control in GWAS datasets
•	Monitoring variant shifts over time or across populations
________________________________________
How to Run
1. Compile
javac HardyWeinbergEvolutionChecker.java
2. Execute
java HardyWeinbergEvolutionChecker
________________________________________
