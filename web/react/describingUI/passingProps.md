#Passing Props to a Component

Props: Props are the information that you pass to a JSX tag. For example, className, src, alt, width, and height are some of the props you can pass to an <img>:

function Avatar() {
return (
<img <some code> />
);
}

export default function Profile() {
return (
<Avatar />
);
}

The props you can pass to an <img> tag are predefined (ReactDOM conforms to the HTML standard). But you can pass any props to your own components, such as <Avatar>, to customize them. Here’s how!

In this code, the Profile component isn’t passing any props to its child component, Avatar:

export default function Profile() {
return (
<Avatar />
);
}
You can give Avatar some props in two steps.

Don’t miss the pair of { and } curlies inside of ( and ) when declaring props:

function Avatar({ person, size }) {
// ...
}
This syntax is called “destructuring” and is equivalent to reading properties from a function parameter:

function Avatar(props) {
let person = props.person;
let size = props.size;
// ...
}

###Specifying a default value for a prop
If you want to give a prop a default value to fall back on when no value is specified, you can do it with the destructuring by putting = and the default value right after the parameter:

function Avatar({ person, size = 100 }) {
// ...
}
Now, if <Avatar person={...} /> is rendered with no size prop, the size will be set to 100.

The default value is only used if the size prop is missing or if you pass size={undefined}. But if you pass size={null} or size={0}, the default value will not be used.

###Forwarding props with the JSX spread syntax

If you want to pass props to a component lazest way try this:

const props = { person: 'John', size: 'medium', isSepia: false, thickBorder: true };

// Using spread syntax in JSX
<Avatar {...props} />;

This forwards all of props to the Avatar without listing each of their names.

Note: Use spread syntax with restraint. If you’re using it in every other component, something is wrong. Often, it indicates that you should split your components and pass children as JSX. More on that next!

###Passing JSX as children

It is common to nest built-in browser tags:

<div>
  <img />
</div>

Sometimes you’ll want to nest your own components the same way:
<Card>
<Avatar />
</Card>

You can think of a component with a children prop as having a “hole” that can be “filled in” by its parent components with arbitrary JSX. You will often use the children prop for visual wrappers: panels, grids, etc.

note: Don’t try to “change props”. When you need to respond to the user input (like changing the selected color), you will need to “set state”