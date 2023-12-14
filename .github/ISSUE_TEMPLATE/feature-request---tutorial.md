name: Feature Request
description: Request a tutorial to add to this repository
title: "[Feature Request]: "
labels: ["feature", "new"]
assignees:
  - phyk
body:
  - type: markdown
    attributes:
      value: |
        Thanks for taking the time to propose a new topic!
  - type: input
    id: lecture
    attributes:
      label: Your Lecture
      description: Which lecture are you taking?
      placeholder: ex. AA
    validations:
      required: true
  - type: textarea
    id: what
    attributes:
      label: What do you propose?
      description: Also tell us, why do you want to see it?
      placeholder: First, state the idea as simple as possible. Then shortly state why you think it is interesting.
    validations:
      required: true
  - type: dropdown
    id: language
    attributes:
      label: Language
      description: To which area does this feature request belong?
      options:
        - General Machine Learning
        - General Optimization
        - Python
        - Julia
        - Software Engineering
        - Other
      default: 0
    validations:
      required: true
  - type: checkboxes
    id: terms
    attributes:
      label: Code of Conduct
      description: By submitting this issue, you agree to follow our [Code of Conduct](https://example.com)
      options:
        - label: I agree to follow this project's Code of Conduct
          required: true
