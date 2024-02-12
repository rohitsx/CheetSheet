#State: A Component's Memory

###When a regular variable isn’t enough

export defult function gallery(){
let Index = 0;

    function handelClick(){
        Index = Index+1;
    }

    return <p onClick={handelClick}>Value of h1 = {Index}</p>

}

The handleClick event handler is updating a local variable, index. But two things prevent that change from being visible:

- Local variables don’t persist between renders: When React renders this component a second time, it renders it from scratch—it doesn’t consider any changes to the local variables.
- Changes to local variables won’t trigger renders: React doesn’t realize it needs to render the component again with the new data.

###Meet your first Hook

Hook: In React, useState, as well as any other function starting with “use”, is called a Hook.

(
Pitfall

Hooks—functions starting with use—can only be called at the top level of your components or your own Hooks. You can’t call Hooks inside conditions, loops, or other nested functions. Hooks are functions, but it’s helpful to think of them as unconditional declarations about your component’s needs. You “use” React features at the top of your component similar to how you “import” modules at the top of your file.
)

Every time your component renders, useState gives you an array containing two values:

- The state variable (index) with the value you stored.
- The state setter function (setIndex) which can update the state variable and trigger React to render the component again.

Here’s how that happens in action:

import react, {useSate} from 'react';

export defult function example(){
let [Index, setIndex] = useState(0);

    function addValue(){
        setIndex(Index+1);
    }

    return <p onClick={addValue}>value of index is {Index}</p>

}

- Your component renders the first time. Because you passed 0 to useState as the initial value for index, it will return [0, setIndex]. React remembers 0 is the latest state value.
- You update the state. When a user clicks the button, it calls setIndex(index + 1). index is 0, so it’s setIndex(1). This tells React to remember index is 1 now and triggers another render.
- Your component’s second render. React still sees useState(0), but because React remembers that you set index to 1, it returns [1, setIndex] instead.


###State is isolated and private 
State is local to a component instance on the screen. In other words, if you render the same component twice, each copy will have completely isolated state! Changing one of them will not affect the other.