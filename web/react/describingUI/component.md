#Intro to the component ##[source](https://react.dev/learn/your-first-component)

###Component: React applications are built from isolated pieces of UI called components. A React component is a JavaScript function that you can sprinkle with markup.

###To export the compoent:
export default function Profile() {
return (
<img
      src="https://i.imgur.com/MK3eW3Am.jpg"
      alt="Katherine Johnson"
    />
)
}

###retrun statement:
Return statements can be written all on one line, as in this component:
return <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />;

But if your markup isn’t all on the same line as the return keyword, you must wrap it in a pair of parentheses:
return (

  <div>
    <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
  </div>
);

###Lowercase And Uppercase in component:
Notice the difference in casing:

<section> is lowercase, so React knows we refer to an HTML tag.
<Profile /> starts with a capital P, so React knows that we want to use our component called Profile.
And Profile contains even more HTML: <img />. In the end, this is what the browser sees:

<section>
  <h1>Amazing scientists</h1>
  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
  <img src="https://i.imgur.com/MK3eW3As.jpg" alt="Katherine Johnson" />
</section>

###Slow renderning in Component:

Components can render other components, but you must never nest their definitions:

export default function Gallery() {
// 🔴 Never define a component inside another component!
function Profile() {
// ...
}
// ...
}

The snippet above is very slow and causes bugs. Instead, define every component at the top level:
export default function Gallery() {
// ...
}

// ✅ Declare components at the top level
function Profile() {
// ...
}
When a child component needs some data from a parent, pass it by props instead of nesting definitions.