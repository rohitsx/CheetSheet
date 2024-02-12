#Importing and Exporting Components
[source](https://react.dev/learn/importing-and-exporting-components)

###Exporting and importing a component step
You can move a component in three steps:

Make a new JS file to put the components in.
Export your function component from that file (using either default or named exports).
Import it in the file where you’ll use the component

eg.

Inside Gallery.js:
export default function Gallery() {
return (
<some code>
);
}

Inside App.js:
import Gallery from './Gallery.js';

export default function App() {
return (
<Gallery />
);
}

note: While importing either './Gallery.js' or './Gallery' will work with React.

###Exporting and importing multiple components from the same file:
A file can only have one default export, but it can have numerous named exports!

exmaple:

Inside Gallery.js:

export function Profile() {
return (
<some code>
);
}

export default function Gallery() {
return (
<some code>
);
}

Inside App.js:

import Gallery from './Gallery.js';
import { Profile } from './Gallery.js';

export default function App() {
return (
<Profile />
);
}

Now you’re using a mix of default and named exports:

Gallery.js:

- Exports the Profile component as a named export called Profile.
- Exports the Gallery component as a default export.
  App.js:
- Imports Profile as a named import called Profile from Gallery.js.
- Imports Gallery as a default import from Gallery.js.
- Exports the root App component as a default export.

note: To reduce the potential confusion between default and named exports, some teams choose to only stick to one style (default or named), or avoid mixing them in a single file.