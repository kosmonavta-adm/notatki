Żeby móc skorzystać z destrukturyzacji w funkcji *map* tablica powinna posiadać odpowiedni typ, wtedy wartość przekazywana do map, nie będzie oznaczona jako *any*.

```jsx
type CollectionItem = {
	title: string,
	createdAt: string,
	itemsCount: number,
	description: string
}

  const x: CollectionItem = {
	  createdAt: '2011-10-05T14:48:00.000Z', 
	  title: 'test', 
	  description: 'test', 
	  itemsCount: 2,
  };

{
	Array<CollectionItem>(100).fill(x).map((item) => (
		<CollectionItem { ...item } />
	))
}
```
