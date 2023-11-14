# TYPESCRIPT

1. What is typescript
   - Javascript with type checking
   - but it offers a lot more
2. Statically typed language
3. Disadvantages
   - There is always complaining
4. Compiling project
   - for one file
   ```
    tcs index.ts
   ```
   - after setting up rootDir and outDir you can just use
   ```
    tcs
   ```
5. Setting type
   ```ts
   let age: number 20
   ```
6. Configuring TS compiler
   ```
   tcs --init
   ```
   Then you will get a config file with the name `tsconfig.json`
   - compiled JS version
     ```json
     "target": "es2016",
     ```
   - Modules
     ```json
     "module": "commonjs",
     ```
   - Change root directory
     ```json
     "rootDir": "./src ",
     ```
   - Change compiled cod directory
     ```json
     "outDir": "./dist ",
     ```
   - Another useful conf to change
     ```json
     "removeComments": true,
     "noEmitOnError": true,
     "sourceMap": true,
     ```
   - Function related
     ```json
     "noUnusedLocals": true,
     "noUnusedParameters": true,
     "noImplicitReturns": true,
     ```
7. ## Typescript types
   - implicit types an explicit types
   - any type
     - You will lose type case (It's not recommend to use any)
   - unknown
   - never
   - enum
   - tuple
8. Arrays in TS
   ```ts
   let numbers: number[] = [1, 2, 3];
   ```
9. Tuples
   - fixed length array with each having specific types
   ```ts
   let user: [number, string] = [1, "Raazi"];

   // cannot do this: because one is string
   let user: [number, string] = ["one", "Raazi"];
   ```

1.  Enums

    ```ts
    const enum Size { Small = 1, Medium, Large }
    // Medium and large will be set to 2 & 3
    // If there is no value to Small it will we to 0
    ```
    - accessing value
    ```ts
    let mySize: Size = Size.Medium;
    ```
2.  Functions
    - there is auto annotation (recommenced to set it implicitly)
    ``` ts
    function calculateTax(income: number): number {
      return 3
    }
    // here the parameter is number type and return value is also number type
    ```
    - Making a variable optional
    - It's better to use default value because of undefined
    ``` ts
    function calculateTax(income: number, taxYear?: number): number {
      return 3
    }
    // By adding ? the param is optional but the value is undefined
    ```
3.  Objects
    - Normal Object
    ``` ts
    let employee: {
      id: number,
      name: string
    } = {id: 1, name: "Raazi"}
    ```
    - Making a value readonly
    ``` ts
    let employee: {
      readonly id: number,
      name: string
    } = {id: 1, name: "Raazi"}
    
    employee.id = 2 // this will not work
    ```
    - Add Methods to object
    ``` ts
    let employee: {
      readonly id: number,
      name: string, 
      retire : (date: Date) => void;
    } = {
          id: 1, 
          name: "Raazi",
          retire: (date:Date)=> console.log(date)
        }

    ```
3.  Type Alias
    - In Object
    - If we use the above implementation we will have to repeat the type everywhere, so in that case we can use typ alias
    ``` ts
    type Employee = {
      id: number,
      name: string
    };

    let employee: Employee = {id: 1, name: "Raazi"}
    ```
3.  Union Types
    - Params can be different values
    ``` ts
    function kgToLbs (weight: number | string): number {
      if (typeof weight === "number") return weight * 2.2
      else return parseInt(weight) * 2.2
    }

    // these two will work
    kgToLbs(10)
    kgToLbs("10kg")
    ```
4.  Type Intersection
    ``` ts
    type Draggable {
      drag: ()=> void
    }
    type Resizable {
      resize: ()=> void
    }

    type UIWidget = Draggable & Resizable

    // using type intersection
    let textBox: UIwidget = {
      drag: () => {}
      resize: () => {}
    }
    ```
5.  Literal types
    ``` ts
    let quantity: 50 == 50

    // here quantity can only be set to 50
    let quantity: 50 == 51 // this will not work


    // we can combine the union operator to make this useful
    type Quantity = 50 | 100;
    let quantity: Quantity == 100
    ```
6.  Nullable type
7.  Optional property, element, call