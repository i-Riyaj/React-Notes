# Context API

# Syntax

### Context.js File

```
import {createContext, useContext} from 'react'

// creating context
const MyContext = createContext({
property : value,
});

// creating context provider
const ContextProvider = MyContext.Provider;

// this method will let us access values inside a component
const useTheContext = useContext(MyContext);

```

### App component
```
import {ContextProvider} from 'Context.js'

<ContextProvider `value={{property}}`>
    <Component/>
</ContextProvider>

```

### Component 
```
import {useTheContext} from 'Context.js'

const {property} = useTheContext(); 
// Now we have the access of property in this component
```

## Usecase

It helps us to acccess some perticular values which in any component deep down in the tree. For example,

```
<div>
    <div>
        <div>
             <div>
                <h1>{username}</h1>
             </div>
        </div>
    </div>
</div>

To access the 'username' value in 'h1' we have to pass the value of 'username' in each component, like :

<div name={username}>
    <div name={username}>
        <div name={username}>
             <div name={username}>
                <h1>{username}</h1>
             </div>
        </div>
    </div>
</div>

But it's not convenient for us to follow the above step. Istead,
- we can create a 'Context' where we will define the prperties and their values.
And with the help of that 'Context' we can access those values in any component without passing the values in each component.
```

## How to create Context API and use it?

We need to make

- Context
- Context Provider
- useContext(Context), this will help us to access the values of Context API inside a component

It looks like :

```
import { createContext, useContext } from 'react'

// context
export const Context = createContext({property: value});

// context provider
export const ContextProvider = Context.Provider;

// method to access the values inside component
export const useTheContext = useContext(Context);

```

Now, suppose I want the valuse to be accessed throughout the whole app. Then I will rap my 'App' component with 'ContextProvider'. Here's an example :

```
import {ContextProvider}

<ContextProvider _value={{property}_}>
    <div>
        <div>
            <div>
                <div>
                   <h1>value of property is accessible here</h1>
                   <Component/>
                </div>
            </div>
        </div>
    </div>
</ContextProvider>

Now, inside the Component :

import { useTheContext }

const {property} = useTheContext();

now we have the access of property here
```
