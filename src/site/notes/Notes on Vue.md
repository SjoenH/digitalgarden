---
{"dg-publish":true,"permalink":"/notes-on-vue/"}
---

# Notes on Vue
#vue #learning #notes

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

[See example code-playground here](https://play.vuejs.org/#eNqlUstO4zAU/ZU73mRGgmTBrlOQ5oHmIfEQILHxJkpuWoNjW/ZNKar671w7TRoQICF29j0PH9tnI344l686FDMxD5VXjiAgde5EGtU66wk24LGBLTTetpAxNRuhs8dfllcGDe3gvJjMom/2XZrJSBppKmsCQRsWcBytv2Z/UWsLt9br+kv2TZp50SfhDLwhbJ0uCXkHMG8fD6vBLE145k7gNzZlpykAWaAlQqM8nxG0JVAGpqJ5Ee+WdIMzrA4jcxaQo9U7NPkOS4A/FkO0iubJ1pQt1iBFL5IiH2X7A4rn2YsX4Se4OBAU2KhRi/wuWMPfsYkaKaJAafQXjhQ/nBQzSEjESn63h/9pRr7Dg2FeLbG6f2V+F9ZxJsWlx4B+hVKMGJV+gdTDp9fnuOb1CLa27jSz3wGvMFjdxYw97Wdnao494aW0/1JzlFnchNM1oQnDpWLQyNwmvhTcndiat66+j3uUHyWdNFt+xRf1+1itP9nN2Ivd159bWvIlwXm7UjUXhauTasPJ+i6M5CRLdTret+kNm2fSaX22T5uXRPw=) 

