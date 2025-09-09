# Network Security - Phishing Detection Pipeline

## Overview

This project is a complete machine learning pipeline for detecting phishing in network data. It includes data ingestion, validation, transformation, model training, prediction, and deployment using FastAPI. The solution is containerized with Docker and supports cloud integration (AWS S3, MongoDB).

## Features

- **Data Ingestion:** Loads network data from CSV, supports MongoDB integration.
- **Data Validation:** Checks schema, column count, and detects dataset drift.
- **Data Transformation:** Cleans and preprocesses data, handles missing values, and prepares features.
- **Model Training:** Trains multiple classifiers (Random Forest, Decision Tree, Gradient Boosting, Logistic Regression, AdaBoost) and selects the best model.
- **Prediction API:** FastAPI endpoint for batch prediction via CSV upload, returns results as HTML table.
- **Deployment:** Dockerized for easy deployment; supports CI/CD with GitHub Actions and AWS ECR.
- **Artifacts:** Stores trained models and preprocessors for reproducibility.

## Project Structure

```
app.py                # FastAPI app entry point
main.py               # (Optional) Main script
push_data.py          # Utility to push CSV data to MongoDB
requirements.txt      # Python dependencies
Dockerfile            # Containerization instructions
data_schema/schema.yaml  # Data schema definition
final_model/          # Saved model and preprocessor
Network_Data/         # Raw network data (CSV)
networksecurity/      # Core package (components, utils, pipeline, etc.)
templates/table.html  # HTML template for prediction output
prediction_output/    # Stores prediction results
valid_data/           # Validated test data
```

## Installation

1. **Clone the repository:**
	 ```bash
	 git clone https://github.com/Devb1234/Network_Security.git
	 cd Network_Security
	 ```

2. **Install dependencies:**
	 ```bash
	 pip install -r requirements.txt
	 ```

3. **Set up environment variables:**
	 - Create a `.env` file with your MongoDB and AWS credentials.

## Usage

### Local Development

- **Start the API server:**
	```bash
	python app.py
	```
	The API will be available at `http://localhost:8080`.

- **Train the model:**
	- Send a GET request to `/train` endpoint or run the training pipeline via code.

- **Make predictions:**
	- Use the `/predict` endpoint to upload a CSV file and receive predictions.

### Docker

- **Build and run the container:**
	```bash
	docker build -t networksecurity .
	docker run -p 8080:8080 networksecurity
	```

### Data Push

- **Push data to MongoDB:**
	```bash
	python push_data.py
	```

## API Endpoints

- `GET /` - Redirects to API docs.
- `GET /train` - Triggers model training pipeline.
- `POST /predict` - Upload CSV for batch prediction.

## Cloud & CI/CD

- Integrated with AWS (ECR, S3) and MongoDB.
- GitHub Actions workflow for CI/CD and deployment.

## Contributing

Feel free to open issues or submit pull requests for improvements.

## License

MIT License
