<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Functions in Blueprints

<sub>[previous](../) • [home](../README.md#user-content-gms2-top-down-shooter) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Now lets see how to create a function in Blueprints.

<br>

---


##### `Step 1.`\|`SPCRK`|:small_blue_diamond:

Open up the **Epic Games Launcher** program and to to the **Unreal Engine \| Library** tab. Press on the version **4.24.1 Launch** button to start a new project.

![alt_text](images/LaunchNewBuild.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Select the **Blank** template and press **Next**.

Select **Games** from the menu then press the **Next** button.

![alt_text](images/GamesNext.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **Blank** template and press **Next**.

![alt_text](images/BlankTemplateNext.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SPCRK`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Select the **C++** type game in the top left tab. The project needs no starter content, set the quality to whatever is best for your computer and the target should be **Desktop / Console**. Select a directory and call the project `TestFunctions`.

![alt_text](images/CreateTestFunctionsProject.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SPCRK`| :small_orange_diamond:

In the content browser press the **Add New** button and create two new folders, one called `Maps` and the other called `Blueprints`.

![alt_text](images/CreateTwoFolders.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond:

Navigate to the maps folder and press **File \| Save Current** to save the current map and call it `HealthDisplayLevel`.

![alt_text](images/SaveCurrentMap.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Navigate to the **Blueprints** folder. In the **Content Browser** select **Add New \| Blueprint Class** and pick the **Actor** class as we have done previously. Call this new blueprint `BP_HealthCounter`.

![alt_text](images/CreateNewBPActor.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now open this newly created Blueprint and press the **+ Add Component** button and select a **Text Render** component.

![alt_text](images/AddTextRenderComponent.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SPCRK`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Name this component `HealthText` and change the **Text** to `100`. Set the **Text Render Color** to a contrasting color with the sky.

![alt_text](images/ScoreTextConfig.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SPCRK`| :large_blue_diamond:

 Let's create the same function we just did in C++ in a blueprint. Press the **+ Function** button to create a new function and name this new function `DoDamage`.

![alt_text](images/CreateAFunction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: 

This creates a new tab called **Do Damage** and notice that there is a node with the name of the function and an execution pin. When it is called the execution pin will run. Now the parameters we pass to the function are called **Inputs** and the return type is called **Outputs**. Please note that in C++ you can only return one value but in blueprints we can return multiple values.

![alt_text](images/EmptyDoDamageFunctionTab.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Add an output of type **Integer** with the name of `New Health`. Add two inputs called `Damage` and `Health` each of type **Integer**. Notice that a **Return** node is added when you added an **Output** to the function.

![alt_text](images/AddInputsAndOutputs.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Now pull off of the **Health** output pin and select an **Integer - Integer** node. Notice that it has a green **f** next to it which indicates that this is a function as well. It is a built in function that comes with the engine.

![alt_text](images/SelectIntMinusIntNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SPCRK`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Connect the pins making sure that you are deducting **Damage** from **Score** then sending the outut to the **Return Node's New Score** input pin:

![alt_text](images/Connect4Pins.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: 

 Lets go back to the **Event Graph** and right click on the empty graph next to the **Event Tick** and add a **Delay** node:

![alt_text](images/AddDelayNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Change the duration to `2.0` and pull off the **Completed** execution pin and select the **Do Damage** function you just wrote.

![alt_text](images/CallDoDamageFunction.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

 Create a new **Variable** and call it `Health` and make it type **Integer**. Press the **Compile** button and change the **Default Value** to `100`.

![alt_text](images/CreateScoreVariable.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Drag a **Get Health** reference to the graph and connect it to the **Health** input pin in the **DoDamage** function. Add a **Random Integer in Rage** node and set the **Min** to `1` and the **Max** to `5`. Send the **Return Value** to the **Damage** parameter in **Do Damage**.

![alt_text](images/HookUpCallDoDamageParams.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`SPCRK`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Add a **Set Health** reference node and connect its execution pin to **Do Damage** and pipe the **New Health** return value to it's input **Health** pin.

![alt_text](images/SetScoreReference.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond:

Drag a copy of the **Health Text** component to the graph and pull off of its pin to select a **Set Text** node.

![alt_text](images/AddSetScoreTextNode.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Connect execution pin from **Set Score** to **Set Text**. Your node chart should now look like this:

![alt_text](images/FinishCall.jpg)

___

##### `Step 21.`\|`SPCRK`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Go to the game and add the **BP_ScoreCounter** to the scene in front of the player. Press the **Compile** button and run the game. Notice that if you keep running the game it will go below zero. Lets fix that up on the next page.

![alt_text](images/to add.jpg)

___



<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - ADD NEXT PAGE">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../)| [home](../README.md#user-content-gms2-top-down-shooter) | [next](../)|
|---|---|---|
