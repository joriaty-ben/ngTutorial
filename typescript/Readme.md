1. transpile .ts to .js with tsc <file>.ts
2. execute it e.g. with $ node <file>.js
3. remember in js a var is scoped to the nearest function, use let at most

// annotations
```
let a: number;
let b: boolean;
let c: string;
let d: any;
let e: number[] = [1,2,3,4];
let f: any[] = [1,true, 'a', false];
```

// enum
```
enum Color { Red = 0, Green = 1, Blue = 2 };
let backgroundColor = Color.Red;
```

// type assertion
```
let endsWithC = (<string>message).endsWith('c');
let alternativeWay = (message as string).endsWith('c');
```

// arrow function (lambda in other languages)
```
let log = function(message) {
    console.log(message);
}
```
//can be express as arrow function:
```
let log = (message) => console.log(message);
```

//custom types