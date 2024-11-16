# SupportAI Chat Widget component

## Installation
```bash
npm i @supportai.it/vue-chat-widget
```

## Usage
Add the following component inside `src/App.vue`.

```vue
<script setup lang="ts">
import { ChatWidget } from '@supportai.it/vue-chat-widget';
</script>

<template>
  <h1>My Website</h1>

  <ChatWidget chat-url="<charUrl>"/>
</template>

```

## Customization
| **Attribute**      | **Description**                                                                | **Required** | **Example**         |
|--------------------|--------------------------------------------------------------------------------|--------------|---------------------|
| chat-url           | The link given by SupportAI to connect to the chat.                            | true         |                     |
| button-color       | Custom color of the open chat button.                                          | false        | #e74266             |
| button-hover-color | Custom color on hover of the open chat button.                                 | false        | #d6365d             |
| button-size        | Size of the chat button.                                                       | false        | 64px                |
| frame-width        | Width of the chat frame.                                                       | false        | 400                 |
| frame-height       | Height of the chat frame.                                                      | false        | 600                 |
| get-context        | A function that returns a string, it will be used by the assistant as context. | false        | () => "Hello World" |