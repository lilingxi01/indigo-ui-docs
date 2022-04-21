---
description: A component box having some checkboxes.
---

# BPCheckboxGroup

## Preview

![BPCheckboxGroup](<../.gitbook/assets/CleanShot 2022-04-21 at 00.30.45@2x.png>)

## Properties

| Prop       | Type                | Description                                                                                                                                                                            |
| ---------- | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`       | String              | The component id that can be used to identify HTML elements in testing.                                                                                                                |
| `label`    | String \| ReactNode | The label that appears above the box. It can be a string or a React Node.                                                                                                              |
| `onChange` | (String\[]) -> Void | A callback function being triggered when selection has been changed. This function will give you a list of selected keys.                                                              |
| `options`  | Object\[]           | [Check here.](bptextinput-6.md#undefined)                                                                                                                                              |
| `selected` | String\[]           | A list of selected keys from options.                                                                                                                                                  |
| `hint`     | String              | The hint information. You should set it back to `null` when you do not want to show it anymore. [Check here](bptextinput-6.md#how-to-use-hint-and-error-properly) for usage guidance.  |
| `error`    | String              | The error information. You should set it back to `null` when you do not want to show it anymore. [Check here](bptextinput-6.md#how-to-use-hint-and-error-properly) for usage guidance. |
| `style`    | Object              | The style object (for React, not MUI) to the root of component.                                                                                                                        |
| `boxStyle` | Object              | The style object (for React, not MUI) to the box.                                                                                                                                      |

## Guidance

### How to fulfill property \`options\`?

`options` should be a list of objects. Each object has three properties: `key` , `label` , `color` .

* `key` : The key that will be returned for selection. Please be unique!
* `label` : The selection label displaying next to the checkbox. It could be a string or a React Node.
* `color` : The accent color of this checkbox. Using different colors (e.g. severities) may increase the intuition.&#x20;

This is a sample option list:

```javascript
const sampleOptions = [
  {
    key: 'option-1',
    label: 'Option 1',
    color: BPColors.green[600],
  },
  {
    key: 'option-2',
    label: 'Option 2',
    color: BPColors.gray[600],
  },
  {
    key: 'option-3',
    label: 'Option 3',
    color: BPColors.green[300],
  },
  {
    key: 'option-4',
    label: 'Option 4',
    color: BPColors.red[600],
  },
];
```

### An integrated usage example

<details>

<summary>Example code of Business Process Severity Selector</summary>

```javascript
const severityOptions = [
  {
    key: 'success',
    label: 'Success',
    color: BPColors.success,
  },
  {
    key: 'info',
    label: 'Info',
    color: BPColors.info,
  },
  {
    key: 'warning',
    label: 'Warning',
    color: BPColors.warning,
  },
  {
    key: 'error',
    label: 'Error',
    color: BPColors.error,
  },
];

export const BPSeveritySelector = ({id = 'bp-severity-selector', label, onChange, style, boxStyle, hint, error}) => {
  const [selected, setSelected] = useState(['success', 'info', 'warning', 'error']);
  return (
    <BPCheckboxGroup
      id={id}
      label={label}
      onChange={(selection) => {
        setSelected(selection);
        onChange(selection);
      }}
      style={style}
      boxStyle={boxStyle}
      hint={hint}
      error={error}
      options={severityOptions}
      selected={selected}
    />
  );
};
```

</details>

### How to use \`hint\` and \`error\` properly?

The hint is a **gray** text under the input field. The error is a <mark style="color:red;">**red**</mark> text under the input field.

You should use hint to notify user of an expected behavior, and you should use error to warn user of an unexpected behavior.

You can create two states for hint and message, and pass them to the properties of BPTextInput. Once you want to display an information, set a string to the corresponding state. Once you want to remove the message, set `null` to the corresponding state.

{% hint style="info" %}
When both **hint** and <mark style="color:red;">**error**</mark> are set (not null), we will _only_ display the <mark style="color:red;">**error**</mark> because it should be more severe.
{% endhint %}

![Hint Message](<../.gitbook/assets/Screen Shot 2022-04-18 at 4.27.27 PM.png>)

![Error Message](<../.gitbook/assets/Screen Shot 2022-04-18 at 4.26.42 PM.png>)



