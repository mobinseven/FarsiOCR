# FarsiOCR
An OCR application for Farsi/ Persian documents.
This OCR application uses open source text recognition [Tesseract 5.1.0](https://github.com/tesseract-ocr/tessdoc) and Python3.

Preprocessing is applied to each image before using `tesseract`. This is done to improve the performance of tesseract and also fix the rotation angle of the image (if needed). After converting the image to a `txt` file, the quality of ocr can be measured using the Levenshtein distance metric (By putting original.docx of the intended image into Data directory). 

## Installation On Windows

1. Install [Python 3.10.11](https://www.python.org/ftp/python/3.10.11/python-3.10.11-amd64.exe)

2. Upgrade pip

``shell
py -m pip install --upgrade pip
```

3. Install [VS Build Tools](https://aka.ms/vs/17/release/vs_BuildTools.exe)

  a. Run installer.
  b. Under "Individual Components" tab search and select these items:
      - Windows 10 SDK
      - build tools (latest)
      - C++ Redistributable Update
  c. Install

4. Install [Tesseract](https://github.com/UB-Mannheim/tesseract/wiki)

  a. Run installer
  b. Under "Choose Components" setup step open "Additional language data" and check "Persian" (the list is not alphabetically ordered. it is near "Finnish")
  c. Intsall
  d. After installation run this command to add the program to `PATH`:
```shell
setx PATH "$($env:path);C:\Program Files\Tesseract-OCR"
```
5. Install farsi language data for tesseract

[Download](https://github.com/tesseract-ocr/tessdata) language training data (fas.traineddata) and move the file to the following directory:
```shell script
mv fas.traineddata /usr/local/share/tessdata
```

6. Install poppler

Open PewerShell and run these commands:

```shell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
scoop install poppler
```

7. Dowwnload this repo using "Code<> --> Download ZIP"
8. Install dependencies via `requirements.txt`
```shell
cd <this repo download location>
py -m pip install -r requirements.txt
```

## How to use?
Copy your pdf or image files into the `data` directory (a sample image in the Data directory is downloaded from the internet). 

Run the `src/ocr.py` and the results will be created in the `output` directory.
