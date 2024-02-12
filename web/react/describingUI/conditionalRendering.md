#Conditional (ternary) operator (? :):

Instead of this:
if (isPacked) {
return <li className="item">{name} ✔</li>;
}
return <li className="item">{name}</li>;

You can write this:
return (

  <li className="item">
    {isPacked ? name + ' ✔' : name}
  </li>
);
You can read it as “if isPacked is true, then (?) render name + ' ✔', otherwise (:) render name”.

Now let’s say you want to wrap the completed item’s text into another HTML tag:

 <li className="item">
      {isPacked ? (
        <del>
          {name + ' ✔'}
        </del>
      ) : (
        name
      )}
    </li>

###Logical AND operator (&&):
when the condition is true, or render nothing otherwise. With &&, you could conditionally render the checkmark only if isPacked is true:

return (

  <li className="item">
    {name} {isPacked && '✔'}
  </li>
);
You can read this as “if isPacked, then (&&) render the checkmark, otherwise, render nothing”.

(Pitfall
Don’t put numbers on the left side of &&.

To test the condition, JavaScript converts the left side to a boolean automatically. However, if the left side is 0, then the whole expression gets that value (0), and React will happily render 0 rather than nothing.

For example, a common mistake is to write code like messageCount && <p>New messages</p>. It’s easy to assume that it renders nothing when messageCount is 0, but it really renders the 0 itself!

To fix it, make the left side a boolean: messageCount > 0 && <p>New messages</p>.
)