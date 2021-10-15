# meh-to-yeah-manually

Thank you for considering me as a potential addition and progressing to the next round. I was glad after I recieved the followup mail right after I applied for the Front End Engineering role @ Manual.

I followed through just as I was asked to in the follow-up mail - answering the questions. But I feel I need to mention that I got carried away,talking about the technicalities 😂 and hence the duration of the recorded video is well over 10 minutes.

Just to be sure that I do not waste any of your valuable time, I decided to append summaries of the technical questions here as well as. 
And while you are at it , you can listen to [experience 🎵](https://www.youtube.com/watch?v=_VONMkKkdf4) - if you will. :D

## Tech Crunch 101

**1. Class Components, bindings, and invoking functions**
![2d64bb116567696db1bc2f7d9363c296](https://user-images.githubusercontent.com/74761990/137496032-2057e2c0-49a3-40c1-a156-99ddbc56515f.png)
- *Click 1 Btn* : even without clicking the btn the handleclick function will get invoked with a global instance and hence as soon as the page loads we will see an alert with MyComponent. Reason being instead of passing a reference to the handleclick function to the eventlistener we are passing the invoked function itself ``` onClick ={this.handleClick()}```. To make it work as expected we need to pass the reference to the handleclick function to the eventlistener like ``` onClick = {this.handleClick}```

- *click 2 btn* : when we click on this btn, we will get an alert with undefined. Which essentially means that the function is being referred to correctly and getting executed as well but it can't read the ```this ``` instance. Reason being, since the handleClick is a method defined outside the constructor function it has lost it's context to the component instance. An easy fix would be to declare a property with the same name inside a constructor and bind it with the component's instance like -> ``` constructor(){
 this.handleClick1 = this.handleClick1.bind(this);
}``` 
after this change the click 2 btn will work just fine and alert with MyComponent, which is just the name property of the component.

- *click 3 btn* : when we click on this button, we will get an alert with MyComponent again. Interesting! Why? Because the click 3 btn has an eventlistener which is refering to a property ``` this.handleClick2``` that is declared inside the constructor and binded with the component instance as well. ``` this.handleClick2 = this.handleClick.bind(this)```

- *click 4 btn* : when we click on this button, we will get an alert saying 'MyComponent'. This is probably the most interestig part about arrow functions and in turn this problem piece as well. Arrow functions work in a slightly different way as compared to traditional functions.
They have a lexical scope - and needs not to be implicitly binded to the constructor to access the component's instance. Therefore upon execution it automatically gets scoped in the constructor. *Decalaring an arrow function inside a class component is technically declaring a property inside the class*

**2. Code Debugging**
