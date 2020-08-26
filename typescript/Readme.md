# Typescript this is!

## The following is made up of codesnippets and additional information

1. transpile .ts to .js with `$ tsc <file>.ts`
2. execute it e.g. with `$ node <file>.js`
3. remember in js a var is scoped to the nearest function, use let at most

### annotations
```
let a: number;
let b: boolean;
let c: string;
let d: any;
let e: number[] = [1,2,3,4];
let f: any[] = [1,true, 'a', false];
```

### enum
```
enum Color { Red = 0, Green = 1, Blue = 2 };
let backgroundColor = Color.Red;
```

### type assertion
```
let endsWithC = (<string>message).endsWith('c');
let alternativeWay = (message as string).endsWith('c');
```

### arrow function (lambda in other languages)
```
let log = function(message) {
    console.log(message);
}
```
#### can be express as arrow function:
```
let log = (message) => console.log(message);
```

### custom types
#### instead of giving many parameters to that function ...
```
let drawPoint = (x, y, z) => {
    // ...
}
```

#### you could pass an object ...
```
let drawPoint = (point) => {
    // ...
}
```

#### ... which holds the parameters (an object is indicated like {object})
```
drawPoint({
    x: 1,
    y: 2
})
```

#### it gets even better when you pass inline annotation for the types ..
```
let drawPoint = (point: { x: number, y: number }) => {
    // ...
}
```

#### But it would be more oop by unsing an interface which would transform the code to
```
interface Point {
    x: number,
    y: number
}
```

#### now you can annotate it to the Parameter
```
let drawPoint = (point: Point) => {
    // ...
}
```

### object oriented programming style

#### a class ...
```
class Point {

    // constructor with optional variables (just for showing it is possible, makes no sense here)
    // the underscore make the variables to a class property
    constructor(private _x?: number, private _y?: number) {
        // is done automatically here
        //this.x = x;
        //this.y = y;
    }

    // getter, setter ...
    get x() {
        return this._x;
    }

    set x(value) {
        if (value < 0)
            throw new Error('value cannot be less than 0.');
        
        this._x = value;
    }

    draw() {
        console.log('X: ' + this.x + ', Y: ' + this.y);
    }

    getDistance(another: Point) {
        console.log(Math.sqrt(Math.pow((another.x - this.x), 2) + Math.pow((another.y - this.y), 2)));
    }
}

// call object (which is basically the instance of the class, like in every other oop language)
let point = new Point(1, 2);
let anotherPoint = new Point(3, 5);

//use it
point.draw();
point.getDistance(anotherPoint);
```

### modularity
exportabel: variables, functions, classes