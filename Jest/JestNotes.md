1. Set up
   - install
   ```
    npm i -D jest
   ```
   - or
   ```
    npm i jest --save-dev
   ```
2. Running
   - basic
   ``` json
    "scripts" : {
        "test" : "jest",
    }
   ```
   - showing coverage
   ``` json
    "testCoverage" : "jest --coverage"
   ```
   - auto running if changes
   ``` json
    "testWatch" : "jest --watchAll",
   ```
3. Test sample
   - sample
   ``` js
    const func = require("./func.js")

    test("<TEST_DESCRIPTION>", ()=> {
        expect(func.add(2,2)).toBe(4);
    });
   ```
   - Others
   ``` js
    // not to be
    expect( func(<INPUT>) ).not.toBe(4)

    // to be null
    expect( func(<INPUT>) ).toBeNull()
    
    // truthy falsy
    expect( func(<INPUT>) ).toBeFalsy()
    expect( func(<INPUT>) ).toBeTruthy()

    // less than or greater than
    expect( func(<INPUT>) ).toeLessThanOrEqual()
    expect( func(<INPUT>) ).toeLessThan()

    // Regex
    expect( func(<INPUT>) ).toMatch(/I/)

    // File excites
    expect( func(<INPUT>) ).toBeDefined()

   ```
    - For non primitives or reference types
   ``` js
    expect( func(<INPUT>) ).toEqual({name: "Raazi"});

    expect( func(<INPUT>) ).toContain("admin") // Array ["john", "admin"] will be true
   ```
4. Asynchronous
   ``` js
   // Promise
    test("user data name should be raazi", ()=> {
        expect.assertions(1);

        return func().then(data=>{
            expect(data.name).toEqual("raazi")
        })
    })
   
   // Async await
    test("user data name should be raazi", async ()=> {
        expect.assertions(1);

        const data = await func()
        expect(data.name).toEqual("raazi")
    })
   ```
5. Before each and after each with describe too...
6. Describe
   ``` js
    describe("Checking", ()=> {
        test("user data name should be raazi", ()=> {
            // Tes
        })
    }) 
   ```