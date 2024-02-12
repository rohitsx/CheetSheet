#Rendering Lists (Map and filter):

###Map: basicly it is a loop without condition. the number of the time it render depend on number of elemnt inside array with used.

Here’s a short example of how to generate a list of items from an array:

Move the data into an array:
const people = [
'Creola Katherine Johnson: mathematician',
'Mario José Molina-Pasquel Henríquez: chemist',
<more data>
];

Map the people members into a new array of JSX nodes, listItems:
const listItems = people.map(person => <li>{person}</li>);

Return listItems from your component wrapped in a <ul>:
return <ul>{listItems}</ul>;

###Filtering:This method takes an array of items, passes them through a “test” (a function that returns true or false), and returns a new array of only those items that passed the test (returned true).

example:

const people = [{
id: 0,
name: 'Creola Katherine Johnson',
profession: 'mathematician',
}, {
id: 1,
name: 'Mario José Molina-Pasquel Henríquez',
profession: 'chemist',
}
}];

You only want the items where profession is 'chemist'. The “test” function for this looks like (person) => person.profession === 'chemist'. Here’s how to put it together:

Create a new array of just “chemist” people, chemists, by calling filter() on the people filtering by person.profession === 'chemist':
const chemists = people.filter(person =>
person.profession === 'chemist'
);
Now map over chemists:
const listItems = chemists.map(person =>

  <li>
     <sone code>
  </li>
);
Lastly, return the listItems from your component:

return <ul>{listItems}</ul>;

(
Pitfall
Arrow functions implicitly return the expression right after =>, so you didn’t need a return statement:

const listItems = chemists.map(person =>

  <li>...</li> // Implicit return!
);
However, you must write return explicitly if your => is followed by a { curly brace!

const listItems = chemists.map(person => { // Curly brace
return <li>...</li>;
});
Arrow functions containing => { are said to have a “block body”. They let you write more than a single line of code, but you have to write a return statement yourself. If you forget it, nothing gets returned!
)

###Keeping list items in order with key:
You need to give each array item a key — a string or a number that uniquely identifies it among other items in that array:

<li key={person.id}>...</li>

###Rules of keys
Keys must be unique among siblings. However, it’s okay to use the same keys for JSX nodes in different arrays.
Keys must not change or that defeats their purpose! Don’t generate them while rendering.

###Why does React need keys?
This becomes important if your array items can move (e.g. due to sorting), get inserted, or get deleted. A well-chosen key helps React infer what exactly has happened, and make the correct updates to the DOM tree.
