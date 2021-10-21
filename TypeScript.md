# Typescript Language





# Variable Declaration

`let variableName: type`

> Declares the variable name and type. Valid types: string, number, boolean, any, array

>> You should not use the any type if possible

```
let name: string;
let age: number;
let isOld: boolean;
let peoplesNames: string[];

name = "Jeff";
age = 56;
isOld = true;
peoplesNames = ["John", "Jeff", "Bill"];

```
> You can limit a variable so it can accept a limited number of types. This is called a Union Type.

```
let unionType: number | string;

unionType = "string";
unionType = 32;

// the following is unacceptable because it was limited to number or string types when it was declared.
unionType = false;

```



# Functions

```
function cal(val1:number, val2:number): number {
  let total = val1 + val2;
  return total;
}
```
> The type after the function parameter list is the functions return type

`cal(5,7);`

> Returns 12

# Objects

```
let objectName: {property1: string, property2: number} = {
  property1: "string";
  property2: 42;
}
```

# Interfaces

> Interfaces describe the shape of an object. Property or methods that contain a ? character at the end of the name means it is an optional propertye or method. When instantiating an interface object, you must include all of the required properties / methods defined by the interface. You can sub-class the base interface to have more or less properties / methods than the base interface.


```
interface AutomobileInterface{
    brand?: string;
    speed?: number;
    speedMethod?(velocidad: number): void
}

interface AutomobileInterface2 extends AutomobileInterface{
    brand: string;
    speed: number;
}

const automobile2: AutomobileInterface2 = {
    brand: "Porsche",
};

const automobile: AutomobileInterface = {
    brand: "BMW",
    speed: 20,
    speedMethod(){
        console.log(`this ${this.brand} is going at ${this.speed} miles an hour`);
    }
};

function car1(automobile: AutomobileInterface){
    automobile.speed = 500;
    console.log(`this ${automobile.brand} is going at ${automobile.speed} miles an hour`);
}

// car1(automobile);

class AutoMobileClass implements AutomobileInterface{
    brand: string;
    speed: number;
    speedMethod(speed){
        console.log(`Hi my cars is going at ${speed} MPH.`);
    }
}

let carObject = new AutoMobileClass();

carObject.speedMethod(100);

```

# Class

> Classes in TypeScript compile down to JS functions.

```
class Tree {
    constructor(public leaf:string){
        this.leaf = leaf;
    }

    public moveLeaf(){
        console.log(`The ${this.leaf} is moving to the right`);
    }
}

let tree1 = new Tree("Green leaf");
console.log(tree1.leaf);
tree1.moveLeaf();
```

## Class inheritance

```
class Building {
    window: string = "window 1";
    escalators(){
        console.log('The escalators is moving');
    }
}
//
// const building = new Building;
//
// building.escalators();

class Building2 extends Building{
    escalators(){
        console.log(this.window);
    }
}

const building2 = new Building2;
building2.escalators();
```





