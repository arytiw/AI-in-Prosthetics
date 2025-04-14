# AI in Prosthetics: EMG Signal Processing with GAN and LSTM Models

This repository presents two complementary approaches for processing EMG (electromyography) signals in the context of AI-powered prosthetic control. The work is part of a research effort to compare a Generative Adversarial Network (GAN) model and an LSTM-based model for denoising, feature extraction, and classification of EMG signals. The comparative insights from these experiments feed into our collaborative paper on advanced signal processing methodologies for prosthetics.

---

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Models](#models)
  - [GAN Model](#gan-model)
  - [LSTM Model](#lstm-model)
- [Installation](#installation)
- [Usage](#usage)
- [Training and Evaluation](#training-and-evaluation)
- [Experimental Comparison](#experimental-comparison)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## Overview

EMG signals are critical for understanding muscular activity and controlling prosthetic devices. However, due to their inherent noise and variability, sophisticated processing techniques are required. This project explores two innovative approaches:

- **GAN-based Model:**  
  Uses adversarial learning to synthesize and enhance EMG signals, improving data quality for downstream tasks.
  
- **LSTM-based Model:**  
  Utilizes Long Short-Term Memory (LSTM) networks to capture temporal dependencies in EMG data for accurate signal classification and prosthetic control.

The goal of this repository is to provide a platform for comparing the performance and robustness of these approaches in real-time prosthetic applications.

---

## Project Structure

AI-in-Prosthetics/ ├── data/ │ └── [EMG datasets and test files] ├── models/ │ ├── gan_model.py # GAN model implementation for synthetic signal generation and enhancement │ └── lstm_model.py # LSTM model for EMG signal classification and prosthetic control ├── utils/ │ ├── preprocessing.py # Functions for signal cleaning, wavelet denoising, and normalization │ └── visualization.py # Scripts for plotting training results, signal comparisons, etc. ├── experiments/ │ └── comparison_analysis.md # Documentation and notes for experimental comparisons ├── main.py # Entry point to run training and evaluation ├── requirements.txt # Python dependencies and package versions └── README.md # This file

markdown
Copy
Edit

- **data/**: Contains the CSV files and other datasets.
- **models/**: Holds the implementation of both the GAN and LSTM models.
- **utils/**: Utility scripts for data preprocessing and visualization.
- **experiments/**: Documentation of experimental protocols and performance comparison details.
- **main.py**: Primary script to execute the training pipelines for both approaches.

---

## Models

### GAN Model

- **Objective:**  
  The GAN model is designed to enhance EMG signal quality by generating synthetic, denoised signals that can augment training data for better prosthetic control.
  
- **Components:**
  - **Generator:** Uses transposed convolutional layers, batch normalization, and activation functions to generate realistic EMG signals from random noise or corrupted inputs.
  - **Discriminator:** Employs convolutional layers and dense layers to differentiate between authentic and generated signals, thus enforcing the generator to improve continuously.
  
- **Training:**  
  The GAN model is trained adversarially, with the generator learning to "fool" the discriminator while the discriminator fine-tunes its classification capabilities.

### LSTM Model

- **Objective:**  
  The LSTM-based model focuses on capturing temporal patterns inherent in EMG signals to classify various limb motions effectively.
  
- **Architecture:**
  - **Preprocessing:** Raw EMG data is cleaned using wavelet denoising, normalized, and segmented using sliding window techniques.
  - **Network:** Utilizes a series of LSTM layers to capture temporal dependencies, followed by dense layers for final classification.
  
- **Application:**  
  This model is intended to perform real-time classification of EMG signals to control prosthetic devices, offering insights into the dynamic muscle activities.

---

## Installation

### Prerequisites

- Python 3.7+
- (Optional) Anaconda/Miniconda for environment management

### Steps

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/arytiw/AI-in-Prosthetics.git
   cd AI-in-Prosthetics
Create and Activate a Virtual Environment:

bash
Copy
Edit
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
Install Dependencies:

bash
Copy
Edit
pip install -r requirements.txt
If the requirements.txt file is missing, install the following packages manually:

bash
Copy
Edit
pip install tensorflow numpy pandas matplotlib seaborn scikit-learn pywt
Usage
Data Preparation
Place your EMG dataset files (CSV format) in the data/ directory.

Ensure that the files follow the standard format (columns for different EMG channels, subject identifiers, and activity labels).

Running the Models
Train the GAN Model:

bash
Copy
Edit
python main.py --model gan
Train the LSTM Model:

bash
Copy
Edit
python main.py --model lstm
Evaluation:
To evaluate the trained models and visualize the results, use:

bash
Copy
Edit
python main.py --evaluate
Real-time Prediction:
A real-time prediction module is provided, which you can run as follows:

bash
Copy
Edit
python realtime_prediction.py --model_path <path_to_saved_model> --input <path_to_input_data>
Training and Evaluation
The training workflow consists of the following steps:

Preprocessing:
Data cleaning, wavelet denoising, and normalization of EMG signals.

Model Training:

For the GAN model, both the generator and discriminator are trained with adversarial loss.

For the LSTM model, the network is trained using supervised learning with labels.

Evaluation:
Models are evaluated based on accuracy, confusion matrices, and qualitative comparisons of raw vs. processed signals. Detailed training logs, visualizations, and performance metrics are generated and saved during training.

Experimental Comparison
Our research paper compares the two approaches in several aspects:

Signal Quality:
Analysis of noise reduction and signal enhancement by the GAN versus the direct classification using the LSTM.

Classification Accuracy:
Performance metrics from the LSTM model, as well as the improvement in downstream tasks when using GAN-enhanced signals.

Robustness:
Comparison under various noise conditions and data scarcity scenarios.

The results of these analyses, along with graphs and statistical tests, are documented in the experiments/comparison_analysis.md file.

Results
Preliminary outcomes indicate:

The GAN model significantly improves the signal-to-noise ratio by generating realistic synthetic signals.

The LSTM model demonstrates robust temporal learning capabilities, achieving high classification accuracy for prosthetic control.

Comparative experiments show that a hybrid approach (using GAN for data augmentation followed by LSTM classification) may offer the best performance.

Detailed performance metrics, plots, and analysis are provided in the experiments documentation.

Contributing
Contributions are welcome to further refine the models and enhance the experimental analysis. To contribute:

Fork the repository.

Create a feature branch:

bash
Copy
Edit
git checkout -b feature/your-feature-name
Commit your changes with meaningful messages.

Push your branch and open a pull request.

Please ensure your contributions adhere to the project's coding and documentation standards.

License
This project is open-source and available under the MIT License. See the LICENSE file for more details.

Acknowledgments
Collaborators:
Special thanks to all members of our research team.

Funding and Support:
Acknowledge any grants, institutions, or organizations that provided support.

Contact:
For further questions or detailed discussion about the research, please contact [Your Contact Information].

This repository is part of a collaborative research effort comparing GAN-based and LSTM-based approaches for EMG signal processing in prosthetic control.
