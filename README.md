## DSM

There are two types of DSM records. The first is a record containing all of the information about the code (A `DSM Codepoint`. The second, called `DSM Diagnosis` is only the information suitable for use in a diagnosis, and contains only the portions that are relevant to a single diagnostic instance.

### DSM Codepoint JSON

The ICD9/10 arrays define which codes are used if the exact combination of specifiers are present. If a non-exact match occurs, the instance with `specifiers` set to `null` will be used.

    {
        "@dsm": "codepoint",
        "DSM5": {
            "dsm_code": "D5011",
            "dsm_revision": "DSM5",
            "section": "",
            "subsection": "",
            "subsubsection": "",
            "name": "",
            "subname": "",
            "specifier_groups": [
                "SG001",
                "SG004"
            ],
            "book_page": "45",
            "notes": "Any relevant diagnostic notes"
        },
        "ICD9": [
            {
                "code_2014": "319.00",
                "specifiers": null
            },
            {
                "code_2014": "319.01",
                "specifiers": ["S0032", "S0045"]
            }
        ],
        "ICD10": [
            {
                "code_2014": "F70",
                "specifiers": null
            }
        ]
    }

### DSM Diagnosis JSON

    {
        "@dsm": "diagnosis",
        "DSM5": {
            "dsm_code": "D5011",
            "dsm_revision": "DSM5",
            "section": "",
            "subsection": "",
            "subsubsection": "",
            "name": "",
            "subname": "",
            "specify": [
                {
                    "specify_id": "F14",
                    "type": "specify if",
                    "value": "First episode"
                },
                {
                    "specify_id": "F25",
                    "type": "specify curent severity",
                    "value": "Severe"
                }
            ]
        
        },
        "ICD9": {
            "code_2014": "319.00"
        },
        "ICD10": {
            "code_2014": "F70"
        }
    }

### DSM Diagnosis JSON

For efficient storage in a database, you can store a minimal representation. Only do this if you can expand it with a local/cached database of the full code information.

Also, the ICD9 and ICD10 sections are optional, as you can create those as well.

    {
        "@dsm": "mdiagnosis",
        "DSM5": {
            "dsm_code": "D5011",
            "dsm_revision": "DSM5",
            "specifiers": [
                "F1234",
                "F4321"
            ]
        },
        "ICD9": {
            "code_2014": "319.00"
        },
        "ICD10": {
            "code_2014": "F70"
        }
    }
    

#### Examples

For developers, here is an example of an ultra-minimal representation of a code:

    {"@dsm": "mdiagnosis","DSM5": {"dsm_code": "D5011","dsm_revision": "DSM5","specifiers": ["F1234","F4321"]}}
    
For clinicians, you should prevent this as one of these formats:

* D5011-F1234-F4321
* D5011-F1234-F4321 "Speech Sound Disorder"
* D5011-F1234-F4321 "Speech Sound Disorder: First Episode, Severe"


### Specifiers

For the specifiers, we have separated each one into a unique specifier code.

Each specifier is a member of a `Specifier Group`.

#### Specifier Group JSON

    {
        "type": "Specify if",
        "notes": "Only used after 1 year",
        "sg": "SG001",
        "dsm_revision": "DSM5"
    }

#### Specifier JSON

    {
        "sg": "SG002",
        "dsm_revision": "DSM5",
        "specify_id": "F503"
        "type": "Specify current severity",
        "value": "Mild"
    }



