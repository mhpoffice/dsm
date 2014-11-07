## DSM

There are two types of DSM records. The first is a record containing all of the information about the code (A `DSM Codepoint`. The second, called `DSM Diagnosis` is only the information suitable for use in a diagnosis, and contains only the portions that are relevant to a single diagnostic instance.

### DSM Codepoint JSON

### DSM Diagnosis JSON

    {
      "DSM5": {
        "section": "",
        "subsection": "",
        "name": "",
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
      },
      "ICD10": {
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
        "sg": "SG001",
        "sid": "S503"
        "type": "Specify current severity",
        "value": "Mild"
    }



