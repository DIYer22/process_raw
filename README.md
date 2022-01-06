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
**Python example:**
```Python
import cv2
from process_raw import DngFile

# Download raw.dng for test:
# wget https://github.com/yl-data/yl-data.github.io/raw/master/2201.process_raw/raw-12bit-GBRG.dng
dng_path = "./raw-12bit-GBRG.dng"

dng = DngFile.read(dng_path)
rgb1 = dng.postprocess()  # demosaicing by rawpy
cv2.imwrite("rgb1.jpg", rgb1[:, :, ::-1])
rgb2 = dng.demosaicing(poww=0.3)  # demosaicing with gamma correction
cv2.imwrite("rgb2.jpg", rgb2[:, :, ::-1])
DngFile.save(dng_path + "-save.dng", dng.raw, bit=dng.bit, pattern=dng.pattern)
```

**Run demo:**
```bash
python -m process_raw.process_raw
```
For document, please see example code of `DngFile.test()` at [`process_raw/process_raw.py`](process_raw/process_raw.py#L154)

## Credits
Source referenced from:
- [rawpy](https://github.com/letmaik/rawpy): for read `.dng` file
- [PiDNG](https://github.com/schoolpost/PiDNG): for save raw as `.dng` file
- [colour_demosaicing](https://github.com/colour-science/colour-demosaicing): Provide demosaicing algorithms
