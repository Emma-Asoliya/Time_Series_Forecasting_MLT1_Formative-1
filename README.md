# Milan Mobile Network Traffic Forecasting
### Comparative Time Series Analysis and Forecasting | Nov-Dec 2013

This project implements a complete pipeline for analysing and forecasting 
mobile internet traffic data from the city of Milan, Italy. Three forecasting 
models are compared: ARIMA (statistical), LSTM and GRU (neural networks).

---

## Project Overview

This project implements three forecasting models for one-step-ahead 
prediction of mobile internet traffic:
- **ARIMA** — Classical statistical model
- **LSTM** — Long Short-Term Memory neural network
- **GRU** — Gated Recurrent Unit neural network

---

## Dataset

The dataset was released by Telecom Italia Mobile as part of the 
Big Data Challenge. It contains CDRs across a 100×100 geographical 
grid over November-December 2013, resulting in approximately 
87.8 million observations across 10,000 geographical areas.

Download the raw data from Harvard Dataverse:
- [Telecom MI Dataset](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/EGZHFV)
- [Milano Grid](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/QJWLFU)

---

## Minimum Data to Run Predictions

`sample_3areas.parquet` is provided in this repository.
It contains pre-processed data for the 3 key areas only
(Squares 5161, 4159, 4556) covering Nov-Dec 2013 (0.23 MB).

---

## Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels torch torchvision jupyter
```

---

## How to Run

### Option 1 — Google Colab with Sample Data (Recommended)

1. Download `sample_3areas.parquet` from this repository
2. Upload it to your Google Drive at: `MyDrive/milan-traffic/sample_3areas.parquet`
3. Open the notebook in Google Colab
4. Go to **Runtime → Change runtime type → T4 GPU**
5. In the notebook update the load line to:
```python
   df_all = pd.read_parquet('/content/drive/MyDrive/milan-traffic/sample_3areas.parquet')
```
6. Run the startup cell first then all remaining cells in order

### Option 2 — Google Colab with Full Raw Data

1. Download the complete dataset from Harvard Dataverse links above
2. Upload to Google Drive with this structure:`MyDrive/milan-traffic/november/dataverse_files/
MyDrive/milan-traffic/december/dataverse_files (1)/`
3. Open the notebook in Google Colab
4. Enable T4 GPU in Runtime settings
5. Run all cells from the beginning

### Option 3 — Running Locally (Windows / Linux / macOS)

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
5. Update all file paths in the notebook from:`/content/drive/MyDrive/milan-traffic/`
To your local path, for example: `C:/Users/YourName/Documents/milan-traffic/`
6. Run all cells in order

---

## Results Summary

| Model | Sq 5161 MAPE | Sq 4159 MAPE | Sq 4556 MAPE | Avg MAPE |
|-------|-------------|-------------|-------------|----------|
| ARIMA | 52.93%      | 57.38%      | 23.58%      | 44.63%   |
| LSTM  | 17.59%      | 9.83%       | 10.87%      | 12.76%   |
| GRU   | 18.05%      | 8.54%       | 9.39%       | 11.99%   |

**Best performing model: GRU** with an average MAPE of 11.99%

---

## Key Findings

- Traffic distribution is heavily right-skewed — a small number of 
  central areas generate disproportionately high activity
- Strong daily (24-hour) and weekly seasonality identified across all areas
- Square 4556 is non-stationary — differencing applied for ARIMA
- 9 anomalous traffic spikes identified, all on weekend afternoons 
  likely due to stadium or event venue crowds
- GRU outperforms LSTM marginally while being faster to execute
- All models struggle with event-driven anomalous spikes


---

## Hardware Used

| Component | Details |
|-----------|---------|
| Platform  | Google Colab |
| RAM       | 12.67 GB |
| GPU       | NVIDIA T4 |
| Python    | 3.12 |

---

## Author
**Emmanuella Briggs**
Machine Learning Techniques I — Formative Assignment 1

---

## References

[1] G. Barlacchi et al., "A multi-source dataset of urban life in the city of 
Milan and the Province of Trentino," Sci. Data, vol. 2, p. 150055, Oct. 2015.
https://doi.org/10.1038/sdata.2015.55

[2] Telecom Italia, "Telecommunications - SMS, Call, Internet - MI," 
Harvard Dataverse, 2015.
https://doi.org/10.7910/DVN/EGZHFV

[3] S. Hochreiter and J. Schmidhuber, "Long short-term memory," 
Neural Comput., vol. 9, no. 8, pp. 1735-1780, Nov. 1997.

[4] K. Cho et al., "Learning phrase representations using RNN 
encoder-decoder for statistical machine translation," 
in Proc. EMNLP, Doha, Qatar, 2014.

