
# AdaptiCritters: Natural Selection Simulator

AdaptiCritters is an interactive Java-based simulation that models natural selection and evolution.
Users can observe how preset genomes, or "Critters," evolve over time in response to environmental pressures.
The simulation provides a means for understanding evolutionary concepts such as adaptation, mutation, and survival of the fittest, all through the lens of evolutionary computation!

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
  - [Compiling the Java Code](#compiling-the-java-code)
  - [Running the Simulation](#running-the-simulation)
- [Project Structure](#project-structure)
- [License](#license)

## Overview

The AdaptiCritters simulator allows users to witness the process of natural selection in a controlled environment using a customizable genetic algorithm.
Critters with varying traits compete for survival, reproduce, and (hopefully) pass on advantageous traits to subsequent generations.
Over time, users can observe the emergence of well-adapted populations, providing insights into evolutionary dynamics.

## Features

- Interactive simulation of natural selection and evolution.
- Visualization of Critter populations and their traits over time.
- Customizable environmental parameters to influence evolutionary outcomes.
- Educational tool for teaching and understanding evolutionary biology concepts.

## Prerequisites

- Java Development Kit (JDK) 8 or higher

To verify Java installation:

```bash
java -version
```

## Usage


### Input File and Scenario Generation Instructions for AdaptiCritters

#### Input File Structure

AdaptiCritters uses a template input file (typically named `template.txt`) to define the genome, events, and environmental interactions that drive simulation. The structure of the input file is critical to initializing a realistic and functional evolutionary model.

#### Example Input Format

```
4                       # Number of genes
6 +49 +42 -30 +16 x -25 # Alleles for gene 1 (x denotes lethal allele)
5 -47 x -38 +12 +24     # Alleles for gene 2
8 +19 +36 -1 +12 x -40 x -13
2 x -5
1 3                     # Number of events and number of generations per event
2                       # Lethal chance (0.1 = 10% chance)
+9 +1 +9 +8 x -4        # Event 1: allele modifiers
+0 x -8 +1 -6           # Event 2
+8 +4 +6 +10 x +5 x +1  # Event 3
x +9                   # Event 4
```

#### Explanation

- The first line defines the **number of genes**.
- Each subsequent line defines the **alleles** for each gene.
  - Alleles are integers indicating fitness contribution.
  - `x` marks **lethal alleles** with a fitness of -1,000,000.
- After the genes, two numbers define:
  - **Number of events**
  - **Number of generations per event**
- Next line: **Lethal allele chance** as a percent (e.g., `2` = 0.1 probability).
- Remaining lines: **Event modifier matrices**, one per generation per event.

### Using the Simulation Generators

The simulator can **auto-generate realistic simulation templates** with customizable parameters:
- Genome complexity (number of genes and alleles)
- Frequency and strength of events
- Probability of lethal alleles

To auto-generate a simulation scenario:

1. Use the generator script included in the GUI or initialize the Java simulation with:
```bash
SimulationGenerator.java
```
,
```bash
SimulationGeneratorCataclysms.java
```
or
```bash
SimulationGeneratorInversion.java
```

2. Set parameters in the config file (example shown below) to point to your custom template:
```
Experiment ID                :adapticritters
Problem Type                 :AC
Data Input File Name         :template.txt
Number of Runs               :1
Generations per Run          :20
Population Size              :100
Fecundity                    :2
Fitness Threshold            :0
Mutation Rate                :.01
```

3. Run the simulation and observe phenotypic evolution over time.

## Genetic Algorithm Representation

The GA encodes each **phenotype** as a 1D array of selected alleles, one per gene. The **fitness** of an individual is the sum of its alleles’ contributions. During simulation:

- **Lethal alleles** instantly cause death.
- **Events** modify allele values for all current and future individuals.
- **Cataclysms** simulate large-scale shifts (e.g., -50 to 0 fitness drops).
- **Uniform crossover** and **mutation** promote genetic diversity.
- **Fitness threshold** kills individuals below a set fitness value.

This structure allows AdaptiCritters to model realistic population dynamics and evolutionary adaptation under simulated environmental pressures.

## Tips

- Use the GUI to build templates and visualize allele/family trees.
- Maintain reasonable population sizes to avoid computational overload.
- Tweak event density and strength to simulate specific evolutionary hypotheses.

For more details, see the `Final Project Report.pdf` in this repository.

---

### Compiling the Java Code

Navigate to the project directory and compile the Java source files:

```bash
javac *.java
```

This command compiles all Java files in the directory.

### Running the Simulation

After successful compilation, run the main class to start the simulation:

```bash
java Main
```

The simulation window will launch, displaying the Critter population and their interactions within the environment.

## Project Structure

```
├── Final Project Report.pdf  # Fully detailed report about this project!
├── Main.java                 # Entry point of the application
├── Critter.java              # Defines the Critter class and its behaviors
├── Environment.java          # Manages the simulation environment and parameters
├── SimulationPanel.java      # Handles the graphical representation of the simulation
├── Utils.java                # Utility functions supporting the simulation
├── SimulationGenerator.java  # Generic simulation template generation
├── SimulationGeneratorCataclysms.java  # Generates templates with preset cataclysmic environmental events
├── SimulationGeneratorInversion.java   # Generates templates designed to completely reverse which genes are advantageous over time within environment
├── README.md                 # Project documentation
└── LICENSE                   # License information
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to explore and modify the simulation parameters to observe different evolutionary outcomes.
If you have any questions or suggestions, please contact [Justin Morera](mailto:mustinjorera@gmail.com).

Developed by Justin Morera, Darren Bansil, and Christian King at the University of Central Florida.
