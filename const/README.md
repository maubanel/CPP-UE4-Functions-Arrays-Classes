<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Const

<sub>[previous](../) • [home](../README.md#user-content-gms2-top-down-shooter) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Const in C++ cannot be altered by the program and the compiler will give an error if this variable is changed.

Lets open up our previous UE4 project TestFunctions.sh in Visual Studio.

<br>

---


##### `Step 1.`\|`SPCRK`|:small_blue_diamond:

A better solution for the Macro we used for than a Macro for a const which IS scope controlled. So open up our Unreal project again and lets make a small change. Comment out the macro:

![alt_text](images/CommentOutMacro.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Create a new variable called `ResetValue` and initialize it to `6000`. Add a `const` keyword that tells the compiler that this value is a constant and cannot be changed.

![alt_text](images/ResetValueConst.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now open the `.cpp` and change the definition of **ResetHealth** and set **Health** to the new constant **Reset Value**.

![alt_text](images/ResetScoreResetValue.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Compile and run the game and you see that it resets the score to **6000** now when the countdown ends.

![alt_text](images/RunGameWorksAsPrevious.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SPCRK`| :small_orange_diamond:

Now if you try and change the const variable the compiler will exit with an error.

![alt_text](images/TryToChangeConstValue.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>



<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT PAGE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../)| [home](../README.md#user-content-gms2-top-down-shooter) | [next](../)|
|---|---|---|
