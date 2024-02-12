#JavaScript in JSX with Curly Braces

###Passing strings with quotes
When you want to pass a string attribute to JSX, you put it in single or double quotes:

export default function Avatar() {
return (
<img
      className="avatar"
      src="https://i.imgur.com/7vQD0fPs.jpg"
      alt="Gregorio Y. Zara"
    />
);
}

Here, "https://i.imgur.com/7vQD0fPs.jpg" and "Gregorio Y. Zara" are being passed as strings.

But what if you want to dynamically specify the src or alt text? You could use a value from JavaScript by replacing " and " with { and }:

###Where to use curly braces
You can only use curly braces in two ways inside JSX:

- As text directly inside a JSX tag: <h1>{name}'s To Do List</h1> works, but <{tag}>Gregorio Y. Zara's To Do List</{tag}> will not.
- As attributes immediately following the = sign: src={avatar} will read the avatar variable, but src="{avatar}" will pass the string "{avatar}".

###CSS and other objects in JSX
Objects are also denoted with curly braces, like { name: "Hedy Lamarr", inventions: 5 }. Therefore, to pass a JS object in JSX, you must wrap the object in another pair of curly braces: person={{ name: "Hedy Lamarr", inventions: 5 }}.

- You may see this with inline CSS styles in JSX.
<ul style={{
      backgroundColor: 'black',
      color: 'pink'
    }}>

note: Inline style properties are written in camelCase. For example, HTML <ul style="background-color: black"> would be written as <ul style={{ backgroundColor: 'black' }}> in your component.

###Use javascript object effectly:
In this example, the person JavaScript object contains a name string and a theme object:
const person = {
name: 'Gregorio Y. Zara',
theme: {
backgroundColor: 'black',
color: 'pink'
}
};

The component can use these values from person like so:

<div style={person.theme}>
  <h1>{person.name}'s Todos</h1>