# ContractNLI_using_BERT
# ContractNLI

A Dataset for Document-level Natural Language Inference for Contracts

![image](https://github.com/areegtarek/ContractNLI-using-BERT/assets/46351336/d0fa0614-626f-409a-b8f3-2e0296051150)

ContractNLI is a dataset for document-level natural language inference (NLI) on contracts whose goal is to automate/support a time-consuming procedure of contract review. In this task, a system is given a set of hypotheses (such as “Some obligations of Agreement may survive termination.”) and a contract, and it is asked to classify whether each hypothesis is entailed by, contradicting to or not mentioned by (neutral to) the contract as well as identifying evidence for the decision as spans in the contract.

Dataset specification
More formally, the task consists of:

Natural language inference (NLI): Document-level three-class classification (one of Entailment, Contradiction or NotMentioned). Evidence identification: Multi-label binary classification over span_s, where a _span is a sentence or a list item within a sentence. This is only defined when NLI label is either Entailment or Contradiction. Evidence spans need not be contiguous but need to be comprehensively identified where they are redundant. We have 17 hypotheses annotated on 607 non-disclosure agreements (NDAs). The hypotheses are fixed throughout all the contracts including the test dataset.

Our dataset is provided as JSON files.

      {
        "documents": [
          {
            "id": 1,
            "file_name": "example.pdf",
            "text": "NON-DISCLOSURE AGREEMENT\nThis NON-DISCLOSURE AGREEMENT (\"Agreement\") is entered into this ...",
            "document_type": "search-pdf",
            "url": "https://examplecontract.com/example.pdf",
            "spans": [
              [0, 24],
              [25, 89],
              ...
            ],
            "annotation_sets": [
              {
                "annotations": {
                  "nda-1": {
                    "choice": "Entailment",
                    "spans": [
                      12,
                      13,
                      91
                    ]
                  },
                  "nda-2": {
                    "choice": "NotMentioned",
                    "spans": []
                  },
                  ...
                }
              }
            ]
          },
          ...
        ],
        "labels": {
          "nda-1": {
            "short_description": "Explicit identification",
            "hypothesis": "All Confidential Information shall be expressly identified by the Disclosing Party."
          },
          ...
        }
      }
