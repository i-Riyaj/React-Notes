# Redux-Toolkit

**Redux** is an individual library whereas **react-redux** is an implementation of redux for **connecting react and redux**.

# How to use it?

## create an store

The first step to use **redux-toolkit** is to create a **store**. **Every App usually have one store**.

```
store.js

import { configureStore } from '@reduxjs/toolkit';

export const store = configureStore({
    key: value (could be one or multiple key-value pair)
})
```

## create Slice

In the second step we will create a slice as following,

```
appSlice.js

import { createSlice, nanoid } from '@reduxjs/toolkit';
// nanoid is a method which generates random id

// initial state which the slice needs
const initialState = {
    //say we are making a 'todo app'
    todos: [{id: 1, text: 'hello world'}]
}

export const appSlice = createSlice({
    // here we need three things
    // name
    // initial state
    // list of reducers

    name: 'todo',
    initialState, //initialState : initialState
    reducers: {
        addTodo: (state, action) => {

            // we will always have the access of 'state' & 'action' here.

            // 'state' will always give us the access of the values of intialState at any present time.

            // 'action' will contain the values like id, text etc. More appropriately values which will be passed in reducer fn inside amy component.  

            const todo = {
                id: nanoid(),
                text: action.payload
            }
            state.todos.push(todo);
        },
        removeTodo: (state, action) => {
            state.todos = state.todos.filter(todo => todo.id !== action.payload);
        },
    }
})

export const { addTodo, removeTodo } = appSlice.actions;

export deffault appSlice.reducer;

```

## give access of reducers to store

Now we will go to 'store.js' and will give it the access of list of reducers 

```
store.js

import { configureStore } from '@reduxjs/toolkit';
import appReducer from 'appSlice.js'

export const store = configureStore({
    // key: value (could be one or multiple key-value pair)
    reducer: appReducer
})
```

## useDispatch() and useSelector() 

Now use,
**useDispatch()** to **send** values;
**useSelector()** to **receive/access** values;

for example, 

### useDispatch() 

``` 
addTodo.jsx

// user writes something and presses on add todo button

import { addTodo } //reducer from 'appSlice.js'
import { useDispatch } from 'react-redux';

const [input, setInput] = React.useState('');
const dispatch = useDispatch();

const addTodoHandler = (e) => {
    e.preventDefault();

    // sending input value to addTodo reducer fn
    dispacth(addTodo(input)); 

    setInput('');
}
```

### useSelector() 

```
import { useSelector } from 'react-redux';

// accessing 'todos'
const todos = useSelector(state => state.todos);
```





