1. Why do we write `onPress={handlePress}` and not `onPress={handlePress()}`?

In Javascript as I know for a course, when we use a () in {}, we are calling immediately that function when we render the component, also it passes its result, that could be 'undefined', so, passing it without (), (like a reference), is like we are telling react to save that function and call it when is pressed by the user

2. What is the difference between `Button` and `Pressable`? When would you choose each one?

Button is a native component of the system, it doesn't allow customizations, only accept 'title', 'color', and 'onpress'.
Pressable can wrap any children and allows fully control on design.
Personally, I would use Button if i need something quick and standard action, like the share profile of the activity, Pressable i would use it for something with custom design, like the Follow and Message as well.


3. What does the `style` function of `Pressable` receive and what does it return? Give an example.

It receives an object with the current state of the interaction, in this one, we destructured it and got the pressed property, and it returns an object or styles array to apply at that moment.
An example could be the step that we made and you gave us in the tutorial
style={({ pressed }) => [styles.button, pressed && styles.pressed]}
if pressed is true, it makes the button semi transparent, if its false, nothing happens

4. Why can you not change a state variable directly (`isFollowing = true`) and what do you do instead?

Is a principle of React, if you change the variable directly, React doesn't know that something changed, so it doesn't re-render the component and the new value is lost in the next render. Instead, we need to use the setter function that we declare at the useState moment, like 'setIsFollowing(!isFollowing)' to change the state of following. If we do that, when we use the setter we are telling React to update the state and draw the screen again

5. Why is `followers` not a second `useState`? What is a *derived value*?

We doesn't use a second state to avoid desyncronizations, like, the button says following but the following count hasn't increased. 
A derived value is a variable that can be calculated from an existing state or props in every render. In this task, we did it on the BASE_FOLLOWERS, where we are increasing 1 or 0 if is true or false the state of isFollowing


6. What does *controlled input* mean for `TextInput`? Which two props make it controlled?

Controlled input means that the text showed in the screen comes from a state of React, so the state is the only source.
The two props that make it controlled are 'value', which it reads the state, and onChangeText, which is the one that updates the state on every keystroke. So, this makes it easy to use text elsewhere.


7. Why is `selectedSkills.push(skill)` wrong when `selectedSkills` is state? Write the correct code.

Is like the answer of the question 4, it mutates the same array that React is holding already, breaking the rules and principles of immutability of React, making React can't detect the update or re-render.
The correct code to add a skill is:

 setSelectedSkills([...selectedSkills, skill]);

and to remove it is:

 setSelectedSkills(selectedSkills.filter((item) => item !== skill));