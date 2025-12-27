Real-Time DDoS Detection on CPU-Only Edge Gateways Using an Ultra-Lightweight MLP

High-resolution performance visualization 

This repository contains the complete source code, Jupyter notebook

The project evaluates a compact 4-layer multilayer perceptron (MLP) for binary DDoS attack detection across three benchmark datasets: KDD Cup 1999, CIC-DDoS2019, and Edge-IIoTset. The detector achieves 99.96% accuracy and zero false positives on KDD Cup 1999, perfect recall (0% FNR) on Edge-IIoTset, and sub-130 µs inference latency on CPU-only hardware, making it highly suitable for resource-constrained Industrial IoT (IIoT) and edge gateway deployments.

Repository Structure
```
.
├── models/FINAL_WORKING/      # Serialized trained detectors (.pkl) for each dataset
├── visualizations/            # High-resolution figures (performance bars, latency, final table)
├── FINAL_99PERCENT_METRICS.csv # Final evaluation metrics
├── notebook.ipynb             # Complete reproducible pipeline (preprocessing, training, evaluation, visualization)
├── requirements.txt           # Python dependencies
├── README.md                  # This file
└── data/                      # (Not included – datasets are public; see download links below)
```

Datasets (Public – Download Separately)
The experiments use three publicly available benchmark datasets:
- KDD Cup 1999
  Link: http://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html
- CIC-DDoS2019
  Link: https://www.unb.ca/cic/datasets/ddos-2019.html
- Edge-IIoTset
  Link: https://ieee-dataport.org/documents/edge-iiotset-new-comprehensive-realistic-cyber-security-dataset-iot-and-iiot-applications

Instructions:  
Modify the path in Cell 3 to match your local structure.

 Quick Start
1. Clone the repository
   ```bash
   git clone https://github.com/
   
2. Create and activate a virtual environment (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate    # Linux/macOS
   venv\Scripts\activate       # Windows
   ```
3. Install dependencies
   ```bash
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
   pip install numpy pandas scikit-learn matplotlib seaborn tqdm joblib
   ```
4. Run the notebook
   - Open `notebook.ipynb` in Jupyter Notebook/Lab or VS Code.
   - Execute all cells sequentially.
   
   The notebook automatically:
   - Loads and preprocesses the three datasets (memory-safe, realistic 30% attack ratio where applicable)
   - Trains the lightweight MLP detector (with dataset-specific regularization for Edge-IIoTset)
   - Evaluates performance and computes all metrics
   - Generates high-resolution visualizations
   - Saves trained models and scalers

 Key Results (Reproduced from Notebook)
- KDD Cup 1999: 99.96% accuracy, 0.0000% FPR, 0.099 ms latency
- CIC-DDoS2019: 94.94% accuracy, 0.098 ms latency
- Edge-IIoTset: 97.27% accuracy, perfect recall (0.00% FNR), 0.127 ms latency
- Single-threaded throughput: 7,723–9,928 packets/second
- Peak memory: < 350 MB
- Model size: < 650 KB per dataset

Real-Time Deployment
The serialized models (`.pkl`) and scalers can be loaded with `joblib` for inference using only PyTorch CPU, no GPU required. A minimal deployment script can be derived from the evaluation section of the notebook for integration into Windows-based edge gateways.

Citation
If you use this code or results in your work, please cite:

```bibtex
Mikiyas Alemayehu and Mohamed Chahine Ghanem and Hamza Kheddar and Dipo Dunsin},

  year = {2026}
}
```

License
This project is released under the MIT License.

Contact
For questions or collaboration, please open an issue or contact the corresponding author.

---
Thank you for your interest! Feel free to star the repository or submit pull requests.
```
