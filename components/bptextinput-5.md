---
description: A component of single checkbox (with label).
---

# BPCheckbox

## Preview

![BPCheckbox](<../.gitbook/assets/Screen Shot 2022-04-18 at 5.39.01 PM.png>)

## Properties

| Prop              | Type                      | Description                                                                                                                                      |
| ----------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`              | String                    | The component id that can be used to identify HTML elements in testing.                                                                          |
| `defaultSelected` |  Boolean \| () -> Boolean | Should it be selected by default? It could be a function (if you need to determine it by checking some other values) or just an initial value.   |
| `onChange`        | (String\[]) -> Void       | A callback function being triggered when selection is changed. This function will take a boolean indicating if this checkbox is selected or not. |
| `contentColor`    | String                    | A color string for children (label). By default, it is a gray color.                                                                             |
| `idleColor`       | String                    | A color string for box when it is not selected. By default, it is a light gray color.                                                            |
| `activeColor`     | String                    | A color string for box when it is selected. By default, it is brand color.                                                                       |

## Guidance

### How to use it?

A minimal example on how to use it should be:

```javascript
<BPCheckbox
    id={`an-info-checkbox`}
    activeColor={BPColors.info}
    contentColor={BPColors.info}
    onChange={(selected) => {
        // Callback here.
        onCheckboxChange('info')(selected);
    }}
    defaultSelected={() => {
        return selectedSeverity.includes('info');
    }}
>
    // This is the label.
    Info
</BPCheckbox>
```
