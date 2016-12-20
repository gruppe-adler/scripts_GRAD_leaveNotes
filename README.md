# GRAD LeaveNotes

* Enables you to:
  * write notes (ACE-Selfinteraction)
  * place notes on the ground
  * store notes in your (virtual) inventory (ACE-Selfinteraction)
  * read notes
  * destroy notes

GRAD LeaveNotes is multiplayer and JIP proof.

[YOUTUBE VIDEO](https://www.youtube.com/watch?v=RiyfNgn-hQo&feature=youtu.be)


## Dependencies
* [CBA_A3](https://github.com/CBATeam/CBA_A3)
* [ACE3](https://github.com/acemod/ACE3)


## Installation
### Manually
1. Create a folder in your mission root folder and name it `modules`. Then create one inside there and call it `grad-leaveNotes`.
2. Download the contents of this repository ( there's a download link at the side ) and put it into the directory you just created.
3. see step 3 below in the npm part

### Via `npm`
_for details about what npm is and how to use it, look it up on [npmjs.com](https://www.npmjs.com/)_

1. Install package `grad-leaveNotes` : `npm install --save grad-listbuymenu`
2. Prepend your mission's `description.ext` with `#define MODULES_DIRECTORY node_modules`
3. Append the following lines of code to the `description.ext`:

```sqf
#include "node_modules\grad-leaveNotes\grad_leaveNotes.hpp"

class CfgFunctions {
    #include "node_modules\grad-leaveNotes\cfgFunctions.hpp"
};

class CfgSounds {
	sounds[] = {};
    #include "node_modules\grad-leaveNotes\cfgSounds.hpp"
};
```


## Usage
Using the notes system is fairly intuitive. Open up your ACE selfinteraction menu, go to "Equipment", "Notes" and choose "Write Note". A notepad will open up. Write whatever you like, then hit "SAVE" to put the note into your virtual inventory or hit "DROP" to place it on the ground. Use your ACE interaction key to read, pick up or destroy notes on the ground. Use your selfinteraction menu and go to "Equipment", "Notes" again to read, drop or destroy notes in your virtual inventory.

Put this into a player's init box to enable or disable him to write notes (default is true):
`[this, true/false] call GRAD_leaveNotes_fnc_allowWriting;`

Put this into a player's init box to set how many notes he can write (default is 10):
`[this, AMOUNTOFNOTES] call GRAD_leaveNotes_fnc_setAmount;`

Both of these functions can also be called on the server or the player.


## Configuration
You can configure this module in your `description.ext`. This is entirely optional however, since every setting has a default value.

Add the class `GRAD_leaveNotes` to your `description.ext`, then add any of these attributes to configure the module:

| Attribute       | Default Value    | Explanation                                                 |
|-----------------|------------------|-------------------------------------------------------------|
| canWriteDefault | 1                | (1/0) Can everyone write notes by default?                  |
| startAmount     | 10               | (Number) How many notes a player can write by default.      |
| noteObject      | "Land_Notepad_F" | (String) Note object class name.                            |
| actOffset[]     | {0,0,0.1}        | (Array) Note object interaction point offset.               |
| actDist         | 2                | (Number) Note object interaction distance.                  |
| playerDistance  | 1                | (Number) Distance to player at which notes will be dropped. |
