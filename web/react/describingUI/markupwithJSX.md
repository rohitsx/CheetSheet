#Writing Markup with JSX
[Source](https://react.dev/learn/writing-markup-with-jsx)

JSX: JSX is a syntax extension for JavaScript that lets you write HTML-like markup inside a JavaScript file.

-In React, rendering logic and markup live together in the same place—components.
-React components use a syntax extension called JSX to represent markup. JSX looks a lot like HTML, but it is a bit stricter and can display dynamic information.

Note: JSX and React are two separate things. They’re often used together, but you can use them independently of each other. JSX is a syntax extension, while React is a JavaScript library.

Converting HTML to JSX :

Suppose that you have some (perfectly valid) HTML:

<h1>Hedy Lamarr's Todos</h1>
<img 
  src="https://i.imgur.com/yXOvdOSs.jpg" 
  alt="Hedy Lamarr" 
  class="photo"
>
<ul>
    <li>Invent new traffic lights
    <li>Rehearse a movie scene
    <li>Improve the spectrum technology
</ul>

And you want to put it into your component:

export default function TodoList() {
return (
// ???
)
}
If you copy and paste it as is, it will not work:

export default function TodoList() {
return (
// This doesn't quite work!

<div>
<h1>Hedy Lamarr's Todos</h1>
<img 
      src="https://i.imgur.com/yXOvdOSs.jpg" 
      alt="Hedy Lamarr" 
      class="photo"
    />
<ul>
<li>Invent new traffic lights
<li>Rehearse a movie scene
<li>Improve the spectrum technology
</ul>
</div>
);
}

This is because JSX is stricter and has a few more rules than HTML! If you read the error messages above, they’ll guide you to fix the markup, or you can follow the guide below.

The Rules of JSX :

1. Return a single root element
   To return multiple elements from a component, wrap them with a single parent tag.

For example, you can use a <div>:

<div>
  <multiple line code>
</div>

If you don’t want to add an extra <div> to your markup, you can write <> and </> instead:

<>
<multiple line code>
</>

This empty tag is called a Fragment. Fragments let you group things without leaving any trace in the browser HTML tree.

2. Close all the tags
   JSX requires tags to be explicitly closed: self-closing tags like <img> must become <img />, and wrapping tags like <li>oranges must be written as <li>oranges</li>.

3. camelCase all most of the things!
   JSX turns into JavaScript and attributes written in JSX become keys of JavaScript objects. In your own components, you will often want to read those attributes into variables. But JavaScript has limitations on variable names. For example, their names can’t contain dashes or be reserved words like class.

This is why, in React, many HTML and SVG attributes are written in camelCase. For example, instead of stroke-width you use strokeWidth. Since class is a reserved word, in React you write className instead,