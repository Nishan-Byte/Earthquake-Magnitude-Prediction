# Data

This directory contains the datasets and data-related files used in the **Earthquake Magnitude Prediction** project.

## Dataset Overview

The project uses earthquake event data containing information such as:

- Geographic coordinates (`latitude`, `longitude`)
- Earthquake depth (`depth`)
- Data quality parameters (`dmin`, `rms`, `gap`)
- Magnitude and magnitude type (`mag`, `magType`)
- Event timestamp (`datetime`)
- Additional temporal, spatial, and historical seismicity features derived during preprocessing

The processed dataset contains **9,775 earthquake events** and **26 columns**.

## Processed Dataset

The final processed dataset contains:

- **23 model features**
- **1 target variable:** `mag`
- **1 split identifier:** `split`
- **1 datetime field:** `datetime`

### Model Features

The 23 features used by the final tuned XGBoost model are:

#### Spatial
- `latitude`
- `longitude`
- `distance_from_center_km`

#### Physical / Data Quality
- `depth`
- `dmin`
- `rms`
- `gap`

#### Temporal
- `year`
- `month_sin`
- `month_cos`
- `day_sin`
- `day_cos`
- `hour_sin`
- `hour_cos`

#### Historical Seismicity
- `past_events_within_100km`
- `recent_local_events_30d`

#### Magnitude Type
- `magType_mb`
- `magType_ml`
- `magType_mw`
- `magType_mwb`
- `magType_mwc`
- `magType_mwr`
- `magType_mww`

## Train / Validation / Test Split

The dataset was divided chronologically to preserve the temporal nature of earthquake data.

| Split | Events |
|---|---:|
| Training | 7,107 |
| Validation | 1,306 |
| Test | 1,362 |
| **Total** | **9,775** |

The final test set contains earthquake magnitudes ranging from **3.4 to 7.7**.

## Data Processing

The preprocessing pipeline includes:

1. Cleaning and preparing the earthquake event records.
2. Processing the event timestamps.
3. Engineering cyclical temporal features using sine/cosine transformations.
4. Creating spatial features such as distance from a reference center.
5. Creating historical seismicity features.
6. Encoding earthquake magnitude types using one-hot encoding.
7. Separating features from the target magnitude.
8. Creating chronological train, validation, and test splits.
9. Applying feature scaling where required by the corresponding model.
10. Passing the resulting feature matrix to the machine-learning pipeline.

## Data Leakage Consideration

The project uses a chronological split rather than a random split so that future earthquake events are not used to train models evaluated on earlier events.

Historical seismicity features were also constructed to represent information available from previous earthquake events.

## Important Note

The raw earthquake data is not included in this repository unless explicitly added by the project author.

If the original dataset is obtained from an external source, users should follow that source's licensing and usage requirements.

The processed data used during model development should be reproducible using the preprocessing code provided in the project repository.
