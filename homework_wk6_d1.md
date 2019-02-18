<!-- Part 1 -->
<!-- this will return print to console: The murderer is Miss Scarlet.
Because: the declareMurderer function is returning the value from the scenario object.murderer  -->
const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Library',
  weapon: 'Rope'
};

const declareMurderer = function() {
  return `The murderer is ${scenario.murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);


<!-- Part 2
This will fail because murderer has been set to a const of 'Professor Plum' so it can't be reset. -->
const murderer = 'Professor Plum';

const changeMurderer = function() {
   murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);

<!-- Part 3
this will return:
First Verdict:  The murderer is Mrs. Peacock.
Second Verdict:  The murderer is Professor Plum.
This is because the firstVerdict uses
murderer = 'Mrs. Peacock' as defined by let murderer in declareMurderer but the secondVerdict uses the variable set out with the scope of the function so returns 'Professor Plum', as set before the function-->
let murderer = 'Professor Plum';

const declareMurderer = function() {
  let murderer = 'Mrs. Peacock';
  return `The murderer is ${murderer}.`;
}

const firstVerdict = declareMurderer();
console.log('First Verdict: ', firstVerdict);

const secondVerdict = `The murderer is ${murderer}.`;
console.log('Second Verdict: ', secondVerdict);


<!-- Part 4
this will return:
The suspects are Miss Scarlet, Professor Plum, Colonel Mustard.
Suspect three is Mrs. Peacock.

This is because within the function suspectThree has been changed to 'Colonel Mustard' but this does not change the value set before the function therefore the value of suspectThree remains as set before, ie Mrs. Peacock; the value was only changed within the scope of the function  -->
let suspectOne = 'Miss Scarlet';
let suspectTwo = 'Professor Plum';
let suspectThree = 'Mrs. Peacock';

const declareAllSuspects = function() {
  let suspectThree = 'Colonel Mustard';
  return `The suspects are ${suspectOne}, ${suspectTwo}, ${suspectThree}.`;
}

const suspects = declareAllSuspects();
console.log(suspects);
console.log(`Suspect three is ${suspectThree}.`);

<!-- Part 5
this will return:
The weapon is the Revolver.

This is because only scenario is set as a constant, the object values can be altered, therefore the value of scenario.weapon can be changed (here from CandleStick to Revolver in changeWeapon - the value is now changed in the object)  -->

const scenario = {
  murderer: 'Miss Scarlet',
  room: 'Kitchen',
  weapon: 'Candle Stick'
};

const changeWeapon = function(newWeapon) {
  scenario.weapon = newWeapon;
}

const declareWeapon = function() {
  return `The weapon is the ${scenario.weapon}.`;
}

changeWeapon('Revolver');
const verdict = declareWeapon();
console.log(verdict);

<!-- Part 6
this will return:
The murderer is Mrs. White.
This is because changeMurderer function calls a function within called plotTwist which resets the value of (global) murderer to Mrs. White. let murderer means the value can be changed
-->
let murderer = 'Colonel Mustard';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    murderer = 'Mrs. White';
  }

  plotTwist();
}

const declareMurderer = function () {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);

<!-- Part 7
this will return:
The murderer is Mr. Green.
The value starts as 'Professor Plum' but this is variable so within the changeMurderer function this is changed:
murderer = 'Mr. Green' has been set as a global variable within the changeMurderer function, all the changes are within the function so they have no effect on the global murderer value set at the start of the function
-->
let murderer = 'Professor Plum';

const changeMurderer = function() {
  murderer = 'Mr. Green';

  const plotTwist = function() {
    let murderer = 'Colonel Mustard';

    const unexpectedOutcome = function() {
      murderer = 'Miss Scarlet';
    }

    unexpectedOutcome();
  }

  plotTwist();
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

changeMurderer();
const verdict = declareMurderer();
console.log(verdict);

<!-- Part 8
this will return:
The weapon is Candle Stick.
initially the murderer is Mrs Peacock in the Dining room
within this function plotTwist is call with 'Dining Room' and then sets the murderer to Colonel Mustard. Within the function unexpectedOutcome is called for Colonel Mustard setting the weapon to Candle Stick
-->
const scenario = {
  murderer: 'Mrs. Peacock',
  room: 'Conservatory',
  weapon: 'Lead Pipe'
};

const changeScenario = function() {
  scenario.murderer = 'Mrs. Peacock';
  scenario.room = 'Dining Room';

  const plotTwist = function(room) {
    if (scenario.room === room) {
      scenario.murderer = 'Colonel Mustard';
    }

    const unexpectedOutcome = function(murderer) {
      if (scenario.murderer === murderer) {
        scenario.weapon = 'Candle Stick';
      }
    }

    unexpectedOutcome('Colonel Mustard');
  }

  plotTwist('Dining Room');
}

const declareWeapon = function() {
  return `The weapon is ${scenario.weapon}.`
}

changeScenario();
const verdict = declareWeapon();
console.log(verdict);

<!-- Part 9
this will return:
The murderer is Professor Plum.
let is only valid within a block so after the if it has no effect therefore the value for murderer remains as the value before the if statement
-->
let murderer = 'Professor Plum';

if (murderer === 'Professor Plum') {
  let murderer = 'Mrs. Peacock';
}

const declareMurderer = function() {
  return `The murderer is ${murderer}.`;
}

const verdict = declareMurderer();
console.log(verdict);
