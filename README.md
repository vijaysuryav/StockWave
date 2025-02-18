# Stockwave Project

This repository contains three Jupyter Notebooks that you can run within 15 minutes. Follow the steps below to set up and run the code.

## Setup Instructions

1. **Upload the unzipped folder** to the CHPC server containing a Spark Jupyter session.
2. **Install the required libraries** by running the following commands in a Jupyter cell:

    ```python
    !pip install tensorflow
    !pip install keras
    !pip install matplotlib
    !pip install ipywidgets
    ```

    Use `pip install` whenever necessary to install missing dependencies.

## Folder Structure

- **data**: Contains all the `.csv` files of the stocks.
- **data_torun**: Contains 10 `.csv` files, used for running the code. Training on all stocks takes a lot of time.
- **data_test_torun**: Gets populated when you run the `download_test_data` Jupyter notebook.
- **means_torun** and **stds_torun**: These folders get populated with `means_dict_torun.json` and `stds_dict_torun.json` when you run the `Stockwave_torun` Jupyter notebook.
- **modelstorun_**: Contains approximately 50 stock-related LSTM models.
- **models_onlinetrained**: Gets populated when you click the retrain button in the GUI, which pops up when you run the `stockwave_vis_torun` Jupyter notebook.

## Running the Jupyter Notebooks

### 1. Running `Stockwave_torun` Jupyter Notebook

Before running, ensure the following:

- You have all the above folders in place.
- The `data_torun` folder has 10 stock `.csv` files.
- The `means_torun` and `stds_torun` folders exist.
- The `modelstorun_` folder exists to save the ten models trained by running this notebook.

Then, run the entire code (it will take approximately 10 minutes to train).

Once the training is done, verify the following:

- The `means_torun/means_dict_torun.json` file should be populated with means for the 10 stocks present in the `data_torun` folder.
- The `stds_torun/stds_dict_torun.json` file should be populated similarly.

### 2. Running `download_test_data` Jupyter Notebook

This notebook is used to download the latest data from the Yahoo Finance website.

Before running, ensure that:

- You have the `data_test_torun` folder, where all the stock `.csv` files will be stored.
- The stocks in the list of tickers in the first cell will be downloaded.

### 3. Running `stockwave_vis_torun` Jupyter Notebook

This notebook handles the visualization and testing of the data.

Before running, ensure that:

- You have all the required folders mentioned above.
- `means_dict_torun.json` and `stds_dict_torun.json` are available.
- The `data_torun` folder contains all 10 `.csv` files.
- The `modelstorun_` folder contains all the 10 `{stock_name}_model.keras` files.

Next, run all the cells until you reach the markdown with the GUI. Run the next cell, and a GUI will pop up.

### GUI Instructions

- **Enter Dates**: Select dates available in the `data_test_torun` folder.
- **Select Stock**: Choose the stock from the dropdown.
- **Buttons**: You will see three buttons:
  - **Visualize**: A graph will pop up showing the predicted and actual values for that particular date.
  - **Clear Graph**: Clears the graph but keeps the buttons active.
  - **Retrain**: Retrains the model on new data. You will need to click the "Visualize" button again to plot the graph after retraining.

---

Follow these steps to run the notebooks and visualize the stock data. If you encounter any issues, feel free to check the folder contents and ensure that all required files are present before running the notebooks.
