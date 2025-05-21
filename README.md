# Computational-Biomechanics-Modeling-Public-Repo
Public repo housing project summary for projects, analysis, and end-to-end research tools developed as part of PhD research. Contact for more details.

Below, I have attached a public-facing readme project summary describing. Currently, data and code is not publically available. Key results are summarized below and key published figures (redacted here) can be found here (https://journals.physiology.org/doi/abs/10.1152/ajpheart.00098.2024) and here (https://pmc.ncbi.nlm.nih.gov/articles/PMC8794227/).


# Computational Biomechanics & Hemodynamics Analysis  
*Computational tools primarily in Python/MATLAB for cardiac biomechanics modeling and hemodynamics characterizations from my PhD research.*  

---

## 📌 Table of Contents  
1. [Scientific Motivation](#-scientific-motivation)  
2. [Repository Structure](#-repository-structure)  
3. [Key Features](#-key-features)  
4. [Results](#-results)  
5. [Summary](#-summary)
6. [Considerations & Limitations](#-considerations--limitations)  
7. [License](#-license)

---

## 🔬 Scientific Motivation  
The heart is dynamic and can undergo a variety of changes to maintain it's function in response to disease. While it is known that the muscular ventricular chambers of the heart can adapt and remodel to maintain cardiac output, how and why the ventricle progresses to heart failure remains unknown.

The study of cardiac biomechanics via clinical and experimental methods have been performed for over a century but are often challenged by the complexity of the system, of which numerous mechanical, biological, and electrophysiological systems operate in harmony to perform cardiac functions. Herein lies the value of  computational approaches, which have become increasingly popular to supplement these studies. One such use is to decouple the multi-faceted biological complexity, facilitating the investigation of isolated molecular or cellular mechanisms.

Here, we present one such computational model which we created to model the function of the right ventricle, the most important clinical indicator in pulmonary hypertension. By applying clinical and experimental data to a mathematical biomechanics framework, parameters of our model can be fitted to produce new insights into health and disease.

This repository contains computational tools developed during my PhD to:  
- **Model** heart function using physics-based biomechanics modeling, BFGS optimization, and linear and non-linear regression analysis.  
- **Analyze** cardiac fluctuations, tissue mechanics, and ventricular hemodynamics in health and in pulmonary arterial hypertension.  
- **Bridge gaps** between experimental studies and clinical outcomes using computational methods.  

**Key Questions Addressed**:  
- How does ventricular biological and mechanical changes affect emerging cardiac function?  
- What patterns of cardiac changes emerge during pulmonary hypertension?
- How can we better tailor clinical care for distinct pulmonary hypertension populations?

---

## 🗂 Repository Structure 
/src/

├── Computational biomechanics analysis/ # Python-based biomechanics tools <br>
│ ├── DiseaseModelExample.py # Core tissue mechanics model<br>
| ├── BFGS__model_optimization.py # BFGS solver for parameter fitting<br>
│ └── helpers/ # Subdirectory for core model helper functions<br>
│<br>
├── Hemodynamics analysis/ # MATLAB hemodynamics scripts<br>
│ ├── SteadyStatePVLoopAnalysis.m # Steady-state heartbeat analysis<br>
│ ├── PVLoopGeneration.m #Backend PV loop generation for steady state analysis<br>
│ ├── MultibeatOcclusionAnalysis.m # Dynamic occlusion response modeling<br>

<br>
/sample data/ # Example inputs/outputs<br>

│ ├── SampleDiseasedPVOcclusionRawData.txt # Synthetic raw experimental occlusion data<br>
│ ├──SampleDiseasedPVSteadyStateRawData.txt #Synthetic raw experimental steady state catheter data<br>
│ ├── SamplePVOcclusionProcessedData.xlsx # Synthetic processed heart blood pressure- chamber volume data during occlusion<br>
│ └── Multibeat occlusion analysis of sample data/ # Sample analysis results<br>

<br>
/figures/ # Key results<br>

├── 1. Modeling Results <br>
| └── Baseline Parameter Fitting.png <br>
| └── Interpreting Model Parameter Fits.png <br>
| └── Parameter Optimization Results.png <br>
├── 2. Biomechanics Analysis<br>
| └── Analyzing Model Parameter Combinations.png <br>
| └── Decoupling Geometric and Material Changes using Model.png #<br>
├── 3. Applications<br>
| └── Applying model to study sex differences in PAH.png <br>
| └── Charting RV Remodeling Timecourse using Model.png <br>


## Key Features
located in /src/
Hemodynamics Analysis

1) Steady state heartbeat analysis:
- Open SteadyStatePVLoopAnalysis.m in matlab. 
- Run the script, loading sample steady state data from /sample_data/SampleDiseasedPVSteadyStateRawData.txt.

2) Heart response to preload variation (occlusion) analysis:
- Open MultibeatOcclusionAnalysis.m in matlab.
- Run the script, loading sample occlusion data from /sample_data/SampleDiseasedPVOcclusionRawData.txt.

Computational Biomechanics Analysis
3) Computational Biomechanics model generation
- Open DiseaseModelExample.py
- Run the script, loading sample pre-processed occlusion data from /sample_data/SamplePVOcclusionProcessedData.xlsx

## 📊 Results
Biomechanics
### Biomechanical Model Fits  

*Figure 1: The model was fitted to healthy clinical data (mean +/-SEM). Model parameters representing the material stiffness (k1 and k2) and contractility (k3) were tuned to match control data during contraction and relaxation. Parameters generated using BFGS (Python implementation in `/src/Computational biomechanics analysis/`).*  

*Figure 2: Root mean squared errors of the computational model predictions of the emergent parameter end-diastolic (A) and end-systolic (B) blood pressure-volume data, show as a percent of the measured true values. For most timepoints, the RMSE remained under 10%. Parameters were optimized using BFGS (Python implementation in `/src/Computational biomechanics analysis/`).*  
<br>

*Figure 3: Model predictions (lines) vs. experimental data (mean+/sem) using 3 sets of parameter combinations: 1) The parameter set optimized to match healthy patient data (green); 2) The parameter set optimized to match healthy patient mechanical properties but disease morphology (black); 3) The parameter set optimized to match both disease morphology and mechanical properties (blue). These combinations reveal the relative importance of these decoupled changes. The model parameter Vw dominated the systolic response while k1 and k2 dominated the diastolic response. Parameters generated using BFGS (Python implementation in `/src/Computational biomechanics analysis/`).*  
<br>

*Figure 4: Healthy (white) and diseased (grey) clinical data shown next to the three model parameter sets for end-systolic (A) and end-diastolic (B) function. *, #, and £ indicate significant additional contributions from each material parameter addition.
<br>

*Figure 5: The model was applied to healthy (black) and PAH (green) groups of males (A) females (B) and estrogen-depleted females (C) and used to generate sarcomeric stress-strain relationships. The model revealed significant passive myocardial stiffening in disease that was the most severe in males. While the slope of the active stress-strain relation increased in disease, only the estrogen-depleted females showed significant differences in active tension. *Figure 5 is a reproduction in part of data published in the American Journal of Physiology (PubMed ID: 38847755).
<br>

Figure 6: The model was applied to clinical data obtained over a range of longitudinal timepoints. This allowed for the discovery of a novel time course of remodeling, by which rapid hypertrophy initially stabilized RV function over 5 weeks, after which significant diastolic stiffening occurred. *Figure 6 is a reproduction in part of data published in the American Journal of Physiology (PubMed ID: 34448637)
<br>


## 🔍 Summary
We present a computational implementation of a mathematical framework to characterize the remodeling of the biomechanics of the right ventricle in both systole and diastole. Our repository shows a few examples of this modeling framework applied to synthetic experimental data. 
We also applied this modeling framework over several scientific studies** to answer our scientific questions.

[Key finding 1]: Systolic ventricular function is primarily stabilized by hypertrophic thickening of the ventricular wall, while diastolic chamber stiffening was explaining by myocardium passive stiffening.

[Key finding 2]: During PAH, the rapid onset of pressure overload is initially stabilized by hypertrophic wall thickening, which was followed by a sequence of diastolic passive stiffness which may contribute to long-term failure

[Key finding 3]: PAH and the cardiac response is strongly sex-dependent. Passive stiffening was most severe in males. While females responded to pressure overload primarily with hypertrophy, estrogen-depleted females upregulated myofiber contractility. These distinct molecular mechanisms may explain differences in long term patient outcomes. These populations may also better respond to distinct mechanism-specific therapy.

## ⚠️ Considerations & Limitations
Data: Sample data is synthetic; real datasets require [institutional approval] from the University of California San Diego.

Access: While key features and implementation are openly accessible from this repository and run self-sufficiently, the study design, research pipeline, and computational model itself are NOT open source in it's entirety. Any derivative scientific findings or publications using this work are subject to standard academic and research licensing and protocols.

Dependencies: included in repository.

Scalability: BFGS optimization scales as O(n²) for large parameter sets.

**For full context, see my PhD Dissertation (Kwan et al. Right Ventricular Remodeling in Pulmonary Arterial Hypertension), located at [https://escholarship.org/uc/item/4295j3cd]

## 📜 License  
- **Code**: [CC-BY-NC-4.0](LICENSE) *(Non-commercial use only)*  
- **Data/Figures**: [CC-BY-NC-4.0](LICENSE) *(Non-commercial use only)*  
