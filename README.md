
# Transformer-Based Object Detection

This project implements an **object detection system** powered by state-of-the-art **transformer models**, including **DETR** (DEtection TRansformer) and **YOLOS** (You Only Look One-level Series). The system supports object detection from both uploaded images and image URLs. It comes with a user-friendly **Gradio web interface** and a **FastAPI API** for automated processing.

Try the demo on Hugging Face: \[**Demo Link**].

## Supported Models

Here’s a list of the available models for different detection and segmentation tasks:

### **DETR (DEtection TRansformer)**:

* **facebook/detr-resnet-50**: Fast and efficient object detection.
* **facebook/detr-resnet-101**: More accurate, but slower than ResNet-50.
* **facebook/detr-resnet-50-panoptic** *(currently has bugs)*: For panoptic segmentation. Detects and segments scenes.
* **facebook/detr-resnet-101-panoptic** *(currently has bugs)*: High-accuracy segmentation for complex scenes.

### **YOLOS (You Only Look One-level Series)**:

* **hustvl/yolos-tiny**: Lightweight and quick. Ideal for environments with limited resources.
* **hustvl/yolos-base**: Strikes a balance between speed and accuracy.

## Key Features

* **Image Upload**: Upload an image from your device to run detection via the Gradio interface.
* **URL Input**: Input an image URL for detection through Gradio or the FastAPI.
* **Model Selection**: Choose between DETR and YOLOS models for object detection or segmentation.
* **Object Detection**: Detects objects and shows bounding boxes with confidence scores.
* **Panoptic Segmentation**: Available with certain models for detailed scene segmentation using colored masks.
* **Image Info**: Displays metadata such as size, format, aspect ratio, and file size.
* **API Access**: Use the FastAPI `/detect` endpoint for programmatic processing.

## How to Get Started

### 1. **Cloning the Repository**

#### Prerequisites:

* Python 3.8 or higher
* `pip` to install dependencies

#### Clone and Set Up:

```bash
git clone https://github.com/NeerajCodz/ObjectDetection.git
cd ObjectDetection
pip install -r requirements.txt
```

#### Run the Application:

* **FastAPI**: Start the server with:

```bash
uvicorn objectdetection:app --reload
```

* **Gradio Interface**: Launch with:

```bash
python app.py
```

#### Access the Application:

* **FastAPI**: Navigate to `http://localhost:8000` to interact with the API or view the Swagger UI.
* **Gradio**: The Gradio interface will be available at `http://127.0.0.1:7860` (URL will show up in the console).

### 2. **Running via Docker**

#### Prerequisites:

* Install Docker on your machine (if you haven’t already).

#### Set Up with Docker:

1. Clone the repository (if you haven’t):

```bash
git clone https://github.com/NeerajCodz/ObjectDetection.git
cd ObjectDetection
```

2. Build the Docker image:

```bash
docker build -t objectdetection:latest .
```

3. Run the container:

```bash
docker run -p 5000:5000 objectdetection:latest
```

Access the app at `http://localhost:5000`.

### 3. **Try the Online Demo**

Test the demo directly on Hugging Face’s Spaces:
[**Object Detection Demo**](https://huggingface.co/spaces/NeerajCodz/ObjectDetection)

## API Usage

Use the `/detect` endpoint in FastAPI for image processing.

### **POST** `/detect`

Parameters:

* **file** *(optional)*: Image file (must be of type image/\*).
* **image\_url** *(optional)*: URL of the image.
* **model\_name** *(optional)*: Choose the model (e.g., `facebook/detr-resnet-50`, `hustvl/yolos-tiny`, etc.).

Example Request Body:

```json
{
  "image_url": "https://example.com/image.jpg",
  "model_name": "facebook/detr-resnet-50"
}
```

Example Response:

```json
{
  "image_url": "data:image/png;base64,...",
  "detected_objects": ["person", "car"],
  "confidence_scores": [0.95, 0.87],
  "unique_objects": ["person", "car"],
  "unique_confidence_scores": [0.95, 0.87]
}
```

## Development & Contributions

To contribute or modify the project:

1. Clone the repository:

```bash
git clone https://github.com/NeerajCodz/ObjectDetection.git
cd ObjectDetection
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Run FastAPI or Gradio:

* **FastAPI**: `uvicorn objectdetection:app --reload`
* **Gradio**: `python app.py`

Access the app on `http://localhost:8000` (FastAPI) or the Gradio interface at the displayed URL.

## Contributing

Contributions are always welcome! Feel free to submit pull requests or open issues for bug fixes, new features, or improvements.


