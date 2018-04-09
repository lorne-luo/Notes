# React

## Built-in Class methods:

**constructor**
```javascript
constructor(props){
super(props);
}
```

**componentDidMount**

The componentDidMount() hook runs after the component output has been rendered to the DOM

**componentWillUnmount**

run at component is ever removed from the DOM

## Using State Correctly
1. Do Not Modify State Directly, always call setState
2. State Updates May Be Asynchronous

React may batch multiple setState() calls into a single update for performance.you should not rely on their values for calculating the next state.
3. State Updates are Merged

## Handling Events
1. React events are named using camelCase, rather than lowercase.
2. `this` need to be been binded manually, public class fields syntax: `handleClick = () => {}`


# Lists and Keys
* A good rule of thumb is that elements inside the map() call need `key`.

# Froms
* camel case for HTML tag event: onBlur onChange onSubmit
* n React, a `<textarea>` uses a value attribute present the text
