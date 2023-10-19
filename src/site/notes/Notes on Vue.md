---
{"dg-publish":true,"permalink":"/notes-on-vue/"}
---

Kebab case in html context, camelCase or PascalCase in JS.

## Slots!

More powerful than react-children. But takes a bit longer to wrap my brain around.

```vue
<slot name="optionalName">Fallback/default goes in here</slot>
```

As a rule of thumb; when you need to pass something that renders, use a slot. Else it's a prop!

## template

```vue
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

```vue
<my-component>
	<p> Defaults to the first slot in my-component</p>
	<template v-slot:second>
		<p>
		Goes in the slot named "second".
		</p>
	</template>
</my-component>
```

Shorthand for v-slot in template is `#`.

And for reference, `MyComponent.vue`  would look something like this:
```vue
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



