<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Classes

<sub>[previous](../) • [home](../README.md#user-content-gms2-top-down-shooter) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

A class is a user defined type.  It contains members (variables and functions in a class) and we access members with a `object.member` notation.  Lets add a new project by right clicking on the solution file and select **Add \| New Project...**.  Select a **Console App** template and call this new project `BasicClass`. Right click on this new project and select **Set as StartUp Project**.

<br>

---


##### `Step 1.`\|`SPCRK`|:small_blue_diamond:

Lets create a **Card** type.  We will give it two member variables one for the number and the other for the suit.  We declare the class with a name (notice that the curly braces at the end of a class ends with a semi-colon `};`).<br><br>Now add two public member variables one of type **int** and one of type **string**. In Main create a new variable of type **Card** and assign a number and assign a suit.  

![alt_text](images/BasicCardClass.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Notice that we access members of the class through dot notation.  We use the name of the variable that holds an instance of this object and then with `.` access its members.  Compile and run and see that it outputs to two public members of the card:

![alt_text](images/NextCardClass.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

What is the problem here?  The caller can make the suit anything, on top of spades, hearts, diamonds and clubs.  Also, they can make a card `-20` or `3000`.<br><br>We want the private implementation handle the limitations of the class as a card has a fixed set of rules.  Now we control the access to the members through the label `public` and `private`.  The public implementation is the interface and accessible by other objects and the `private` implementation is only accessible through the public interface.<br><br>So lets move `Number` and `Suit` into a `private: ` implementation.  Add two getters a `GetNumber()` and `GetSuit()` inside a public interface. <br><br> Notice that we also have the definition inside the declaration and don't have a separate implementation.  This is common for simple functions like this that run [inline](https://www.geeksforgeeks.org/inline-functions-cpp/).  Now the person calling this class cannot directly alter this class.  So how are we going to set the value?<br><br>This is where the class constructor comes into play.  This is a special function that runs when the class is instantiated.  In this case we will have the caller pass an integer and a float for the card and suit.

![alt_text](images/CardClassPrivateAbstraction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Compile and run and you will notice that we pass the card we want to construct when we create an instance of this class.

![alt_text](images/SetNextCard.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SPCRK`| :small_orange_diamond:

There is a better way of representing both the cards and the suits.  In many games the value of Jack, Queen and King are all 10 with Ace being 1 or 11.  This means that an integer value for the value is not necessarilly a good way of separating a 10 card from a king card.  This is where [enumerators](https://en.cppreference.com/w/cpp/language/enum) come into play.<br><br>It allows us to have a constant value of a distinct type that resticts us to a range of values.  This allows us to use words to represent the meaning of a value in a list. We have a scoped `enum call Card Number` that by default would set the first value to `0`. Since Ace can be worth 1, it makes sense to start the enumerator at `1` instead of its default.  It then sets `Two` to `1`, `Three` to `2` etc...<br><br>We also need to update `GetNumber()` return type from `int` to `CardNumber`.  We also need to change the variable `Number`'s type to `CardNumber`.

![alt_text](images/UseEnumForCard.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond:

Now press compile.  Notice that you get an error when you try and use `cout <<` on `GetNumber()`.  It doesn't recognize the type so it doesn't know what to print.  

![alt_text](images/CardNumberEnumerator.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

 We need to create an operator override before the main() function that defines how to output this type. Any function can be overridden to accept different types of parameters.  This also extends to CPP operators. This allows us to tell the program how the operator should work.  There is nothing restricting our definitions but it is best to keep up with the intent of the operator.  So CardNumber++ should move to the next card and maybe we don't want to override `*` as I am not aware of games where cards multiply two cards for a result (but if it does this is an acceptable override).

![alt_text](images/OverrideOperatorCardNumber.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press compile and run and you should see the card.

![alt_text](images/PrintsOutCard.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now how does this help us with a person who puts in an invalid value when instantiating a **Card** class?  It doesn't.  Lets enter an illegal value like so:

![alt_text](images/AddIllegalNumber.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SPCRK`| :large_blue_diamond:

Compile and woops we get an error. We are crashing in OS and it is not a value that is recognized.  

![alt_text](images/CrashingIllegalValue.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: 

Now we can check for the error in the Card class itself.  Or we can say, hey lets not crash and keep running but make the value clear to the user that is not a valid one.  Lets go with this.  So if the value is greater than **King** and less than **Ace** then it is an **Invalid Card**.

![alt_text](images/AddErrorOutput.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now compile and run again, and the game would continue but the player would know that something is very wrong (not an elegant solution if this was a real card game). Is it better for the game to crash and assert, or communicate a message to the player?  This is something you need to decide.  We will cover error reporting in UE4 later on.

![alt_text](images/InvalidCard.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Lets do the same thing for the suit.  Lets turn it into a class enumerator. Again, because the number starts at `1` we will have the suit start at `1`.

![alt_text](images/AddCardSuit.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now we need to change `Suit` to a **CardSuit** type as well as the return type for `GetSuit()`. We also set it in the class constructor.

![alt_text](images/SetCardSuitEnum.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: 

Now it won't compile as `OS` doesn't know what to do with this type when fed into its output stream.  Just like the previous override we will have a message when the integer is out of range.  This will not crash but print an error message.

![alt_text](images/SuitEnumOverride.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Now pass the appropriate type when instantiating the **Card** class:

![alt_text](images/PassNextCardSuitParameter.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now run and compile and you should get a valid card as the parameters passed are valid.

![alt_text](images/RunWithBothEnums.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now for card number an integer as a value passed makes sense, but I wouldn't know which suit 1 is.  This might not be the best way of instantiatijg this class.  What if the programmer already knows about the **CardSuit** enum.  Wouldn't it be nice to also allow a person to pass both values as enumerators like so:

![alt_text](images/NextCardWithEnumAsParams.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Well we can override any function including the class constructor.  This allows us to allow the programmer to instantiate the class in the way that works best for them. So we can add another consructor where we override the parameters to accept a **CardNumber** and **CartSuit** class enumerator as well.

![alt_text](images/CardOverrideEnumsParams.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond:


We define card and assign the variables passed to the class.

![alt_text](images/DefinitionOfCardToCreateInput.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Now we can instantiate the **Card** class with either integers or the correct enumerators.  Try instantiating the **King** of **Hearts**.

![alt_text](images/ErrorInOutput.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT PAGE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../)| [home](../README.md#user-content-gms2-top-down-shooter) | [next](../)|
|---|---|---|
