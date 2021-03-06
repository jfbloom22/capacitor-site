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
<div class="docgen docgen-index">

* [`show()`](#show)
* [`hide()`](#hide)
* [`setAccessoryBarVisible(...)`](#setaccessorybarvisible)
* [`setScroll(...)`](#setscroll)
* [`setStyle(...)`](#setstyle)
* [`setResizeMode(...)`](#setresizemode)
* [`addListener(...)`](#addlistener)
* [`addListener(...)`](#addlistener)
* [`addListener(...)`](#addlistener)
* [`addListener(...)`](#addlistener)
* [`removeAllListeners()`](#removealllisteners)
* [Interfaces](#interfaces)
* [Enums](#enums)

</div>
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

<!--DOCGEN_API_START-->
<!--Update the source file JSDoc comments and rerun docgen to update the docs below-->
<div class="docgen docgen-api">

## API

### show()

```typescript
show() => Promise<void>
```

Show the keyboard. This method is alpha and may have issues

**Returns:** <code>Promise&lt;void&gt;</code>

--------------------


### hide()

```typescript
hide() => Promise<void>
```

Hide the keyboard.

**Returns:** <code>Promise&lt;void&gt;</code>

--------------------


### setAccessoryBarVisible(...)

```typescript
setAccessoryBarVisible(options: { isVisible: boolean; }) => Promise<void>
```

Set whether the accessory bar should be visible on the keyboard. We recommend disabling
the accessory bar for short forms (login, signup, etc.) to provide a cleaner UI

| Param         | Type                                 |
| ------------- | ------------------------------------ |
| **`options`** | <code>{ isVisible: boolean; }</code> |

**Returns:** <code>Promise&lt;void&gt;</code>

--------------------


### setScroll(...)

```typescript
setScroll(options: { isDisabled: boolean; }) => Promise<void>
```

Programmatically enable or disable the WebView scroll

| Param         | Type                                  |
| ------------- | ------------------------------------- |
| **`options`** | <code>{ isDisabled: boolean; }</code> |

**Returns:** <code>Promise&lt;void&gt;</code>

--------------------


### setStyle(...)

```typescript
setStyle(options: KeyboardStyleOptions) => Promise<void>
```

Programmatically set the keyboard style

| Param         | Type                                                                  |
| ------------- | --------------------------------------------------------------------- |
| **`options`** | <code><a href="#keyboardstyleoptions">KeyboardStyleOptions</a></code> |

**Returns:** <code>Promise&lt;void&gt;</code>

--------------------


### setResizeMode(...)

```typescript
setResizeMode(options: KeyboardResizeOptions) => Promise<void>
```

Programmatically set the resize mode

| Param         | Type                                                                    |
| ------------- | ----------------------------------------------------------------------- |
| **`options`** | <code><a href="#keyboardresizeoptions">KeyboardResizeOptions</a></code> |

**Returns:** <code>Promise&lt;void&gt;</code>

--------------------


### addListener(...)

```typescript
addListener(eventName: 'keyboardWillShow', listenerFunc: (info: KeyboardInfo) => void) => PluginListenerHandle
```

| Param              | Type                                      |
| ------------------ | ----------------------------------------- |
| **`eventName`**    | <code>"keyboardWillShow"</code>           |
| **`listenerFunc`** | <code>(info: KeyboardInfo) => void</code> |

**Returns:** <code><a href="#pluginlistenerhandle">PluginListenerHandle</a></code>

--------------------


### addListener(...)

```typescript
addListener(eventName: 'keyboardDidShow', listenerFunc: (info: KeyboardInfo) => void) => PluginListenerHandle
```

| Param              | Type                                      |
| ------------------ | ----------------------------------------- |
| **`eventName`**    | <code>"keyboardDidShow"</code>            |
| **`listenerFunc`** | <code>(info: KeyboardInfo) => void</code> |

**Returns:** <code><a href="#pluginlistenerhandle">PluginListenerHandle</a></code>

--------------------


### addListener(...)

```typescript
addListener(eventName: 'keyboardWillHide', listenerFunc: () => void) => PluginListenerHandle
```

| Param              | Type                            |
| ------------------ | ------------------------------- |
| **`eventName`**    | <code>"keyboardWillHide"</code> |
| **`listenerFunc`** | <code>() => void</code>         |

**Returns:** <code><a href="#pluginlistenerhandle">PluginListenerHandle</a></code>

--------------------


### addListener(...)

```typescript
addListener(eventName: 'keyboardDidHide', listenerFunc: () => void) => PluginListenerHandle
```

| Param              | Type                           |
| ------------------ | ------------------------------ |
| **`eventName`**    | <code>"keyboardDidHide"</code> |
| **`listenerFunc`** | <code>() => void</code>        |

**Returns:** <code><a href="#pluginlistenerhandle">PluginListenerHandle</a></code>

--------------------


### removeAllListeners()

```typescript
removeAllListeners() => void
```

Remove all native listeners for this plugin

**Returns:** <code>void</code>

--------------------


### Interfaces


#### KeyboardStyleOptions

| Prop        | Type                                                    |
| ----------- | ------------------------------------------------------- |
| **`style`** | <code><a href="#keyboardstyle">KeyboardStyle</a></code> |


#### KeyboardResizeOptions

| Prop       | Type                                                      |
| ---------- | --------------------------------------------------------- |
| **`mode`** | <code><a href="#keyboardresize">KeyboardResize</a></code> |


#### PluginListenerHandle

| Prop         | Type                    |
| ------------ | ----------------------- |
| **`remove`** | <code>() => void</code> |


#### KeyboardInfo

| Prop                 | Type                |
| -------------------- | ------------------- |
| **`keyboardHeight`** | <code>number</code> |


### Enums


#### KeyboardStyle

| Members     | Value                |
| ----------- | -------------------- |
| **`Dark`**  | <code>"DARK"</code>  |
| **`Light`** | <code>"LIGHT"</code> |


#### KeyboardResize

| Members      | Value                 |
| ------------ | --------------------- |
| **`Body`**   | <code>"body"</code>   |
| **`Ionic`**  | <code>"ionic"</code>  |
| **`Native`** | <code>"native"</code> |
| **`None`**   | <code>"none"</code>   |

</div>
<!--DOCGEN_API_END-->
