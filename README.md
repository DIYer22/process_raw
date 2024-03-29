# `process_raw`: A python package to process raw and dng file

## Features
- [x] Reading `.dng` file to `np.array`
- [x] Saving raw image as `.dng` file
- [x] Demosaicing (by rawpy)
- [x] Demosaicing with [gamma correction](https://en.wikipedia.org/wiki/Gamma_correction) (for raw image > 8bit)

## Usage 
**Install**
```bash
pip install process_raw 
```

**Run demo:**
```bash
python -m process_raw.process_raw
```
Then, the browser will automatically open a visual web page, like [demo.html](https://yl-data.github.io/2201.process_raw/raw_simple_Malvar2004_pow0.3/)

For document, please see example code of `DngFile.test()` at [`process_raw/process_raw.py`](process_raw/process_raw.py#L186)

**Python example:**
```Python
import cv2
import numpy as np
from process_raw import DngFile

# Download raw.dng for test:
# wget https://github.com/yl-data/yl-data.github.io/raw/master/2201.process_raw/raw-12bit-GBRG.dng
dng_path = "./raw-12bit-GBRG.dng"

dng = DngFile.read(dng_path)
raw = dng.raw  # np.uint16
raw_8bit = np.uint8(raw >> (dng.bit-8))
cv2.imwrite("raw_8bit.png", raw_8bit)

rgb1 = dng.postprocess()  # demosaicing by rawpy
cv2.imwrite("rgb1.jpg", rgb1[:, :, ::-1])
rgb2 = dng.demosaicing(poww=0.3)  # demosaicing with gamma correction
cv2.imwrite("rgb2.jpg", rgb2[:, :, ::-1])
DngFile.save(dng_path + "-save.dng", dng.raw, bit=dng.bit, pattern=dng.pattern)
```
## Credits
Source referenced from:
- [rawpy](https://github.com/letmaik/rawpy): For read `.dng` file
- [PiDNG](https://github.com/schoolpost/PiDNG): For save raw as `.dng` file
- [colour_demosaicing](https://github.com/colour-science/colour-demosaicing): Provide demosaicing algorithms
