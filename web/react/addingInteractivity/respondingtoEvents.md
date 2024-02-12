#Responding to Events

###Adding event handlers
To add an event handler, you will first define a function and then pass it as a prop to the appropriate JSX tag.

example:
export default function Button() {
function handleClick() {
alert('You clicked me!');
}

return (
<button onClick={handleClick}>
Click me
</button>
);
}

By convention, it is common to name event handlers as handle followed by the event name. You’ll often see onClick={handleClick}, onMouseEnter={handleMouseEnter}

Alternatively, you can define an event handler inline in the JSX:
button onClick={() => {
alert('You clicked me!');
}}>

(

Pitfall

Functions passed to event handlers must be passed, not called. For example:

calling function:

the handleClick function is passed as an onClick event handler. This tells React to remember it and only call your function when the user clicks the button.
<button onClick={handleClick}> (correct)

the () at the end of handleClick() fires the function immediately during rendering, without any clicks. This is because JavaScript inside the JSX { and } executes right away.
<button onClick={handleClick()}> (incorrect)

When you write code inline, you have to be cautious:

wrap it in an anonymous function like so:
<button onClick={() => alert('You clicked me!')}> (correct)

This alert fires when the component renders, not when clicked!
<button onClick={alert('You clicked me!')}> (incorrect)

)

###Event propagation
Event handlers will also catch events from any children your component might have. We say that an event “bubbles” or “propagates” up the tree: it starts with where the event happened, and then goes up the tree.

example in this code:

export default function Toolbar() {
return (

<div className="Toolbar" onClick={() => {
alert('You clicked on the toolbar!');
}}>
<button onClick={() => alert('Playing!')}>
Play Movie
</button>
<button onClick={() => alert('Uploading!')}>
Upload Image
</button>
</div>
);
}

If you click on the "Play Movie" button or the other button you will see alert ("playing") the alert("You clicked on the toolbar!") from the div, so two message will appear.

###Stopping Propagation
Event handlers receive an event object as their argument. By convention, it’s usually called e. You can use this object to read information about the event.

That event object also lets you stop the propagation. To prevent an event from reaching parent components, you need to call e.stopPropagation() like this Button component does:

function Button({ onClick, children }) {
return (
<button onClick={e => {
e.stopPropagation();
onClick();
}}>
{children}
</button>
);
}

export default function Toolbar() {
return (

<div className="Toolbar" onClick={() => {
alert('You clicked on the toolbar!');
}}>
<Button onClick={() => alert('Playing!')}>
Play Movie
</Button>
</div>
);
}

###Passing handlers as alternative to propagation

function Button({ onClick, children }) {
return (
<button onClick={e => {
e.stopPropagation();
onClick();
}}>
{children}
</button>
);
}

Notice, onClick(); one line 107 This pattern provides an alternative to propagation. It lets the child component handle the event, while also letting the parent component specify some additional behavior. Unlike propagation, it’s not automatic. But the benefit of this pattern is that you can clearly follow the whole chain of code that executes as a result of some event.

If you rely on propagation and it’s difficult to trace which handlers execute and why, try this approach instead.

###Preventing default behavior

Some browser events have default behavior associated with them. For example, a <form> submit event, which happens when a button inside of it is clicked, will reload the whole page by default, You can call e.preventDefault() on the event object to stop this from happening:

export default function Signup() {
return (
<form onSubmit={e => {
e.preventDefault();
alert('Submitting!');
}}>
<input />
<button>Send</button>
</form>
);
}

Don’t confuse e.stopPropagation() and e.preventDefault(). They are both useful, but are unrelated:

e.stopPropagation() stops the event handlers attached to the tags above from firing.
e.preventDefault() prevents the default browser behavior for the few events that have it.
