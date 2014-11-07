## DSM

There are two types of DSM records. The first is a record containing all of the information about the code (A `DSM Codepoint`. The second, called `DSM Diagnosis` is only the information suitable for use in a diagnosis, and contains only the portions that are relevant to a single diagnostic instance.

### DSM Codepoint JSON

The ICD9/10 arrays define which codes are used if the exact combination of specifiers are present. If a non-exact match occurs, the instance with `specifiers` set to `null` will be used.

    {
        "DSM5": {
            "section": "",
            "subsection": "",
            "name": "",
            "subname": "",
            "specifier_groups": [
                "SG001",
                "SG004"
            ]
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
        "DSM5": {
            "section": "",
            "subsection": "",
            "name": "",
            "subname": "",
            "specify": [
                {
                    "specify_id": "s14",
                    "type": "specify if",
                    "value": "First episode"
                },
                {
                    "specify_id": "s14",
                    "type": "specify if",
                    "value": "First episode"
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


### Specifiers

For the specifiers, we have separated each one into a unique specifier code.

Each specifier is a member of a `Specifier Group`.

#### Specifier Group JSON

    {
        "type": "Specify if",
        "notes": "Only used after 1 year",
        "sg": "SG001",
        "dsm_version": "DSM5"
    }

#### Specifier JSON

    {
        "sg": "SG002",
        "specify_id": "S503"
        "type": "Specify current severity",
        "value": "Mild"
    }



