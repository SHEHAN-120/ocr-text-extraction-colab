# OCR with Python, Tesseract, and OpenCV

This project demonstrates Optical Character Recognition (OCR) using **Tesseract OCR**, **Python**, and **OpenCV**.
It was developed and tested on **Google Colab** with multilingual text recognition support.

---

## 🚀 Features

* Text extraction from images using [Tesseract OCR](https://github.com/tesseract-ocr/tesseract)
* Bounding box visualization for detected text
* Confidence-based filtering of results
* Multilingual OCR (English, Portuguese, Sinhala, etc.)
* Custom font rendering using PIL
* Example usage with natural scene images and scanned documents
* Search for specific patterns (e.g., dates using regex)

---

## 🛠️ Tools & Libraries Used

* **Python 3**
* **Tesseract OCR**
* **Pytesseract** – Python wrapper for Tesseract
* **OpenCV** – image processing
* **NumPy**
* **Matplotlib**
* **PIL (Pillow)**
* **Google Colab** – development environment




---

## 📖 Example Usage

### 1. Install dependencies

```bash
!sudo apt install tesseract-ocr
!pip install pytesseract opencv-python pillow matplotlib
```

### 2. Basic OCR

```python
import pytesseract
import cv2

img = cv2.imread('test01.jpg')
text = pytesseract.image_to_string(img, lang='eng')
print(text)
```

### 3. Bounding Boxes with Confidence Filter

```python
from pytesseract import Output

result = pytesseract.image_to_data(img, output_type=Output.DICT)
for i in range(len(result['text'])):
    if int(result['conf'][i]) > 40:
        print(result['text'][i])
```

---

## 🌍 Multilingual OCR

To enable support for other languages (example: Sinhala, Portuguese):

```bash
!apt-get install tesseract-ocr-sin
!apt-get install tesseract-ocr-por
```

Or manually download `.traineddata`:

```bash
!wget -O ./tessdata/sin.traineddata https://github.com/tesseract-ocr/tessdata/raw/main/sin.traineddata
```

Usage:

```python
text = pytesseract.image_to_string(img, lang='sin', config="--tessdata-dir tessdata")
```

---

## 📌 Functions Implemented

* `bouding_box(result, img, i)` – draw rectangle around detected text
* `write_text(text, x, y, img, font, font_size=32)` – overlay text with custom fonts
* Regex-based text search (example: date patterns)
* Visualization with OpenCV and cv2\_imshow

---

## 📸 Example Outputs

* Bounding boxes drawn around detected words
* Text recognition in multiple languages
* Extracted structured information (dates, tables, etc.)



---

## 📜 License

This project is open-source under the MIT License.
