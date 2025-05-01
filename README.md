# DigTwinEconometrics
Simple model to test Technology and Policy for Rural Areas Development
This repository includes all the materials attached to the research paper "Digital Twin Framework for Lika-Senj: simple model to test Technology and Policy for Rural Areas Development"
All code and scripts developed for this study are publicly available under an open-source license, granting permission for reuse and modification by other scholars for research purposes.
#  Instructions
1. Download Miniconda. If using a Windows system, here is the link:
https://www.anaconda.com/docs/getting-started/anaconda/install#windows-installation
2. Install the latest version of Python on your device
3. Create the structure of the folders as in the following figure (everything is already included in the zip file attached). Put all the scripts in the folder “script” Create the folder structure as shown in the following figure. Place all scripts in the “script” folder and the configuration file in “config”
   
![image](https://github.com/user-attachments/assets/52bae506-d3fc-45e3-9f63-f954ecfdc6ce)

5. In the scripts, ensure that all paths are customised (replace all instances marked with [insert your path] in the scripts with your own path).


# Reproducibility Protocol
## 1. Setup
Create environment:
conda create -n rural_digital python=3.9
conda activate rural_digital
pip install -r requirements.txt

## 2. Download geospatial data:
python scripts/01_data_generation.py --download_osm

## 3. Execution
### Full pipeline
python run_pipeline.py --config config/model_params.yml

or
### Individual components
python scripts/02_abm_simulation.py --input data/synthetic/farmers.geojson

## 4. Output Analysis

a) ABM Results: outputs/metrics/adoption_rate.csv

b) Economic Trends:

outputs/visualizations/gdp_trend.png

python scripts/03_system_dynamics.py

c) AR Kiosks: outputs/geospatial/kiosks.geojson

python scripts/04_geospatial_opt.py

## 5. Validation & Extension

### Tests
#### test_abm.py

def test_adoption_threshold():

    model = RuralModel(farmers_with_low_income)
    
    model.run_for(10)
    
    assert model.dc.model_vars['adoption'][-1] < 0.2
    

## Key Features

•	Complete Isolation: All paths relative to project root

•	Parameterized: YAML config for easy adjustments

•	Modular: Swap ABM/SD implementations without breaking pipeline

•	Reproducible: Seed control for stochastic processes

