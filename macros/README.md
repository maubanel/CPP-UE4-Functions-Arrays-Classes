<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Macros

<sub>[previous](../) • [home](../README.md#user-content-gms2-top-down-shooter) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Macros in C++ are different than Macros in blueprints. We will cover blueprint Macros later. But since we were using macros for UPROPERTY and UFUNCTION it would be good to explain what these are.

A macro is a preprocessor directive that is preceded by a hash sign #. These lines are resolved by the pre processor before the compilation begins.

Lets add a restart so that when the health gets to 0 it resets to a new value (just for testing) 400. We will do this initially by using Macros.

<br>

---


##### `Step 1.`\|`SPCRK`|:small_blue_diamond:

A macro just replaces the text you provide with another value. Go back to the TestFunctions Unreal project and open up **HealthCounter_CPP.h** and add `#define RESETHEALTH 400`. Notice that it is very similar to the preprocessor directive to include other header files. It starts with a `#` pound sign and then it is customary to name all macros with ALLCAPS. The preprocessor will replace the RESETHEALTH with the number 400.

![alt_text](images/DefineResetScore.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

 Lets declare a new function `void ResetHealth()` where we will reset the score to a desired constant value. Lets also make it accessible in blueprints by including the UFUNCTION macro.

![alt_text](images/ResetScoreFunction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now go to the `.ccp` file and add a function definition setting the Health to the macro constant. Then update the display text. Make sure you build the project and make sure there are no compile errors.

![alt_text](images/ChangeScoreToMacro.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now to restart the game we want to call **PlayerIsHit** in a blueprint after the player's health gets to 0. Go back to the `.h` file and add the required macro:

![alt_text](images/MakeHitPlayerCall.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SPCRK`| :small_orange_diamond:

Now open up **BP_HealthCounter_CPP** and add the following logic:

When Health is less or equal to zero then wait 5 seconds, run the **ResetHealth** function, wait another 2 seconds, then run **PlayerIsHit** to start the recursive function again.

![alt_text](images/AddLogicForResetingScore.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond:

We have a bug in our logic. Open up the definition for **PlayerIsHit()** and change the `else` to `if (Health <= 0)`. This is because the previous if catches Health when it is above `0` but then subtracts a random amount. We need to check AGAIN if **Health** is now less than zero.

![alt_text](images/ChangeElseToIf.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Compile the blueprint then run the game. It should start at the value you set in the editor then goes to `400` which is what the MACRO replacement peforms once the score gets to 0.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

 Quit Unreal and reopen the **FunctionTemplayClasses** solution file we created previously. Lets first look at `?` conditional operator. First lets type in an `if` - `else` conditional statement.

![alt_text](images/CPPConsoleAppMacro.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We can replace this multipline if else statement with a single line. We can define a string and we put a `?` after the conditional statement then if the condition is true what is on the right hand of the `?` is used and if false then what is on the right hand side of `:`. So the keyword `if` is replaced with `?` (but placed after the condition) and `else` is replaced with `:`. This allows us to save space and express the condition more concisely.

![alt_text](images/OneLineIfElse.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SPCRK`| :large_blue_diamond:

 Press **F5** to compile and run and you should get the same result as the multiline if else statement.

![alt_text](images/RundSingleLineStatement.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: 

 Lets get back to Macros. Now we can **also** have one line Macro functions. Here is one that returns the larger value of the two passed to it.

![alt_text](images/MacroFunction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

 Lets call this new macro function.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/CallNewMacroFunct.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

When you build and run it you should see it select `7` as the larger number.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/Value7Returns.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Lets do the same thing but pass it two variables instead.

![alt_text](images/UseVariablesCallingMacro.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now build and run it and it works as expected returning an `8`.

![alt_text](images/MacroPassingVariablesRunning.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Many issues can arise with macros as it can unexpected behaviors. For example if you pass an argument with another effect to a Macro you can get unexpected results. Look at the following.

![alt_text](images/FudgingValueInPassedMacro.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Build and run and you expected to see the number `9` didn't you?

![alt_text](images/UnexpectedMacroReturn.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond:

Why did this happen? It took `MAXVAL(++j, ++i)` expands to if `(++j) > (++i) : (++j) : (++i)`. Notice that it runs **++j** anbd **++y** twice with the text replacement. Now Macros are used a lot and certainly used in UE4 but you should avoid using them unless they are necessary. Here are some of the downfalls:

1. There is no scope in namesapce for #define macros. So any file that includes this header will inherit this macro. If it is a common name then it will pick the macro over the local implementation of that variable or function.

2. It is not type safe. So there are no safeguards for using the wrong type.

3. Macros cannot be debugged as they are run by the preprocessor. You can't see what the macro translates to.

4. Macros can have expansion issues like the one we just experienced.




<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT PAGE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../)| [home](../README.md#user-content-gms2-top-down-shooter) | [next](../)|
|---|---|---|
