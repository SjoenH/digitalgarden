---
{"dg-publish":true,"permalink":"/vue/"}
---

# Watch
For running side-effects. We can watch some state and do something whenever it changes.

```tsx
const question = ref('')
watch(question, async (newQeustion, oldQuestion)=>{
	// Note that we have access to the new value as well as the old one. That's pretty sick!
})
```

So that means we can have a quite intuitive way to work with a store.
Like... 
```tsx
watch(()=>productStore.get.starredProducts(),
	(starredProducts) => {
		 // do something
	}
)
```


This will run every time the `productStore.get.starredProducts()` changes. 

**NB: But not on mount!** Unless we set it to run immediately like this:
```tsx
watch(()=>productStore.get.starredProducts(),
	(starredProducts) => {
		 // do something
	},
	{immediate: true}
)
```

This gives us some more fine-control over the lifecycle... Which is nice.
