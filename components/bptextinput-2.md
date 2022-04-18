---
description: A consistent primary button component.
---

# BPButton

## Preview

![BPButton](<../.gitbook/assets/Screen Shot 2022-04-18 at 5.36.43 PM.png>)

## Properties

| Prop      | Type            | Description                                                                   |
| --------- | --------------- | ----------------------------------------------------------------------------- |
| `id`      | String          | The component id that can be used to identify HTML elements in testing.       |
| `style`   | Object          | A typical style object (of React, support MUI `sx`) for the button component. |
| `onClick` | (Event) -> Void | The callback function when button is clicked.                                 |

## Guidance

### How to use it?

A minimal example on how to use it should be:

```javascript
<BPInput
    id={'a-primary-button-id'}
    onClick={(event) => {
        // Do something when button is clicked.
    }}
/>
```
