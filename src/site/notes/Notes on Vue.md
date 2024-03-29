---
{"dg-publish":true,"permalink":"/notes-on-vue/"}
---

# Notes on Vue
#vue #learning #notes

Kebab case in html context, camelCase or PascalCase in JS.
Consistency is key.

## Slots!

More powerful than react-children. But takes a bit longer to wrap my brain around.

```tsx
<slot name="optionalName">Fallback / default goes in here </slot>
```

As a rule of thumb; when you need to pass something that renders, use a slot. Else it's a prop!

## template

```tsx
<template>
	Used for grouping things without rendering a div or span.
</template>

<p>The paragraphs under will show and hide together</p>
<template v-if="someBool">
	<p>item one</p>
	<p>item two</p>
</template>

<p>If true, it will render like this:</p>

<p>item one</p>
<p>item two</p>

```

### template v-slot

template supports the `v-slot` directive. That means that all that goes into the template will be directed to the `v-slot:destination`.

For example:

We have a component that is using the slot of some other component:

```tsx
<my-component>
	<p> Defaults to the first slot in my-component</p>
	<template v-slot:second>
		<p>
		Goes in the slot named "second".
		</p>
	</template>
</my-component>
```

And for reference, `MyComponent.vue`  would look something like this:
```tsx
<template>
	<slot>
		Nothing provided in slot one
	</slot>
	<slot name="second">
		Nothing provided
	</slot>
</template>
```

And would render as:

```html
<p>Defaults to the first slot in my-component</p>
<p>Goes in the slot named "second".</p>
```

[See example code-playground here](https://play.vuejs.org/#eNp9UstuwjAQ/JWVL1wgOXCjFKkPVLVSadX26EuULGCa2Ja9oSDEv3ftEAio9LbemVmPPbsTd9Ym6xrFSIx97pQl8Ei1nUitKmscwev2wXClURPMnamgl6SdXhD3bqQep42chXwgrGyZEfIJYFxtB3nLjx3u2Qk84jyrS/JABmiJMFfO8/WlIVAauqJxGgxFXTsZ1oPAHHnMjS4OaJzblgBPBn0YFYbHsTqrsAApGpEUyVF2uiA9955emO/goi/I86C5WiQrbzT/4S5opAgCVaJ7s6SM9lKMICIBy8rS/LzEHrka+20/X2L+/Ud/5TehJ8W7Q49ujVIcMcrcAqmBp58z3HB9BCtT1CWz/wE/0JuyDh4b2n2tC7bd4UW3z3ETlF58+emGUPv2UcFoYO4jXwrehbAY155+sjtMhlEn9Z5/8WKdwi6ehxDCO+QzM7RkJ2CdWauC0+R8Y7YsbwI7kqMsZn57ivzKmDNpN+P9L6+PCjU=) 


> Shorthand for v-slot in template is `#`. So `v-slot:second` could be rewritten as `#second`


### Back-and-fourth

```vue
<template v-slot="providedItem">
 {{providedItem}}
</template>
```

# Watch

> For running side-effects. 

We can watch some state and do something whenever it changes.

```ts
const question = ref('')
watch(question, async (newQeustion, oldQuestion)=>{
	// Note that we have access to the new value as well as the old one. That's pretty sick!
})
```

So that means we can have a quite intuitive way to work with a store.
Like... 
```ts
watch(()=>productStore.get.starredProducts(),
	(starredProducts) => {
		 // do something
	}
)
```


This will run every time the `productStore.get.starredProducts()` changes. 

**NB: But not on mount!** Unless we set it to run immediately like this:
```ts
watch(()=>productStore.get.starredProducts(),
	(starredProducts) => {
		 // do something
	},
	{immediate: true}
)
```

This gives us some more fine-control over the lifecycle... Which is nice.
