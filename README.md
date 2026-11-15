# Spatiotemporal Deep Learning for Heatwave Prediction over India

## 1. Project Overview

This project focuses on developing a spatiotemporal deep learning approach for heatwave prediction over India using ERA5 reanalysis data.

The project uses historical atmospheric and meteorological variables to identify heatwave conditions and investigate their prediction using a Convolutional Long Short-Term Memory (ConvLSTM) model.

The primary objective is to study how atmospheric conditions change across geographical locations and over time, and how these patterns can help identify potential heatwave events.

## 2. Project Objectives

- Collect historical ERA5 reanalysis data for the Indian geographical region.
- Integrate historical and additional recent climate data.
- Generate daily atmospheric variables from six-hourly observations.
- Perform data preprocessing and heatwave event identification.
- Develop a spatiotemporal ConvLSTM model.
- Evaluate the model's ability to predict heatwave events.
- Analyse spatial and temporal patterns associated with heatwaves.

## 3. Dataset Description

The project uses ERA5 reanalysis data obtained from the following sources:

1. **WeatherBench 2:** Used to obtain historical ERA5 data.
2. **Copernicus Climate Data Store (CDS):** Used to retrieve additional ERA5 data through its API.

### Dataset Specifications

| Parameter | Description |
|---|---|
| Geographic region | India |
| Data period | 1990–2026 |
| Spatial resolution | 1.5° × 1.5° |
| Grid dimensions | 21 × 20 |
| Data frequency | Daily |
| Number of variables | 8 |
| File format | NetCDF (.nc) |
| Final dataset size | Approximately 168 MB |

**Data coverage note:** The dataset spans 1990–2026, but the additional recent-year data cover selected periods rather than every day of every year.

### Atmospheric Variables

The final dataset contains the following eight variables:

| Variable | Description |
|---|---|
| `tmax` | Daily maximum 2 m temperature |
| `tmean` | Daily mean 2 m temperature |
| `u10` | Daily mean eastward wind component at 10 m |
| `v10` | Daily mean northward wind component at 10 m |
| `msl` | Mean sea-level pressure |
| `z500` | Geopotential at 500 hPa |
| `q850` | Specific humidity at 850 hPa |
| `t850` | Temperature at 850 hPa |

## 4. Data Processing Workflow

The data preparation workflow consists of the following stages:

1. **Historical Data Extraction:** Historical ERA5 data are obtained from WeatherBench 2 for the selected geographical region.
2. **Recent Data Retrieval:** Additional ERA5 data are requested through the Copernicus Climate Data Store API.
3. **Daily Aggregation:** Six-hourly observations are converted into daily atmospheric variables.
4. **Coordinate Alignment:** Spatial coordinates are aligned to maintain a consistent geographical grid.
5. **Dataset Merging:** Historical and additional datasets are combined chronologically.
6. **Data Validation:** The merged dataset is checked for duplicate dates, missing values, time coverage and spatial dimensions.
7. **Final Dataset Generation:** The processed data are stored in NetCDF format for subsequent model development.

## 5. Repository Structure

```text
heatwave-prediction-india/
│
├── README.md
│
├── ML_Project_Complete_dataset_code.ipynb
│
├── models/
│
├── outputs/
│
├── report/
│
├── requirements.txt
│
└── .gitignore
```

The repository will be updated as the project progresses. Model preprocessing, training, evaluation and result visualisation files will be added in subsequent stages.

## 6. Technologies and Libraries

The project uses the following technologies and Python libraries:

- Python
- Google Colab
- Xarray
- NumPy
- Pandas
- Dask
- Zarr
- NetCDF
- WeatherBench 2
- Copernicus Climate Data Store API
- PyTorch
- Scikit-learn
- Matplotlib

## 7. Installation and Dependencies

Clone the repository:

```bash
git clone https://github.com/vanshikapatil709/Heatwave-Prediction-India.git
```

Navigate to the project directory:

```bash
cd Heatwave-Prediction-India
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

The data extraction notebook is designed to run in Google Colab. Open the notebook using Google Colab and mount Google Drive when prompted.

## 8. Dataset Access

The final merged dataset is approximately 168 MB and is stored separately in Google Drive. It is not included directly in this GitHub repository because of GitHub's standard file-size restrictions.

Final dataset filename:

`india_daily_full.nc`

The dataset can be accessed through the project owner's shared Google Drive location, subject to access permissions.

To reproduce the data preparation process, the required historical and recent ERA5 source files must be available in the configured Google Drive directory.

For recent ERA5 retrieval, users need their own Copernicus Climate Data Store account and API credentials.

**Note:** API credentials must be configured privately and must never be committed to this public repository.

## 9. Execution Instructions

### Step 1: Open the notebook

Open:

`notebooks/ML_Project_Complete_dataset_code.ipynb`

in Google Colab.

### Step 2: Configure Google Drive

Mount Google Drive and update the dataset folder path according to your own Drive directory.

### Step 3: Configure CDS API access

For data retrieval, configure your own Copernicus Climate Data Store API credentials.

### Step 4: Execute the relevant sections

Follow the notebook's documented sections for historical data extraction, recent data retrieval, dataset merging and validation.

The extraction and retrieval sections may submit new data requests and consume considerable time. Do not execute the entire notebook indiscriminately if the required datasets have already been downloaded.

### Step 5: Verify the merged dataset

The final output is:

`india_daily_full.nc`

Use the final validation section to inspect its dimensions, variables, time coverage, missing values and duplicate dates.

## 10. Data Sources and References

- WeatherBench 2: https://weatherbench2.readthedocs.io/
- WeatherBench 2 Dataset: https://console.cloud.google.com/storage/browser/weatherbench2
- Copernicus Climate Data Store: https://cds.climate.copernicus.eu/
- ERA5 Single-Level Reanalysis: https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels
- ERA5 Documentation: https://confluence.ecmwf.int/pages/viewpage.action?pageId=462906181

## 11. Disclaimer

ERA5 is a reanalysis dataset that combines observations with numerical weather modelling. It is not equivalent to direct observations at every geographical grid point.

The project is intended for academic research and experimentation. Its model outputs should not be treated as operational heatwave warnings or a replacement for official meteorological forecasts.
