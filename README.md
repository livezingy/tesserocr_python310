
# what is tesserocr
[tesserocr](https://github.com/sirfz/tesserocr) integrates directly with Tesseract's C++ API using Cython which allows for a simple Pythonic and easy-to-read source code. It enables real concurrent execution when used with Python's threading module by releasing the GIL while processing an image in tesseract.

tesserocr is designed to be Pillow-friendly but can also be used with image files instead.

# what is tesserocr_python310
One of the way to install tesserocr on Windows, is to Download the wheel file corresponding to your Windows platform and Python installation from [tesserocr-windows_build](https://github.com/simonflueckiger/tesserocr-windows_build/releases). 

If you need Windows tessocr package and your Python version is not supported by above mentioned project, you can try to follow step by step instructions for Windows 64bit in [Windows.build.md.](https://github.com/sirfz/tesserocr/blob/master/Windows.build.md)

tesserocr_python310 is compiled with python3.10 + tesseract5.0.1 + windows10 x64 refer to [Windows.build.md.](https://github.com/sirfz/tesserocr/blob/master/Windows.build.md)

# how to use tesserocr_python310
1. Download the tesserocr_python310.

2. Download .traineddata files which can be found at https://github.com/tesseract-ocr/tessdata and Setting the path of the .traineddata files as the value of TESSDATA_PREFIX environment variable. 
 
3. Come to the path of the tesserocr-2.5.2-cp310-cp310-win_amd64.whl on the command line and install the tesserocr via
```
pip install tesserocr-2.5.2-cp310-cp310-win_amd64.whl
```

4. Copy leptonica-1.83.0.dll/libpng16.dll/tesseract50.dll/zlib.dll to where the tesserocr.cp310-win_amd64.pyd is after the step3. My path of tesserocr.cp310-win_amd64.pyd is PATH\TO\python\Lib\site-packages on My Pc.

## Check
```
import tesserocr
from tesserocr import PyTessBaseAPI
from PIL import Image

with PyTessBaseAPI() as api:
    print(tesserocr.tesseract_version())  # print tesseract-ocr version
    print(tesserocr.get_languages())  # prints tessdata path and list of available languages
    api.SetImageFile('PATH/TO/TEST/IMAGE/testtessrocr.png')
    print(api.GetUTF8Text())
```
output of the above code:
```
tesseract 5.0.1
 leptonica-1.83.0 (Feb 11 2022, 22:34:51) [MSC v.1929 LIB Release x64]
  libpng 1.6.37 : zlib 1.2.11
('d:\\Program Files\\Tesseract-OCR\\tessdata/', ['chi_sim', 'chi_sim_vert', 'eng', 'equ', 'osd'])
git clone https://github.com/sirfz/tesserocr.git
cd tesserocr
```
