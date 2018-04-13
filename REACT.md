# React

Docs: https://reactjs.org/docs/hello-world.html

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
* `<textarea>` uses `value` attribute present the text
```html
<textarea value={this.state.value} onChange={this.handleChange} />
```
* `<select` uses `value` attribute on the root select tag to specify selected.
```html
<select value={this.state.value} onChange={this.handleChange}>
    <option value="grapefruit">Grapefruit</option>
</select>
```
* `<input type="file" />` is uncontrolled component
* use `event.target.name` to handle multiple inputs
```html
<input name="isGoing" type="checkbox" checked={this.state.isGoing} onChange={this.handleInputChange} />

handleInputChange(event) {
    const target = event.target;
    const value = target.type === 'checkbox' ? target.checked : target.value;
    const name = target.name;

    this.setState({
      [name]: value  //ES6 computed property name 
    });
  }
```

# Lifting State Up
In React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it

# Composition and  Containment
use the special children prop to pass children elements directly into their output
```javascript
function FancyBorder(props) {
  return (
    <div className={'FancyBorder FancyBorder-' + props.color}>
      {props.children} // output <h1>Welcome</h1>
    </div>
  );
}


function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1>Welcome</h1>
    </FancyBorder>
  );
}
```

# Specialization
```javascript
function Dialog(props) {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        {props.title}
      </h1>
      <p className="Dialog-message">
        {props.message}
      </p>
    </FancyBorder>
  );
}

function WelcomeDialog() {
  return (
    <Dialog
      title="Welcome"
      message="Thank you for visiting our spacecraft!" />
  );
}
```

# JSX in Depth
* JavaScript Expressions as Children, You can pass any JavaScript expression as children, by enclosing it within {}
```javascript
<MyComponent>{'foo'}</MyComponent>
```
* props children can be a function
* Booleans, Null, and Undefined Are Ignored: false, null, undefined,(0 will be printed) and true are valid children. They simply don’t render. Useful to conditionally render.
```javascript
<div>
  {showHeader && <Header />}
</div>
```
* Convert false, true, null, or undefined to string to print: `<div>{String(myVariable)}<div>`
* Use `prop-types` can validate prop type

# Callback Ref
* When to Use Refs
  1. Managing focus, text selection, or media playback.
  2. Triggering imperative animations.
  3. Integrating with third-party DOM libraries.
* If the ref callback is defined as an inline function, it will get called twice during updates, first with null and then again with the DOM element.

