- State variables might look like regular JavaScript variables that you can read and write to. However, state behaves more like a snapshot. Setting it does not change the state variable you already have, but instead triggers a re-render.

### Setting state triggers renders

import { useState } from 'react';

export default function Form() {
const [isSent, setIsSent] = useState(false);
const [message, setMessage] = useState('Hi!');
if (isSent) {
return <h1>Your message is on its way!</h1>
}
return (

<form onSubmit={(e) => {
e.preventDefault();
setIsSent(true);
sendMessage(message);
}}>
<textarea
placeholder="Message"
value={message}
onChange={e => setMessage(e.target.value)}
/>
<button type="submit">Send</button>
</form>
);
}

Here’s what happens when you click the button:

- The onSubmit event handler executes.
- setIsSent(true) sets isSent to true and queues a new render.
- React re-renders the component according to the new isSent value.

### Rendering takes a snapshot in time

When React re-renders a component:

- React calls your function again.
- Your function returns a new JSX snapshot.
- React then updates the screen to match the snapshot your function returned.

In this code when you click the “+3” button, number only increments once per click!

import { useState } from 'react';

export default function Counter() {
const [number, setNumber] = useState(0);

return (
<>

<h1>{number}</h1>
<button onClick={() => {
setNumber(number + 1);
setNumber(number + 1);
setNumber(number + 1);
}}>+3</button>
</>
)
}

Setting state only changes it for the next render. During the first render, number was 0. This is why, in that render’s onClick handler, the value of number is still 0 even after setNumber(number + 1) was called.

Here is what this button’s click handler tells React to do:

1. setNumber(number + 1): number is 0 so setNumber(0 + 1).

- React prepares to change number to 1 on the next render.

2. setNumber(number + 1): number is 0 so setNumber(0 + 1).

- React prepares to change number to 1 on the next render.

3. setNumber(number + 1): number is 0 so setNumber(0 + 1).

- React prepares to change number to 1 on the next render.

You can also visualize this by mentally substituting state variables with their values in your code. Since the number state variable is 0 for this render, its event handler looks like this:

<button onClick={() => {
setNumber(0 + 1);
setNumber(0 + 1);
setNumber(0 + 1);
}}>+3</button>

For the next render, number is 1, so that render’s click handler looks like this:

<button onClick={() => {
setNumber(1 + 1);
setNumber(1 + 1);
setNumber(1 + 1);
}}>+3</button>

This is why clicking the button again will set the counter to 2, then to 3 on the next click, and so on.
