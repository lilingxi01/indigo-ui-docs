---
description: A magic component that can be used to let user input a date.
---

# BPDatePicker

## Preview

![BPDatePicker](<../.gitbook/assets/Screen Shot 2022-04-18 at 5.37.04 PM.png>)

## Properties

| Prop       | Type                | Description                                                                                                                                                                            |
| ---------- | ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`       | String              | The component id that can be used to identify HTML elements in testing.                                                                                                                |
| `label`    | String \| ReactNode | The label that appears above the input field. It can be a string or a React Node.                                                                                                      |
| `onChange` | (Date) -> Void      | A callback function being triggered when inputted date is changed (not when user is inputting). This function will give you a parsed date object.                                      |
| `baseDate` | Date                | The date object indicate the base date of all magic modifiers. All modification will be made based on the given base date. By default, it is `now` .                                   |
| `hint`     | String              | The hint information. You should set it back to `null` when you do not want to show it anymore. [Check here](bptextinput-3.md#how-to-use-hint-and-error-properly) for usage guidance.  |
| `error`    | String              | The error information. You should set it back to `null` when you do not want to show it anymore. [Check here](bptextinput-3.md#how-to-use-hint-and-error-properly) for usage guidance. |

## Guidance

### Why there is no \`value\`?

Because the algorithm inside BPDatePicker is complicated, we do not want you to validate it before it is finalized (which may increase the complexity for users). But you can still give users a hint or an error when parsed date is not correct.

### How to use \`hint\` and \`error\` properly?

The hint is a **gray** text under the input field. The error is a <mark style="color:red;">**red**</mark> text under the input field.

You should use hint to notify user of an expected behavior, and you should use error to warn user of an unexpected behavior.

You can create two states for hint and message, and pass them to the properties of BPTextInput. Once you want to display an information, set a string to the corresponding state. Once you want to remove the message, set `null` to the corresponding state.

{% hint style="info" %}
When both **hint** and <mark style="color:red;">**error**</mark> are set (not null), we will _only_ display the <mark style="color:red;">**error**</mark> because it should be more severe.
{% endhint %}

![Hint Message](<../.gitbook/assets/Screen Shot 2022-04-18 at 4.27.27 PM.png>)

![Error Message](<../.gitbook/assets/Screen Shot 2022-04-18 at 4.26.42 PM.png>)



