# Stochastic Modeling of Gene Circuits in E.coli

## Overview
In this project, I explored how randomness (or stochasticity) influences gene expression in E. coli. Even genetically identical cells can behave differently due to random fluctuations in gene activity. To study this, I used the Gillespie algorithm to simulate gene expression dynamics and compared the results to real-world experimental data from the GSE61633 dataset.

## Implementation

### Data Preparation
- I used microarray expression data from E. coli (GSE61633).
- Specifically, I extracted gene expression from the Wild Type strain (GSM1509588) using BioPython's Affy tools.

### Data Normalization
I applied standard scaling (mean = 0, standard deviation = 1) to normalize the gene expression values for accurate comparison and modeling.

### Exploratory Data Analysis
I visualized the expression distribution and found most genes had low expression (background noise), with a few showing high expression — potential activity hotspots.

### Stochastic Modeling
I built a simple stochastic model with three biological processes:
- Transcription (DNA → mRNA)
- Translation (mRNA → Protein)
- Degradation (mRNA and proteins breaking down over time)

Parameters used in the model:
- Transcription rate: 0.1
- Translation rate: 0.05
- mRNA degradation rate: 0.02
- Protein degradation rate: 0.01

### Simulation
- I ran 50 stochastic simulations using the Gillespie algorithm to observe how mRNA and protein levels change over time.
- Each simulation followed a unique random path, highlighting the inherent variability in biological systems.

### Validation
- I compared the simulated mRNA and protein levels to actual gene expression data.
- mRNA results closely matched the experimental data, while protein results differed, suggesting room for model improvement.

## Results
- Final mRNA levels:
  - Mean: 4.52
  - Standard Deviation: 1.93

- Final protein levels:
  - Mean: 11.98
  - Standard Deviation: 5.43

- Statistical Validation:
  - t-test: Showed no significant difference between experimental and simulated mRNA levels.
  - KS-test: Confirmed a good match for mRNA, but highlighted discrepancies in protein predictions.

## Key Takeaways
1. Gene expression is noisy by nature, and stochastic modeling helps visualize and quantify that noise.
2. My model worked well for mRNA, but needs refinement for protein behavior.
3. Stochastic simulations like this are useful for synthetic biology, genetic circuit design, and understanding gene-level variability in cells.

## Tools & Technologies
- Programming Language: Python
- Key Libraries: gillespy2, pandas, matplotlib, BioPython
- Simulation Method: Gillespie Algorithm
- Notebook: execution_1file.ipynb (used for all modeling and analysis)

## Future Improvements
- Tune parameters to improve protein accuracy
- Add more biological mechanisms (e.g., feedback loops, delays)
- Use real-time or additional datasets to generalize the model
- Explore machine learning to predict or correct simulation results
