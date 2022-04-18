---
description: >-
  A component for users to select a domain (including EAI Domains, Publishing
  Business Domains, and more).
---

# BPDomainSelector

## Properties

| Prop                | Type                | Description                                                                                                                                                   |
| ------------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`                | String              | The component id that can be used to identify HTML elements in testing.                                                                                       |
| `label`             | String \| ReactNode | The label that appears above the input field. It can be a string or a React Node.                                                                             |
| `onChange`          | (String\[]) -> Void | A callback function being triggered when selection is changed. This function will take a list of string (the string corresponds to the id/key of items).      |
| `searchPlaceholder` | String              | A string that will be the placeholder of the search field. It can be used to guide users while doing a search (to let them know what they are searching for). |
| `list`              | String\[]           | A string list that has all selection options.                                                                                                                 |

## Guidance

### \`onChange\`

When `All` is selected, the function `onChange` will callback an empty list. Otherwise, it will return a list of selected entry strings.

### How to use it?

A minimal example on how to use it should be:

```javascript
<BPDomainSelector
  id={'an-id'}
  label={'Business Domain'}
  searchPlaceholder={'Search a business domain'}
  list={aBusinessDomainSampleList} // Put the list into here. It could be a state.
  onChange={(selected) => {
    setSelectedBusinessDomain(selected);
    // `selected` is a list even when there is only one selected option.
  }}
/>
```
