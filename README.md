# Image Dataset Splitter

This Python script automates the process of splitting an image dataset into training and testing sets and organizing them into separate folders.

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This script is particularly useful for machine learning projects where a dataset of images needs to be divided for training and evaluation purposes. It simplifies the process by automatically splitting the dataset into two parts based on a specified ratio and organizing the images into separate folders for training and testing.

## Getting Started

To use this script, follow the instructions below.

### Prerequisites

- Python (version 3.6 or higher)
- Google Colab (if running the provided code in a Colab environment)

### Installation

1. Clone or download this repository to your local machine.
2. Ensure you have Python installed.
3. If you're using Google Colab, upload the provided code to your Colab environment.

## Usage

1. **Prepare Your Dataset:** Ensure your dataset is stored in a folder on Google Drive.

2. **Update Paths:** Update the `data_path`, `train_path`, and `test_path` variables in the provided code to match your folder structure.

3. **Run the Script:** Execute the script to split the dataset into training and testing sets and organize them into separate folders. 

    ```python
    # Mount Google Drive
    from google.colab import drive
    drive.mount('/content/drive')

    # Import necessary libraries
    import os
    import shutil
    from sklearn.model_selection import train_test_split

    # Define paths for data manipulation
    data_path = '/content/drive/My Drive/example_dataset/input_data'
    train_path = '/content/drive/My Drive/example_dataset/train_data'
    test_path = '/content/drive/My Drive/example_dataset/test_data'

    # Ensure the existence of required folders, if not, create them
    if not os.path.exists(train_path):
        os.makedirs(train_path)
    if not os.path.exists(test_path):
        os.makedirs(test_path)

    # Load image data
    image_names = os.listdir(data_path)

    # Split the data into train and test sets
    train_names, test_names = train_test_split(image_names, test_size=0.2, random_state=42)

    # Move the training data
    for image_name in train_names:
        shutil.move(os.path.join(data_path, image_name), os.path.join(train_path, image_name))

    # Move the test data
    for image_name in test_names:
        shutil.move(os.path.join(data_path, image_name), os.path.join(test_path, image_name))
    ```

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these guidelines:

1. Fork the repository on GitHub.
2. Make your changes and commit them to your fork.
3. Submit a pull request with a detailed explanation of your changes.

If you encounter any bugs or have suggestions for improvements, please open an issue on GitHub.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
