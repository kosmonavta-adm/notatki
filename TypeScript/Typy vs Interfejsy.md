- Interfejsy o tej samej nazwie zadeklarowane w jednym bloku zostaną połączone
```TypeScript
interface User {
	name: string;
}

interface User {
	id: string;
}

const user: User = {
	id: "123"
};

// Property 'name' is missing in type '{ id: string; }' but required in type 'User'.
```

- Typy nie mogą zostać ponownie otwarte
```TypeScript
type Window = {
	title: string; 
}   

type Window = {   
	ts: TypeScriptAPI; 
}    

// Error: Duplicate identifier 'Window'.
```

- Interfejsy mogą skorzystać z *extends*, typy nie.
	- Typy cały czas mogą zostać rozszerzone korzystając z *&*
		```TypeScript
		type WithId = { 
			id: string;
		}; 
		type User = WithId & { 
			name: string;
		}; 
		
		const user: User = { 
			id: "123",
			name: "Karl",
			wrongProperty: 123,
		};
		/*
		Type '{ id: string; name: string; wrongProperty: number; }' is not assignable to type 'User'. Object literal may only specify known properties, and 'wrongProperty' does not exist in type 'User'.
		*/	
		```

- Interfejsy nie mogą wyrażać unii oraz zmapowanych i warunkowych typów.

Źródła:
https://www.totaltypescript.com/type-vs-interface-which-should-you-use