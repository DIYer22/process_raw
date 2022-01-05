# process_raw: A python package to process raw and dng file

## Feature
- [x] Reading dng file
- [x] Saving dng file
- [x] Demosaicing
- [x] Demosaicing with pow (for raw image > 8bit)

## Usage 
```bash
# Install
pip install process_raw 

# Run example
python3 -m process_raw.process_raw
```
For document, please see example code of `DngFileformat.test()` at [`process_raw/process_raw.py`](process_raw/process_raw.py#L154)

## Credits
Source referenced from:
- [PiDNG](https://github.com/schoolpost/PiDNG): for save dng file
- [rawpy](https://github.com/letmaik/rawpy): for read dng file
- [colour_demosaicing](https://github.com/colour-science/colour-demosaicing): Provide demosaicing algorithms
