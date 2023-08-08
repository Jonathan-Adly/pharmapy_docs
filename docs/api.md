---
hide:
  - toc
---


## <strong>fda_helper</strong>


<ul>
<li> The <strong>drug_information(name, route)</strong> function accepts a drug name and a route, and returns a dictionary with general information about the drug from the FDA API. This includes several fields of information including dosage, warnings, and adverse reactions. </li>
    ``` py
    from PharmaPy import fda_helper

    drug = "ciprofloxacin" 

    route = "oral"

    result = fda_helper.drug_information(drug, route)

    print(result) # 

    ```

<br>
<li> The <strong>drug_field(name, route, field)</strong> function returns the value of just a specific field of the comprehensive drug information. For example, in the example below, just the <i>spl_product_data_elements</i> field is returned. </li>

    ``` py
    from PharmaPy import fda_helper

    drug = "ciprofloxacin" 

    route = "oral"

    field = "spl_product_data_elements"

    result = fda_helper.drug_field(drug, route, field)

    print(result) # "Ciprofloxacin Ciprofloxacin CIPROFLOXACIN..."
    ```

</ul>
---

## <strong>nadac</strong>


<ul>
<li> The <strong>get_from_ndc_list(ndc_list)</strong> function accepts a list of ndcs and returns the latest NADAC per unit for each ndc </li>
    ``` py
    from PharmaPy import nadac

    ndc_list = ['24385005452','46122062978']

    result = nadac.get_from_ndc_list(ndc_list)

    print(results) # [{'ndc_description': '8HR ARTHRITIS PAIN ER 650 MG', 'ndc': '46122062978', 'nadac_per_unit': '0.06987', 'pricing_unit': 'EA', 'as_of_date': '2022-12-28'}, {'ndc_description': '12HR NASAL DECONGEST ER 120 MG', 'ndc': '24385005452', 'nadac_per_unit': '0.28255', 'pricing_unit': 'EA', 'as_of_date': '2022-12-28'}]


    ```

<br>
<li> The <strong>get_avg_from_ndc_description(drug_name, exact_match=False, start_with=False)</strong> function takes a drug name and returns the average NADAC per unit for that drug
    across all ndcs that match the drug name on the latest nadac files.
    default matching behavior is "contain", but you can also match on starts_with (by setting starts_with to True) or exact (by setting exact_match to True). </li>

    ``` py
    from PharmaPy import nadac

    drug = "ciprofloxacin" 

    result = nadac.get_avg_from_ndc_description(drug, exact_match=False, starts_with=False)

    print(result)
    ```

</ul>

---
## <strong>ner</strong>

<ul>
<li> The <strong>predict(text)</strong> function accepts a text sample and outputs an array containing all the drugs found in the sample.</li>
    ``` py
    from PharmaPy import ner

    text = "After surgery, David was given oxycodone for pain, prednisone to reduce inflammation, and benazepril for blood pressure control."

    result = ner.predict(text)

    print(result) #['oxycodone', 'prednisone', 'benazepril']

    ```

</ul> 

---

## <strong>rxnorm</strong>


<ul>
<li> The <strong>get_all_formulations(drug_name)</strong> function accepts a drug name and outputs an array of all formulations of the drug.</li>
    ``` py
    from PharmaPy import rxnorm

    drug = "ciprofloxacin"

    result = rxnorm.get_all_formulations(drug)

    print(result) # ['atorvastatin 10 MG / ezetimibe 10 MG Oral Tablet [Lypqozet]', 'atorvastatin 20 MG / ezetimibe 10 MG Oral Tablet [Lypqozet]', ...]

    ```
</li>
<br>
<li> The <strong>get_all_matching_drug(partial_drug=None)</strong> function outputs a list of all drugs in the RxNorm API. If <i>partial_drug</i> is provided, it filters the list to only names that contain the given partial name.</li>
    ``` py
    from PharmaPy import rxnorm

    result = rxnorm.get_all_matching_drug()

    print(result)

    ```
</li>
<br>
<li> The <strong>get_rxcui_by_ndc(drug_ndc)</strong> function takes any NDC-10 code (with or without hyphens) or NDC-11 code (with hyphens only) and returns the RxCUI numbers that can be used for other RxNorm functions. Some RxCUIs may return multiple RxCUI codes. </li>
    
    ``` py
    from PharmaPy import rxnorm

    ndc_code = "0777310502"

    result = rxnorm.get_rxcui_by_ndc(ndc_code)

    print(result)

    ```
</li>
<br>
<li> The <strong>get_rxcui_by_drug(drug)</strong> function takes a drug (input format as drug name, dose, dosage form; ex. lisinopril 20mg tablet or lisinopril
    20 mg tablet) And returns a list of RxCUIs that can be used for other functions.</li>
    
    ``` py
    from PharmaPy import rxnorm

    drug = "cipro"

    result = rxnorm.get_rxcui_by_drug(drug)

    print(result)

    ```
</li>
<br>
<li> The <strong>get_rxnorm_name(rxcui)</strong> function takes the RxCUI and returns a drug name and dosage. </li>
    
    ``` py
    from PharmaPy import rxnorm

    rxcui = "198013"

    result = rxnorm.get_rxnorm_name(rxcui)

    print(result)

    ```
</li>
<br>
<li> The <strong>get_drug_class_by_name(drug_name, exact_match=False)</strong> function returns the class of a drug given its name. </li>
    
    ``` py
    from PharmaPy import rxnorm

    drug = "cipro"

    result = rxnorm.get_drug_class_by_name(drug)

    print(result)

    ```
</li>
<br>
<li> The <strong>get_drug_class_by_ndc(ndc)</strong> function returns the class of a drug given its ndc. </li>
    
    ``` py
    from PharmaPy import rxnorm

    ndc = "0777310502"

    result = rxnorm.get_drug_class_by_ndc(ndc)

    print(result)

    ```
</li>
<br>
<li> The <strong>get_fda_rxcuis(drug_name)</strong> returns a list of dicionaries of the keys of all the drug names with corresponding rxcui values, given that the drug exists in the FDA API. </li>
    
    ``` py
    from PharmaPy import rxnorm

    ndc = "0777310502"

    result = rxnorm.get_drug_class_by_ndc(ndc)

    print(result)

    ```
</li>

</ul>