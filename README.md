Sec3-Lec44 ==> Passing Method References Between Components
=======================================================================
We saw the name/age change on click of the button. Lets say we want this change
on click of below paragraph also (2nd paragraph as below) : 
---------------------------------
I am a Manu and I am 29 years old
-----------------------------------

So we want on click of above para also like on click of button the value changes
i.e Max's name should change to "Maximilian " and Stephanie's age should change to 27

Earlier button and function "switchNameHandler" was in same file App.js so we called it easily but now  they are in different file 
function in App.js and para in Person.js
So here we can pass reference to the handler as a property to the component 
The name of property here is "click" as below


Change in App.js ==> click={this.switc hNameHandler} added
----------------------------------------------------------
<PersonProp 
name={this.state.persons[1].name} 
age={this.state.persons[1].age} 
click={this.switchNameHandler} > My Hobby : Racing</PersonProp>

Change in Person_props.js ==> onClick={props.click} added
---------------------------------------------------------
const personProp = (props) => {
  return (
    <div>
    <p onClick={props.click}> I am a {props.name} and I am { props.age} years old</p>
    <p>{props.children}</p>
    </div>
  )
};



Hence, we can pass method also as props so that we can call a method which might
change the state in another component which doesnot have direct access to state


We may now need to pass value for our handler so "switchNameHandler" should
receive new name so that the hardcoded "Maximilian" gets value dynamically

for this we can use "bind" as in next section

