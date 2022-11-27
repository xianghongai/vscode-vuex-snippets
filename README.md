# Vuex Snippet (Visual Studio Code)

用于快捷编写 [Vuex](https://vuex.vuejs.org/) (3.x, 4.x.)。

Quickly write Vuex (3.x, 4.x.).

另外按需安装:

Also need to install :

- [Vue Basic Snippets](https://marketplace.visualstudio.com/items?itemName=NicholasHsiang.vscode-vue-basic-snippets)，包含 Vue 2 和 3 中共用的 `v-*` 系列指令、`import` 组件、指令、服务之类的代码。
  Contains code for the `v-*` family of directives, `import` components, directives, and services common to Vue 2 and 3.
- [Vue 2 Snippets](https://marketplace.visualstudio.com/items?itemName=NicholasHsiang.vscode-vue2-snippets)，参考 Vue 2 官方文档示例及测试用例源码。
  Using Vue 2 official documentation example and test cases.
- [Vue 3 Snippets](https://marketplace.visualstudio.com/items?itemName=NicholasHsiang.vscode-vue3-snippets)，参考 Vue 3 官方文档示例及测试用例源码。
  Using Vue 3 official documentation example and test cases.
- [JavaScript Code Snippet](https://marketplace.visualstudio.com/items?itemName=NicholasHsiang.vscode-javascript-snippet)，参考 MDN 文档。
  Using MDN documentation.
- [JavaScript Comment Snippet](https://marketplace.visualstudio.com/items?itemName=NicholasHsiang.vscode-javascript-comment)，参考 JSDOC、ESDOC 文档，用于便捷编写 JavaScript 注释。
  Reference JSDOC, ESDOC documentation for easy writing of JavaScript comments.
- [Pinia Snippets](https://marketplace.visualstudio.com/items?itemName=NicholasHsiang.vscode-pinia-snippets)，参考 Pinia 官方文档示例。
  Using Pinia's official documentation example.

---

## Snippets

- Vuex.Store Constructor Options
- Vuex.Store Instance Properties
- Vuex.Store Instance Methods
- Component Binding Helpers

### Store

- Vuex <ins>C</ins>reate a new <ins>S</ins>tore (<ins>Vue2</ins>) | _prefix: `cs4vue2`_ →

```js
import Vue from 'vue';
import Vuex from 'vuex';
import resources from './modules/resources';

Vue.use(Vuex);

export default new Vuex.Store({
  modules: {
    resources,
  },
});
```

- Vuex <ins>C</ins>reate a new <ins>S</ins>tore | _prefix: `cs`_ →

```js
import { createStore, createLogger } from 'vuex';
import resources from './modules/resources';

const debug = process.env.NODE_ENV !== 'production';

export default createStore({
  modules: {
    resources,
  },
  strict: debug,
  plugins: debug ? [createLogger()] : [],
});
```

- Vuex <ins>C</ins>reate a new <ins>S</ins>tore (<ins>TS</ins>) | _prefix: `cs4ts`_ →

```ts
import { InjectionKey } from 'vue';
import { createStore, useStore as baseUseStore, Store } from 'vuex';

export interface State {
  property: any;
}

export const key: InjectionKey<Store<State>> = Symbol();

export const store = createStore<State>({
  state: {
    property: 'value',
  },
});

export function useStore() {
  return baseUseStore(key);
}

import { store, key } from './store';
app.use(store, key);
```

- Vuex <ins>u</ins>se<ins>S</ins>tore (<ins>TS</ins>) | _prefix: `us4ts`_ →

```ts
import { useStore } from '@/store';
const store = useStore();
```

- Vuex <ins>u</ins>se<ins>S</ins>tore | _prefix: `us`_ →

```js
import { useStore } from 'vuex';
const store = useStore();
```

### State

- Vuex <ins>State</ins> | *prefix: `state`*

```js
const state = () => ({
  property: 'value',
});
```

- Vuex store state (this.$store) | *prefix: `storeStateVm`*

```js
this.$store.state.propery
```

- Vuex store state | *prefix: `storeState`*

```js
store.state.propery
```

- Vuex <ins>im</ins>port <ins>m</ins>ap<ins>S</ins>tate | *prefix: `imms`*

```js
import { mapState } from 'vuex';
```

- Vuex mapState | *prefix: `ms`*

```js
...mapState({
  property: (state) => state.some.nested.module.property,
}),
```

- Vuex <ins>m</ins>ap<ins>S</ins>tate (<ins>n</ins>amespace) | *prefix: `msn`*

```js
...mapState('some/nested/module', {
  property: (state) => state.property,
}),
```

### Getters

- Vuex <ins>C</ins>reate <ins>G</ins>etters | *prefix: `cg`*

```js
export default {
  derivedResource(state) {
    
    return ;
  },
}
```

- Vuex <ins>G</ins>etters <ins>p</ins>roperty | *prefix: `gp`*

```js
derivedResource(state) {
  
  return ;
},
```

- Vuex <ins>G</ins>etters <ins>p</ins>roperty (<ins>M</ins>ethod-Style) | *prefix: `gpm`*

```js
derivedResource: (state) => (payload) => {
  
  return ;
},
```

- Vuex store getters (this.$store) | *prefix: `storeGettersVm`*

```js
this.$store.getters.propery
```

- Vuex store getters | *prefix: `storeGetters`*

```js
store.getters.propery
```

- Vuex <ins>im</ins>port map<ins>G</ins>etters | *prefix: `immg`*

```js
import { mapGetters } from 'vuex';
```

- Vuex <ins>m</ins>ap<ins>G</ins>etters | *prefix: `mg`*

```js
...mapGetters(['some/nested/module/someGetter', 'someGetter']),
```

- Vuex <ins>m</ins>ap<ins>G</ins>etters (<ins>n</ins>amespace) | *prefix: `mgn`*

```js
...mapGetters('some/nested/module', ['someGetter', 'someOtherGetter']),
```

- Vuex <ins>m</ins>ap<ins>G</ins>etters (<ins>d</ins>ifferent name) | *prefix: `mgd`*

```js
...mapGetters({
  alias: 'someGetter',
}),
```

### Mutations

- Vuex <ins>C</ins>reate <ins>Mu</ins>tations | *prefix: `cmu`*

```js
export default {
  mutation(state, payload) {
    
  },
};

```

- Vuex <ins>M</ins>utations <ins>p</ins>roperty | *prefix: `mp`*

```js
mutation(state, payload) {
  
},
```

- Vuex <ins>im</ins>port <ins>m</ins>ap<ins>M</ins>utations | *prefix: `immm`*

```js
import { mapMutations } from 'vuex';
```

- Vuex <ins>C</ins>ommitting <ins>M</ins>utation (this.$store) | *prefix: `storeCommit` / `cmvm`*

```js
this.$store.commit('someMutation');
```

- Vuex <ins>C</ins>ommitting <ins>M</ins>utation (this.$store, <ins>p</ins>ayload) | *prefix: `storeCommit` / `cmpvm`*

```js
this.$store.commit('someMutation', payload);
```

- Vuex <ins>C</ins>ommitting <ins>M</ins>utation | *prefix: `storeCommit` / `cm`*

```js
store.commit('someMutation');
```

- Vuex <ins>C</ins>ommitting <ins>M</ins>utation (<ins>p</ins>ayload) | *prefix: `storeCommit` / `cmp`*

```js
store.commit('someMutation', payload);
```

- Vuex <ins>C</ins>ommitting <ins>M</ins>utation (<ins>O</ins>bject-Style) | *prefix: `storeCommit` / `cmo`*

```js
store.commit({
  type: 'someMutation',
  payload,
});
```

- Vuex <ins>m</ins>ap<ins>M</ins>utations | *prefix: `mm`*

```js
...mapMutations(['some/nested/module/someMutation', 'someMutation']),
```

- Vuex <ins>m</ins>ap<ins>M</ins>utations (<ins>n</ins>amespace) | *prefix: `mmn`*

```js
...mapMutations('some/nested/module', ['someMutation', 'someOtherMutation']),
```

- Vuex <ins>m</ins>ap<ins>M</ins>utations (<ins>d</ins>ifferent name) | *prefix: `mmd`*

```js
...mapMutations({
  handler: 'someMutation',
}),
```

### Actions

- Vuex <ins>C</ins>reate <ins>A</ins>ctions | *prefix: `ca`*

```js
export default {
  async createResource(context, payload) {
    
  },
  async removeResource(context, payload) {
    
  },
  async updateResource(context, payload) {
    
  },
  async fetchResource(context, payload) {
    
  },
  async fetchAllResource(context, payload) {
    
  },
}
```

- Vuex <ins>A</ins>ction <ins>p</ins>roperty | *prefix: `ap`*

```js
handler(context, payload) {
  
},
```

- Vuex <ins>a</ins>sync <ins>A</ins>ction <ins>p</ins>roperty | *prefix: `asap`*

```js
async handler(context, payload) {
  
},
```

- Vuex <ins>i</ins>mport <ins>m</ins>apActions | *prefix: `imma`*

```js
import { mapActions } from 'vuex';
```

- Vuex <ins>D</ins>ispatching <ins>A</ins>ction (this.$store) | *prefix: `storeDispatch` / `davm`*

```js
this.$store.dispatch('someAction');
```

- Vuex <ins>D</ins>ispatching <ins>A</ins>ction (this.$store, <ins>p</ins>ayload) | *prefix: `storeDispatch` / `dapvm`*

```js
this.$store.dispatch('someAction', payload);
```

- Vuex <ins>D</ins>ispatching <ins>A</ins>ction | *prefix: `storeDispatch` / `da`*

```js
store.dispatch('someAction');
```

- Vuex <ins>D</ins>ispatching <ins>A</ins>ction (<ins>p</ins>ayload) | *prefix: `storeDispatch` / `dap`*

```js
store.dispatch('someAction', payload);
```

- Vuex <ins>D</ins>ispatching <ins>A</ins>ction (<ins>O</ins>bject-Style) | *prefix: `storeDispatch` / `dao`*

```js
store.dispatch({
  type: 'someAction',
  payload,
});
```

- Vuex <ins>m</ins>ap<ins>A</ins>ctions | *prefix: `ma`*

```js
...mapActions(['some/nested/module/someAction', 'someAction']),
```

- Vuex <ins>m</ins>ap<ins>A</ins>ctions (<ins>n</ins>amespace) | *prefix: `man`*

```js
...mapActions('some/nested/module', ['someAction', 'someOtherAction']),
```

- Vuex <ins>m</ins>ap<ins>A</ins>ctions (<ins>d</ins>ifferent name) | *prefix: `mad`*

```js
...mapActions({
  handler: 'someAction',
}),
```


### Modules

- Vuex <ins>C</ins>reate <ins>M</ins>odules | *prefix: `cm`*

```js
import getters from './getters';
import actions from './actions';
import mutations from './mutations';

const state = () => ({
  property: 'value',
});

export default {
  namespaced: true,
  state,
  getters,
  actions,
  mutations,
};

```

### Plugin

- Vuex <ins>C</ins>reate a <ins>P</ins>lugin | *prefix: `cp`*

```js
const featurePlugin = (store) => {
  store.subscribe((mutation, state) => {
    
  });
};

```

### Component Binding Helpers

- Vuex <ins>c</ins>reate<ins>N</ins>amespaced<ins>H</ins>elpers | *prefix: `cnh` / `helper`*

```js
import { createNamespacedHelpers } from 'vuex';

const { mapState, mapActions } = createNamespacedHelpers('some/nested/module');

```

### Composition API Accessing

- Vuex Composition API <ins>s</ins>etup() <ins>A</ins>ccessing <ins>S</ins>tate | *prefix: `sas`*

```js
const property = computed(() => store.state.property);
```

- Vuex Composition API <ins>s</ins>etup() <ins>A</ins>ccessing <ins>G</ins>etters | *prefix: `sag`*

```js
const property = computed(() => store.getters.property);
```

- Vuex Composition API <ins>s</ins>etup() <ins>A</ins>ccessing <ins>M</ins>utations | *prefix: `sam`*

```js
const mutation = () => store.commit('mutation');
```

- Vuex Composition API <ins>s</ins>etup() <ins>A</ins>ccessing <ins>A</ins>ctions | *prefix: `saa`*

```js
const handler = () => store.dispatch('handler');
```


### Store Instance Methods

- Vuex store subscribe | *prefix: `storeSubscribe`*

```js
const unsubscribe = store.subscribe((mutation, state) => {
  
});
```

- Vuex store subscribeAction | *prefix: `storeSubscribeAction`*

```js
const unsubscribe = store.subscribeAction((action, state) => {
  
});
```

- Vuex store subscribeAction (Object-Style) | *prefix: `storeSubscribeAction`*

```js
const unsubscribe = store.subscribeAction({
  before: (action, state) => {
    
  },
  after: (action, state) => {
    
  },
  error: (action, state, error) => {
    
  }
});
```

- Vuex store replaceState | *prefix: `storeReplaceState`*

```js
store.replaceState(otherState);
```

- Vuex store watch | *prefix: `storeWatch`*

```js
const unwatch = store.watch(
  (state) => state.property,
  (value) => {
    ;
  },
  {
    immediate: true,
    deep: true,
  }
);

```

- Vuex store registerModule | *prefix: `storeRegisterModule`*

```js
store.registerModule('moduleName', {
  state: () => ({}),
  mutations: {},
  actions: {},
  getters: {},
});
```

- Vuex store unregisterModule | *prefix: `storeUnregisterModule`*

```js
store.unregisterModule('moduleName')
```

- Vuex store hasModule | *prefix: `storeHasModule`*

```js
store.hasModule('moduleName')
```

- Vuex store hotUpdate | *prefix: `storeHotUpdate`*

```js
store.hotUpdate({
  
})
```

--EOL--

## License 📃

MIT License

**Donate**

![xianghongai@gmail.com](https://raw.githubusercontent.com/caringrun/assets/master/donate.png)
