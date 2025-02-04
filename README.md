<h1 align="center">
Ant Design Pro Layout
</h1>

<div align="center">

[![NPM version](https://img.shields.io/npm/v/@ant-design-vue/pro-layout/next?style=flat)](https://npmjs.org/package/@ant-design-vue/pro-layout) [![Vue Support](https://img.shields.io/badge/support-Vue3-green?style=flat)](./package.json) [![Vue Grammar Level](https://img.shields.io/badge/full-Composition%20API-blue?style=flat)](https://v3.vuejs.org/guide/composition-api-introduction.html) [![NPM downloads](http://img.shields.io/npm/dm/@ant-design-vue/pro-layout.svg?style=flat)](https://npmjs.org/package/@ant-design-vue/pro-layout) [![License](https://img.shields.io/github/license/vueComponent/pro-layout)](./LICENSE)

</div>

## Install

```bash
# yarn
yarn add @ant-design-vue/pro-layout@next
# npm
npm i @ant-design-vue/pro-layout@next -S
```

## Basic Usage

First, you should add the `@ant-design-vue/pro-layout` that you need into the library.

```js
import 'ant-design-vue/dist/antd.less'; // antd css
import '@ant-design-vue/pro-layout/dist/style.css'; // pro-layout css or style.less

import { createApp } from 'vue';
import ProLayout, { PageContainer } from '@ant-design-vue/pro-layout';

const app = createApp();

app.use(ProLayout).use(PageContainer).mount('#app');
```

After that, you can use pro-layout in your Vue components as simply as this:

```vue
<template>
  <pro-layout
    :locale="locale"
    v-bind="state"
    v-model:openKeys="state.openKeys"
    v-model:collapsed="state.collapsed"
    v-model:selectedKeys="state.selectedKeys"
  >
    <router-view />
  </pro-layout>
</template>

<script>
import { defineComponent, reactive } from 'vue';
// import { getMenuData, clearMenuItem } from '@ant-design-vue/pro-layout';

const locale=(i18n: string) => i18n;

export default defineComponent({
  setup() {
    const state = reactive({
      collapsed: false,
      openKeys: ['/dashboard'],
      selectedKeys: ['/welcome'],

      isMobile: false,
      fixSiderbar: false,
      fixedHeader: false,
      menuData: [],
      sideWidth: 208,
      hasSideMenu: true,
      hasHeader: true,
      hasFooterToolbar: false,
      setHasFooterToolbar: has => (state.hasFooterToolbar = has),
    });

    return {
      locale,
      state,
    };
  },
});
</script>
```

or `TSX`

```tsx
import { defineComponent, reactive } from 'vue';
import { RouterView } from 'vue-router';
import ProLayout from '@ant-design-vue/pro-layout';
import '@ant-design-vue/pro-layout/dist/style.css'; // pro-layout css or style.less

export default defineComponent({
  setup() {
    const state = reactive({
      collapsed: false,

      openKeys: ['/dashboard'],
      selectedKeys: ['/welcome'],

      isMobile: false,
      fixSiderbar: false,
      fixedHeader: false,
      menuData: [],
      sideWidth: 208,
      hasSideMenu: true,
      hasHeader: true,
      hasFooterToolbar: false,
      setHasFooterToolbar: (has: boolean) => (state.hasFooterToolbar = has),
    });

    return () => (
      <ProLayout {...state} locale={(i18n: string) => i18n}>
        <RouterView />
      </ProLayout>
    );
  },
});
```

## Build project

```bash
npm run build # Build library
npm run build:types # Build d.ts
```
