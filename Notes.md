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

 With these classes, let's say the character needs to add a sleep() method:
 
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

	- [ ] 131. OOP vs FP | 4min
	- [ ] 132. OOP vs FP 2 | 5min
- [ ] Section 9: Asynchronous JavaScript 00/011 | 1hr 56min
	- [ ] 133. Section Overview | 5min Resources
	- [ ] 134. Quick Note: Upcoming Videos | 1min
	- [ ] 135. How JavaScript Works | 24min
	- [ ] 136. Promises | 22min
	- [ ] 137. ES8 - Async Await | 15min
	- [ ] 138. ES9 (ES2018) | 5min
	- [ ] 139. ES9 (ES2018) - Async | 11min
	- [ ] 140. Job Queue | 7min Resources
	- [ ] 141. Parallel, Sequence and Race | 10min Resources
	- [ ] 142. ES2020: allSettled() | 4min
	- [ ] 143. Threads, Concurrency and Parallelism | 11min Resources
- [ ] Section 10: Modules In JavaScript 00/07 | 53min
	- [ ] 144. Section Overview | 3min Resources
	- [ ] 145. What Is A Module? | 11min Resources
	- [ ] 146. Module Pattern | 13min
	- [ ] 147. Module Pattern Pros and Cons | 5min
	- [ ] 148. CommonJS, AMD, UMD | 10min
	- [ ] 149. ES6 Modules | 9min Resources
	- [ ] 150. Section Review | 2min
- [ ] Section 11: Error Handling 00/08 | 43min
	- [ ] 151. Section Overview | 1min Resources
	- [ ] 152. Errors In JavaScript | 9min Resources
	- [ ] 153. Try Catch | 10min Resources
	- [ ] 154. Async Error Handling | 13min Resources
	- [ ] 155. Async Error Handling 2 | 4min Resources
	- [ ] 156. Exercise: Error Handling | 1min Resources
	- [ ] 157. Extending Errors | 5min Resources
	- [ ] 158. Section Review | 1min
