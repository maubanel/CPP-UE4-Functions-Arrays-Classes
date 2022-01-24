<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Function CPP and BP

<sub>[previous](../) • [home](../README.md#user-content-gms2-top-down-shooter) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

The power in Unreal is to allow programmers to expose elements that can be accessed and viewed and/or changes in blueprints. This is a powerful feature that allows programmers the ability to give designers and others the power to implement custom features made specifically for the game they are working on.

<br>

---


##### `Step 1.`\|`SPCRK`|:small_blue_diamond:

We have the ability to harness the power of Blueprints in our C++ classes in Unreal. Any UACTOR or UOBJECT can have a blueprint version of that class. Go to your **HealthCounter_CPP** file in Unreal and right click it. Select **Create Blueprint class based on HealthCounter_CPP**:

![alt_text](images/BPBasedOnCPP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

 Select the **Blueprints** folder and name it `BP_MyHealthCounter_CPP`.

![alt_text](images/NameBPInheritedCPP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Double click and open `BP_MyHealthCounter_CPP`. Now sometimes the blueprint editor window looks different and there is no graph to add logic. If you ever get this screen you can press the link `Open Full Bueprint Editor`.

![alt_text](images/SmallBPEditor.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Unreal for its existing blueprints does not expose the parents members and functions in the **My Blueprint** menu by default. You need to click on the **Eyeball** button and select **Show Inherited Variables** like so:

![alt_text](images/ShowInheritedVariables.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SPCRK`| :small_orange_diamond:

Click on the **Arrow** that appears next **Variables**. Look for the variables we created. They are not there. We see other variables that are part of the original UACTOR class that we created this from. We need to include a UE4 MACRO with UPROPERTY spedifiers.

![alt_text](images/ClickOnVariablesArrow.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond:

So open **HealthCounter_CPP.h** and add a UPROPERTY macro with some specifiers. A full list of property specifiers can be found on [UE4's website](https://docs.unrealengine.com/en-US/Programming/UnrealArchitecture/Reference/Properties/Specifiers/index.html).

Lets look at the specifiers. The **EditAnywhere** specifier allows the user of the blueprint to edit the value in the property window on any instance of this bluerpint. **BlueprintReadWrite** allows the blueprint to read or write to this variable. The final specifier **Category** allows us to group variables in folders/groups. Press **control b** to build.

![alt_text](images/FirstUProperty.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now go back to the blueprint and check out the variables. We should now see the **Health** variable in the folder called **Player Stats** with the default set in the constructor to `100`:

![alt_text](images/ShowScoreInBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the blueprint change the **Score** default value to `200` and press compile.

![alt_text](images/ChangeDefaultValueTo200.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Create a new room and call it `BP_CPP_ScoreDisplay`. Add the **BP_ScoreCounter_CPP** blueprint to the level and press run. We notice a small problem, the value of the text gets set in the C++ constructor to 100 then gets set after the alarm is called. So we start at 100 and then subtract from 200 when the first alarm is called.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SPCRK`| :large_blue_diamond:

That's an easy fix, open up **HealthCounter_CPP.cpp** and add an update to the Text in the **Begin Play** function like so. Press **control b** to build.

![alt_text](images/FixMiscountdown.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: 

Now run the game and it should start counting down from 200.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

So another variable that is ripe to expose for others to edit is the **DeadText** variable. Open up **ScoreCounter_CPP.h** and add a **UPROPERTY** macro with the same specifiers as we used previously.

![alt_text](images/AdMacroToDeadText.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now the way we have currently written this class we set this variable in **Begin Play** in the CPP. Maybe it is better left to the editor. Lets comment out this assignment in **ScoreCounter_CPP.cpp**. Now build the game with **control b**.

![alt_text](images/DontSetDeadTextInCPP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the blueprint and set the default value to **DeadText** to something different. Press compile.

![alt_text](images/SetNewDeadTextMessage.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: 

Now the message appears in the game window when you run and the score gets to below 0.

![alt_text](images/YaDeadAll.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Just note that it is best practice to make all variables UPROPERTIES but in some rare cases you will not be able to. You can control its access through the specifiers. This helps with garbage collection and freeing up memory in your game. Now we can do the same thing with functions. Now go to the blueprint and right click on the graph and look for the **DoDamage** function. Nothing appears. We need a UFUNCTION marco with specifiers to access functions in blueprints.

![alt_text](images/TryCallingDoDamageFunction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Use the UFUNCTION macro and the specifier **BlueprintCallable** which allows us to access the function in a blueprint. We can also set teh Category. For a full list take a look at UE4's [UFUNCTION specifiers](https://docs.unrealengine.com/en-US/Programming/UnrealArchitecture/Reference/Properties/Specifiers/index.html). Add it to your `.h` file and build the project.

![alt_text](images/BluerintCallableDoDamage.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

 Now go back to the blueprint and right click on the graph and try and add **DoDamage**. Notice that it shows up in the menu:
 
![alt_text](images/DoDamageAppears.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond:

Notice that **DoDamage** node has two input pins (parameters) and a return value. **Target** always shows up so that you can assign the function to antoher object or class. It defaults to self which means that this object is calling the function. OK, next up - lets take a look at **Macros** in C++.

![alt_text](images/DoDamageNodeBP.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>



<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT PAGE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../)| [home](../README.md#user-content-gms2-top-down-shooter) | [next](../)|
|---|---|---|
