# <h1><b>Introduction</b></h1>

## <b>Overview</b>
---
<p> PharmaPy is a python package that provides functionality for several useful utilities for drug information tasks. It requires Python version 3.10 and can be installed from the command line with the following command.

```
pip install PharmaPy
```
</p>



A direct link to the package can be found [here](https://pypi.org/project/PharmaPy/)


## <b>Modules at a glance</b>
---
### <b>FDA Helper</b>

This module interfaces with the openfda API and can return information about a specific drug when provided with a name and route. It can also retrieve a singular field from the drug information. 

### <b>NADAC</b>

This module performs several common tasks to get drug pricing based on the NADAC dataset. Useful when you have a list of NDCs or drug name and what to get how much they cost.


### <b>Named-Entity Recognition (NER)</b>

This extracts drug names from any text sample. Useful when you have medical notes, questions, or PDFs and you want to extract the drug name for further analysis. The model is very small wiht ~95% accuracy and can run locally or any modern CPU server. No complicated machine learning deployment needed.


### <b> RXNorm </b>

This module simplifies interactions with the RXNorm API. Useful to get supplemental drug information that may not be in the FDA label database.