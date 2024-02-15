# Resumé Parser

## Overview

   Welcome to the Resumé Parser Demo App! This web-based application demonstrates the basic functionality of spacy NER and customized parsing pipeline, allowing users to extract different entities of words and add custom rules to extract specific or expected entities.

## Dataset

   The language model is from spacy. The *en_core_web_trf* is noteably a stronger model but it comes with a much larger file. To keep the app light and fast, I use *en_core_web_md* for this demo app instead. The [resume dataset from kaggle](https://www.kaggle.com/datasets/snehaanbhawal/resume-dataset) is used to demonstrate the capability of spacy parser and make a skill parser, and a [sample dataset](https://ait.ac.th/wp-content/uploads/2021/12/chaky_resume.pdf) is parsed extensively to demonstrate how custom parser works.

   There are 4 custom parsers for certificates, education degrees, phone number, and email. Json of [degrees](https://gist.github.com/cblanquera/21c925d1312e9a4de3c269be134f3a6c#file-degrees-json) and [certs](https://gist.github.com/cblanquera/21c925d1312e9a4de3c269be134f3a6c#file-certs-json) are converted into JsonList in [converter.ipynb](https://github.com/thassung/Resume_Parser/blob/main/converter.ipynb) and used to extract pattern (hard-code) of each degree and certificate names for the custom parser. The other two parsers—phone number and email—use regex pattern to detect those information.

## Features

   - **Resumé Content:** User can type resume or paste a resume content in this text box to extract entities.
   - **Upload Button:** User can click this button to browse local resume pdf file and upload it to the applcation. *NOTE that only pdf file format is supported*
   - **Parse Button:** User clicks *parse* after typing in resume content or upload the resume file. The app will parse the input **prioritizing** uploaded file. If a file is uploaded, the text in *Resumé Content* will be replaced with text from pdf file to prevent confusion if the uploaded file or the text is parsed.
   - **Download Parsed Data Button:** User can download the parsed data in json format.
   - **Extracted Information:** User can see the parsed data on the right side. There are 5 categories shown included:
     - **Skills:** Skills included in the resume.
     - **Educations:** Education degrees included in the resume.
     - **Certificates:** Certificates included in the resume.
     - **Work Experiences:** Associated organization/institutes included in the resume. *en_core_web_md* is not the best for detecting organization named entity (*en_core_web_trf* does a much better job). To filter some out, the *filtered* checkbox will filtered some parsed entitities out with simple rules (length, keyword, and letter case) 
     - **Contact:** Phone number and email included in the resume. In case of multiple phone number and/or email, the first one is shown assuming a resume usually include the individual's contact information before referee's.

## Application

### Prerequisites

- Ensure you have Python installed

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/thassung/TrydoDict.git
   ```

2. Install the required Python dependencies:

   ```bash
   pip install flask PyPDF2 spacy
   ```

3. Navigate to the app directoty:
   ```bash
   cd Resume_Parser/app
   ```

4. Start the flask application:
   ```bash
   python main.py
   ```

   You can access the application via http://localhost:8080

   Below is how the app should look like.

   ![image](https://github.com/thassung/Resume_Parser/assets/105700459/c8abda73-175b-4a6d-90f7-81c29dbfb588)
