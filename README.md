
# Flask API


- End point URL: 
```
/processAadhar
```
- Allowed file types: 'png', 'jpg', 'jpeg'
- Imports and runs OCR_Dictionary



# Aadhar Data Extraction
Contains 4 modules
- OCR.py
- PreProcessor.py
- AadharExtractor.py
- OCR_Dictionary.py     

### OCR.py
- Uses EasyOCR for recognizing text
- Takes the path of the images as the parameter and converts all the text from the image to a list of lines
- Returns the list of lines
- All EasyOCR parameters are set in this file

### PreProcessor.py
- Has it's own implementation of EasyOCR with a different set of parameters for better pre-processing
- Identifies and removes non-english character. The bounding box is replaced by white pixels

### AadharExtractor.py
- Contains the set of regular expression rules for extraction of required data from the list of lines received from the OCR module

### OCR_Dictionary.py
- Imports and runs all the above modules
- Takes the image path and the dump path as parameters
- The dump path is used by the PreProcessor module to temporarily store the pre-processed image 

# Running in Local Environment
- Clone this repository using 
```
git clone https://github.com/aditya-gitte/Aadhar-flask-API.git
```
- cd into the directory, create a virtual env(optional) and install the requirements by running
```
pip install -r requirements.txt
``` 
- Start the development server by running
```
flask run
```
- Send a POST request to "/processAadhar"  on the development server (you can check the development server URL in the terminal) with payload as a key value pair. The key should be 'img' and the image file should be the value
```
localhost/processAadhar
```
- Allowed file types: 'png', 'jpg', 'jpeg'  

# Credits
[@atharvanagmoti20](https://github.com/atharvanagmoti20) for optimizing EasyOCR parameters and helping in the workflow design

