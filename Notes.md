- [ ] Section 8: OOP vs FP 00/03 | 26min
	- [ ] 130. Composition vs Inheritance | 16min
	  - Inheritance tends to focus on a Superclass that is extended to smaller pieces that add or overwrite things
		- Composition tends to focus on smaller pieces to create something bigger
		- Inheritance can have problems that composition solves
		  - Structure of our code
			  - "What it is", What things are
				- Data, methods, actions, and functions that act upon that data
		- Composition
		  - Structure of our code
			 - "What it has", What things do to data

 - With these classes, let's say the character needs to add a sleep() method:

	```javascript
	class Character {
		constructor(name, weapon) {
			this.name = name;
			this.weapon = weapon;
		}
		attack() {
			return 'attack with ' + this.weapon
		}
		sleep() {} // This method is added
	}

	class Elf extends Character {
		constructor(name, weapon, type) {
			super(name, weapon)
			console.log('What am I?', this);
			this.type = type;
		}
	}

	class Ogre extends Character {
		constructor(name, weapon, color) {
			super(name, weapon)
			console.log('What am I?', this);
			this.type = type;
		}
	}
	```

	- All my subclasses that extend from character now have the sleep() method.
	- However, with such "tight coupling", if the addition of the sleep class breaks the subclasses - I've got a problem that ripples down through the subclasses (Potential Fragile Base Class Problem).

	- Potential "Hierarchy Problem": What if I have two different kinds of elves, a "Junior Elf" vs a "Boss Elf". What happens if the Junior Elf gets promoted temporarily? Also, I may want a simple Junior Elf that comes with (an unwanted) giant collection of capabilities from parent classes.

	- If I know that Inheritance can have (Complexity) problems, how do I fix those problems with Composition?
	- Remove all the methods

	```javascript
	function getAttack(character) {
		return Object.assign({}, character, { attackFn () => {} });
	}

	function Elf(name, weapon, type) {
		let elf = {
			name,
			weapon,
			type
		}

		// Add abilities to the elf
		return getAttack(elf)
	}

	// Pseudocode
	Elf  = attack() + sleep()
	Ogre = attack() + sleep() + makeFort()
	```

	- [ ] 132. OOP vs FP 2 | 5min
	  - Key differences
		  - FP: many operations for which the data is fixed
			  - stateless, we don't modify state, state is immutable
				- functions are pure, aim for no side effects
				  - great for parallel computing
			- OOP: few operations on common data
			  - stateful, we are modifying state
				- many side effects
				  - not-great for parallel computing
			- FP and OOP **can** be combined (React Object Example, React FP Example)