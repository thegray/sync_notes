---

Tags : #concept #development #design #pattern
Back Links :
Date : {{31-03-2022}} 08:56

---

# Software Design Pattern
## Creational
### 1. Singleton
### 2. Prototype
Prototype or Clone, is to create object/class from another object to get its functionality.
### 3. Builder
Class have methods to build up object's properties which rather than using constructor.
	Example:
	class Human {
		bool brain = false;
		bool body = false;
		private Human addBrain() {
			this.brain = true;
			return this;
		}
		private Human addBody() {
			this.body = true;
			return this;
		}
	}
### 4. Factory
