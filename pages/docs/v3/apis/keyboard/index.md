---
title: Keyboard
description: Keyboard API
contributors:
  - mlynch
  - jcesarmobile
---

<plugin-platforms platforms="ios,android"></plugin-platforms>

# Keyboard

The Keyboard API provides keyboard display and visibility control, along with event tracking when the keyboard shows and hides.

<!--DOCGEN_INDEX_START-->
* [show()](#show)
* [hide()](#hide)
* [setAccessoryBarVisible()](#setaccessorybarvisible)
* [setScroll()](#setscroll)
* [setStyle()](#setstyle)
* [setResizeMode()](#setresizemode)
* [addListener()](#addlistener)
* [addListener()](#addlistener)
* [addListener()](#addlistener)
* [addListener()](#addlistener)
* [removeAllListeners()](#removealllisteners)
* [Interfaces](#interfaces)
* [Enums](#enums)
<!--DOCGEN_INDEX_END-->


## Window Events for cordova-plugin-ionic-keyboard compatibility

* keyboardWillShow
* keyboardDidShow
* keyboardWillHide
* keyboardDidHide

## Example

```typescript
import { Plugins, KeyboardInfo } from '@capacitor/core';

const { Keyboard } = Plugins;

// Keyboard Plugin Events

Keyboard.addListener('keyboardWillShow', (info: KeyboardInfo) => {
  console.log('keyboard will show with height', info.keyboardHeight);
});

Keyboard.addListener('keyboardDidShow', (info: KeyboardInfo) => {
  console.log('keyboard did show with height', info.keyboardHeight);
});

Keyboard.addListener('keyboardWillHide', () => {
  console.log('keyboard will hide');
});

Keyboard.addListener('keyboardDidHide', () => {
  console.log('keyboard did hide');
});

// window events

window.addEventListener('keyboardWillShow', (e) => {
  console.log('keyboard will show with height', (<any>e).keyboardHeight);
});

window.addEventListener('keyboardDidShow', (e) => {
  console.log("keyboard did show with height", (<any>e).keyboardHeight);
});

window.addEventListener('keyboardWillHide', () => {
  console.log('keyboard will hide');
});

window.addEventListener('keyboardDidHide', () => {
  console.log('keyboard did hide');
});

// API

Keyboard.setAccessoryBarVisible({isVisible: false});

Keyboard.show();

Keyboard.hide();

```

## Keyboard configuration (iOS only)

The keyboard plugin allows the following configuration values to be added in `capacitor.config.json` for the iOS platform:

- `resize`: It configures the way the app is resized when the Keyboard appears.
Allowed values are
  - `none`: Not the app, nor the webview are resized
  - `native`: (default) The whole native webview will be resized when the keyboard shows/hides, it will affect the `vh` relative unit.
  - `body`: Only the html `<body>` element will be resized. Relative units are not affected, because the viewport does not change.
  - `ionic`: Only the html ion-app element will be resized. Use it only for ionic apps.

- `style`: If set to `dark` it will use Dark style keyboard instead of the regular one.

```json
{
  "plugins": {
    "Keyboard": {
      "resize": "body",
      "style": "dark"
    }
  }
}
```

## API

<!--DOCGEN_API_START-->
<!--Update the source file JSDoc comments and rerun docgen to update the docs below-->
## API

### show

```typescript
show() => Promise<void>
```

Show the keyboard. This method is alpha and may have issues

**Returns:** Promise&lt;void&gt;

--------------------


### hide

```typescript
hide() => Promise<void>
```

Hide the keyboard.

**Returns:** Promise&lt;void&gt;

--------------------


### setAccessoryBarVisible

```typescript
setAccessoryBarVisible(options: { isVisible: boolean; }) => Promise<void>
```

Set whether the accessory bar should be visible on the keyboard. We recommend disabling
the accessory bar for short forms (login, signup, etc.) to provide a cleaner UI

| Param       | Type                    |
| ----------- | ----------------------- |
| **options** | { isVisible: boolean; } |

**Returns:** Promise&lt;void&gt;

--------------------


### setScroll

```typescript
setScroll(options: { isDisabled: boolean; }) => Promise<void>
```

Programmatically enable or disable the WebView scroll

| Param       | Type                     |
| ----------- | ------------------------ |
| **options** | { isDisabled: boolean; } |

**Returns:** Promise&lt;void&gt;

--------------------


### setStyle

```typescript
setStyle(options: KeyboardStyleOptions) => Promise<void>
```

Programmatically set the keyboard style

| Param       | Type                                          |
| ----------- | --------------------------------------------- |
| **options** | [KeyboardStyleOptions](#keyboardstyleoptions) |

**Returns:** Promise&lt;void&gt;

--------------------


### setResizeMode

```typescript
setResizeMode(options: KeyboardResizeOptions) => Promise<void>
```

Programmatically set the resize mode

| Param       | Type                                            |
| ----------- | ----------------------------------------------- |
| **options** | [KeyboardResizeOptions](#keyboardresizeoptions) |

**Returns:** Promise&lt;void&gt;

--------------------


### addListener

```typescript
addListener(eventName: 'keyboardWillShow', listenerFunc: (info: KeyboardInfo) => void) => PluginListenerHandle
```

| Param            | Type                         |
| ---------------- | ---------------------------- |
| **eventName**    | "keyboardWillShow"           |
| **listenerFunc** | (info: KeyboardInfo) => void |

**Returns:** [PluginListenerHandle](#pluginlistenerhandle)

--------------------


### addListener

```typescript
addListener(eventName: 'keyboardDidShow', listenerFunc: (info: KeyboardInfo) => void) => PluginListenerHandle
```

| Param            | Type                         |
| ---------------- | ---------------------------- |
| **eventName**    | "keyboardDidShow"            |
| **listenerFunc** | (info: KeyboardInfo) => void |

**Returns:** [PluginListenerHandle](#pluginlistenerhandle)

--------------------


### addListener

```typescript
addListener(eventName: 'keyboardWillHide', listenerFunc: () => void) => PluginListenerHandle
```

| Param            | Type               |
| ---------------- | ------------------ |
| **eventName**    | "keyboardWillHide" |
| **listenerFunc** | () => void         |

**Returns:** [PluginListenerHandle](#pluginlistenerhandle)

--------------------


### addListener

```typescript
addListener(eventName: 'keyboardDidHide', listenerFunc: () => void) => PluginListenerHandle
```

| Param            | Type              |
| ---------------- | ----------------- |
| **eventName**    | "keyboardDidHide" |
| **listenerFunc** | () => void        |

**Returns:** [PluginListenerHandle](#pluginlistenerhandle)

--------------------


### removeAllListeners

```typescript
removeAllListeners() => void
```

Remove all native listeners for this plugin

**Returns:** void

--------------------


### Interfaces


#### KeyboardStyleOptions

| Prop      | Type                            |
| --------- | ------------------------------- |
| **style** | [KeyboardStyle](#keyboardstyle) |


#### KeyboardResizeOptions

| Prop     | Type                              |
| -------- | --------------------------------- |
| **mode** | [KeyboardResize](#keyboardresize) |


#### PluginListenerHandle

| Prop       | Type       |
| ---------- | ---------- |
| **remove** | () => void |


#### KeyboardInfo

| Prop               | Type   |
| ------------------ | ------ |
| **keyboardHeight** | number |


### Enums


#### KeyboardStyle

| Members   | Value   |
| --------- | ------- |
| **Dark**  | "DARK"  |
| **Light** | "LIGHT" |


#### KeyboardResize

| Members    | Value    |
| ---------- | -------- |
| **Body**   | "body"   |
| **Ionic**  | "ionic"  |
| **Native** | "native" |
| **None**   | "none"   |


<!--DOCGEN_API_END-->
