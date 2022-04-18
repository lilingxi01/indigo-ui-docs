---
description: >-
  A text-inputting component that can accept user's input and callback on input
  changed.
---

# BPTextInput

## Properties

| Prop           | Type                | Description                                                                                                                                                |
| -------------- | ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`           | String              | The component id that can be used to identify HTML elements in testing.                                                                                    |
| `label`        | String \| ReactNode | The label that appears above the input field. It can be a string or a React Node.                                                                          |
| `boxRef`       | (ReactNode) -> Void | A function to get the reference of input box (a box includes the entire rectangle including input field, before-field elements, and after-field elements). |
| `value`        | String              | The value in the input field. [Check here](bptextinput.md#how-to-use-value-property) for more information on usage.                                        |
| `onChange`     | (Event) -> Void     | A callback function being triggered when input is changed. This function will take an event.                                                               |
| `onTextChange` | (String) -> Void    | A callback function being triggered when input is changed. This function will take inputted string only.                                                   |
| `placeholder`  | String              | The placeholder of input field.                                                                                                                            |
| `style`        | Object              | A typical style object (of React, not MUI) for the root of component.                                                                                      |
| `boxStyle`     | Object              | A typical style object (of React, not MUI) for the box.                                                                                                    |
| `inputStyle`   | Object              | A typical style object (of React, not MUI) for the input field.                                                                                            |
| `onFocus`      | (Event) -> Void     | A callback function being triggered when input field is on focused.                                                                                        |
| `onClick`      | (Event) -> Void     | A callback function being triggered when input field is on clicked. (An `onClick` callback will not be triggered if the focus is not taken by a click)     |
| `onBlur`       | (Event) -> Void     | A callback function being triggered when input field is not on focused anymore (on blurred).                                                               |
| `onEnterPress` | (Event) -> Void     | A callback function being triggered when keyboard ENTER (or RETURN) is being pressed and the input field is on focused.                                    |
| `onEscPress`   | (Event) -> Void     | A callback function being triggered when keyboard ESC (or ESCAPE) is being pressed and the input field is on focused.                                      |
| `disableInput` | Bool                | Should the input field be disabled?                                                                                                                        |
| `beforeField`  | ReactNode           | Content displayed before the input field but inside the input box. Clicking it (without any additional event) should active the input field.               |
| `afterField`   | ReactNode           | Content displayed after the input field but inside the input box. Clicking it (without any additional event) should active the input field.                |
| `hint`         | String              | The hint information. You should set it back to `null` when you do not want to show it anymore. Check here for usage guidance.                             |
| `error`        | String              | The error information. You should set it back to `null` when you do not want to show it anymore. Check here for usage guidance.                            |

## Guidance

### How to use \`value\` property

The value property should be the value state. By default, the value inputted will not go into the input field directly, it will trigger the `onChange` callback for you to validate it and store it into a value state, then send it back to the `BPTextInput` .

A minimal example on how to use it should be:

```javascript
const [sampleState, setSampleState] = useState('');

return (
    <BPTextInput
        value={sampleState} // Pass in the state.
        onChange={(value) => {
            // You can validate the value here.
            // If the value is invalid, you can ignore this input,
            // so it will not appear in the input field.vas
            setSampleState(value); // Use callback to set the state.
        }}
    />
);
```

{% hint style="info" %}
**Good to know:** We want to help you control the validation of the inputted text. This would be the best way.
{% endhint %}

### How to use \`hint\` and \`error\` properly?

The hint is a **gray** text under the input field. The error is a <mark style="color:red;">**red**</mark> text under the input field.

You should use hint to notify user of an expected behavior, and you should use error to warn user of an unexpected behavior.

You can create two states for hint and message, and pass them to the properties of BPTextInput. Once you want to display an information, set a string to the corresponding state. Once you want to remove the message, set `null` to the corresponding state.

{% hint style="info" %}
When both **hint** and <mark style="color:red;">**error**</mark> are set (not null), we will _only_ display the <mark style="color:red;">**error**</mark> because it should be more severe.
{% endhint %}

![Hint Message](<../.gitbook/assets/Screen Shot 2022-04-18 at 4.27.27 PM.png>)

![Error Message](<../.gitbook/assets/Screen Shot 2022-04-18 at 4.26.42 PM.png>)



