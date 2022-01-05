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

# Example
python3 -m process_raw.process_raw
```
For document, please see `DngFileformat.test()` at [`process_raw/process_raw.py`](process_raw/process_raw.py#L154)

## Credits
Source referenced from:
- [PiDNG](https://github.com/schoolpost/PiDNG): for save dng file
- [rawpy](https://github.com/letmaik/rawpy): for read dng file
