---
layout: post
title: "OCR for English and Chinese"
categories:
- Programming
- Research

Tags:
- data
- OCR
- tesseract
---

### Version

 `tesseract-3.04.01_2` and `imagemagick-6.9.5-2`

**tesseract project** in [github](https://github.com/tesseract-ocr/tesseract)

Install ImageMagick for image conversion:

```
brew install imagemagick
```
Install tesseract for OCR:   

```
brew install tesseract --with-all-languages
```

Or install without `--all-languages` and install them manually as needed.

Make sure the input image is a grayscale `.tif` and fairly large. ~500x150 was too small, while ~2000*500 worked very well.

```
convert input.png -resize 400% -type Grayscale input.tif
```

OCR it. The default language is English. Language codes are 3 chars per man tesseract.

```
tesseract -l eng input.tif output
```
This creates output.txt.


### 识别简体中文

download file `chi_sim.traineddata` and `chi_tra.traineddata` from [tessdata](https://github.com/tesseract-ocr/tessdata) and put them into `/usr/local/share/tessdata/`

```
convert inputfile.jpg -type Grayscale inputfile.tif
export TESSDATA_PREFIX=/usr/local/share/
tesseract inputfile.tif output -l chi_sim
```

### clean image use python

```py
from PIL import Image
import subprocess

def cleanFile(filePath, newFilePath):
    image = Image.open(filePath)

    #Set a threshold value for the image, and save
    image = image.point(lambda x: 0 if x<143 else 255)
    image.save(newFilePath)

    #call tesseract to do OCR on the newly created image
    subprocess.call(["tesseract", newFilePath, "output"])
    
    #Open and read the resulting data file
    outputFile = open("output.txt", 'r')
    print(outputFile.read())
    outputFile.close()

cleanFile("page.jpg", "page_clean.png")
```