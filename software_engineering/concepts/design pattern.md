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
Function that can determine which object to create or instantiate
class VehicleFactory{
	createVehicle(string type) {
		if (type === "car") {
			return new CreateCar();
		} else {
			return new CreateOther();
		}
	}
}
### 5. Facade
Wrap components or functions to another function to the small detail.

### 6. Proxy / Substitute
Create object from original one to handle various operation.

### 7. Iterator
Add iterate functionality to a collection.

### 8. Observer
Callback to subscriber

### 9. Mediator
Middleware to control every components.

### 10. State
Create states of an object that determine object's behaviour.