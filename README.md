# Description
<a href="https://github.com/spartanjoax/TOCOM">
    <img src="https://img.shields.io/badge/Python-3.7%20%7C%203.8-blue?style=for-the-badge&logo=python" />
</a>

Technical validation code for the TOol COndition MONitoring (TOCOMON) face-milling dataset.

# Acknowledgements
This work was developed at the [Software and systems engineering](https://www.mondragon.edu/en/research-transfer/engineering-technology/research-and-transfer-groups/-/mu-inv-mapping/grupo/ingenieria-del-sw-y-sistemas) and the [High-performance machining](https://www.mondragon.edu/en/research-transfer/engineering-technology/research-and-transfer-groups/-/mu-inv-mapping/grupo/mecanizado-de-alto-rendimiento) groups at Mondragon University, as part of the [Digital Manufacturing and Design Training Network](https://dimanditn.eu/es/home).

This project has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 814078.

# Installation
1. Fork the project.
2. Clone the project.
3. Follow the instructions in the [link](#usage) section.

# Usage
This code is meant to be used alongside the TOCOM face-milling dataset. This repository provides three main scripts to process and evaluate the TOCOMON dataset. Below are instructions for each script:

1. **Signal_sync.py** (Signal synchroniser):
This script handles the synchronization of internal and external signals, aligning them based on peak analysis to ensure that all data sources are accurately aligned for further analysis. 

```bash
   python Signal_sync.py --input_dir <path_to_raw_data> --output_dir <path_to_synced_data>
```
- `--input_dir`: Path to the directory containing the unsynchronised signal data. Default value is `../tocomon_unsynced"`.
- `--output_dir`: Path to the directory where synchronised data will be saved. Default value is `../tocomon_synced`. A CSV file (`signals_sync.csv`) with the synchronisation selections is saved also in this directory  upon script completion.

2. **Signal_feature_extraction.py** (Signal feature extraction):
This script performs feature extraction on the synchronized signals, generating time, frequency, and time-frequency-domain features (e.g., RMS, kurtosis, peak-to-peak, wavelet energy) that can be used for tool condition monitoring (TCM) analysis.

```bash
python Signal_feature_extraction.py --input_dir <path_to_synced_data>
```
- `--input_dir`: Path to the directory containing synchronized data. Default value is `../tocomon_synced`. A CSV file (`signals_stats.csv`) with the extracted features is saved in this directory upon script completion.

3. **Signal_evaluator.py** (Signal evaluation):
This script evaluates the extracted features against tool wear annotations, providing insights into which features show strong correlations with tool wear, and is useful for understanding the most relevant metrics for TCM.

```bash
python Signal_evaluator.py --features_path <path_to_features_file>
```
- `--features_path`: Path to the file containing the extracted features. Default value is `../tocomon_synced/signals_stats.csv`.

# Example Workflow
1. **Step 1**: Synchronize Signals

Run Signal_sync.py to align raw signals from different sources, creating synchronized files ready for feature extraction.

2. **Step 2**: Extract Features

Use Signal_feature_extraction.py to process synchronized signals and extract a range of relevant features.

3. **Step 3**: Evaluate Features

Finally, apply Signal_evaluator.py to analyze the extracted features against tool wear data, identifying metrics most associated with tool wear progression.

This sequence allows users to go from raw data to insights on the most relevant features for tool condition monitoring in milling processes.

# Contributors

[//]: contributor-faces

<a href="https://github.com/spartanjoax"><img src="https://avatars.githubusercontent.com/u/29443664?v=4" title="José Joaquín Peralta Abadía" width="80" height="80"></a>

[//]: contributor-faces

# Cite

If you use this code in your own work, please use the following bibtex entries:

```bibtex
@misc{tocom2024, 
  title={Technical validation code for TOCOMON -- Face-milling dataset for smart tool condition monitoring}, 
  author={Peralta Abadia, Jose Joaquin}, 
  year={2024}, 
  publisher={GitHub}, 
  howpublished={\url{https://github.com/spartanjoax/TOCOM}} }
  
@article{peralta2025tocomon,
  title={{TOCOMON -- Face-milling dataset for smart tool condition monitoring}},
  author={Peralta Abadia, Jose Joaquin and Cuesta Zabaljauregui, Mikel and Larrinaga Barrenechea, Felix},
  journal={...pending...},
  year={2025}
}
```