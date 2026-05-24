# Milan Mobile Network Traffic Forecasting

Comparative time series analysis and forecasting of mobile network 
traffic data from Milan, Italy (Nov-Dec 2013).

## Project Overview
This project implements three forecasting models for one-step-ahead 
prediction of mobile internet traffic:
- **ARIMA** — Classical statistical model
- **LSTM** — Long Short-Term Memory neural network
- **GRU** — Gated Recurrent Unit neural network

## Dataset
The dataset was released by Telecom Italia Mobile as part of the 
Big Data Challenge. It contains CDRs across a 100×100 geographical 
grid over November-December 2013.

Download the raw data from:
- [Telecom MI Dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/EGZHFV)
- [Milano Grid](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/QJWLFU)

## How to Run

### Requirements

### Steps

**Option 1 — Using processed data (recommended):**
1. Upload `processed_data.parquet` to your Google Drive at:
   `MyDrive/milan-traffic/processed_data.parquet`
2. Open the notebook in Google Colab
3. Run the startup cell first
4. Run all remaining cells in order

**Option 2 — From raw data:**
1. Download the raw dataset from the Harvard Dataverse links above
2. Place november files in `milan-traffic/november/dataverse_files/`
3. Place december files in `milan-traffic/december/dataverse_files (1)/`
4. Run all cells from the beginning

### Platform
Google Colab with T4 GPU (recommended for Task 3 neural network training)

### Running on Windows / Linux / macOS (Local)

1. Install Python 3.10 or above
2. Install required libraries:
```bash
   pip install pandas numpy matplotlib seaborn scikit-learn statsmodels torch torchvision jupyter
```
3. Launch Jupyter:
```bash
   jupyter notebook
```
4. Open the `.ipynb` file
5. Update file paths in the notebook from `/content/drive/MyDrive/` to your local path
6. Run all cells in order

## Results Summary

| Model | Avg MAPE |
|-------|----------|
| ARIMA | 44.63%   |
| LSTM  | 12.76%   |
| GRU   | 11.99%   |

## Repository Structure
## Author
Emmanuella Briggs

## References
Barlacchi et al., "A multi-source dataset of urban life in the 
city of Milan," Sci. Data, 2015.
