# 🐣 Object Oriented Programming Template

- [🐣 Object Oriented Programming Template](#-object-oriented-programming-template)
  - [🔑 Key Words](#-key-words)
  - [👀 Fast Lookup](#-fast-lookup)
  - [JavaScript OOP Template](#javascript-oop-template)
  - [TypeScript OOP Template](#typescript-oop-template)

## 🔑 Key Words

## 👀 Fast Lookup

- **In JavaScript**
  - No access modifiers like `public`, `private`, `protected`.

## JavaScript OOP Template

```javascript
class Person {
  /**
   * Creates an instance of a class with a name and age.
   * @constructor
   * @param {string} name - The name of the person.
   * @param {number} age - The age of the person.
   */
  constructor(name, age) {
    // "_" is a convention to indicate that the property is private.
    this._name = name;
    this._age = age;
  }

  /**
   * Gets the person's name.
   * @returns {string} The name of the person.
   */
  get name() {
    return this._name;
  }

  /**
   * Sets the person's name.
   * @param {string} name - The new name to assign.
   */
  set name(newName) {
    if (typeof newName !== "string") {
      throw new Error("Name must be a string");
    }
    this._name = newName;
  }

  /**
   * Gets the person's age.
   * @returns {number} The age of the person.
   */
  get age() {
    return this._age;
  }

  /**
   * Sets the person's age.
   * @param {number} newAge - The new age to assign.
   */
  set age(newAge) {
    if (typeof age !== "number" || newAge < 0) {
      throw new Error("Invalid age");
    }
    this._age = newAge;
  }

  /**
   * Displays a greeting message.
   * @return {string}
   */
  greet() {
    return `Hello! My name is ${this._name}, and I am ${this._age} years old.`;
  }

  /**
   * A static method to check adulthood by age threshold.
   * @param {number} age - The age to check.
   * @return {boolean} Whether the age is considered adult or not.
   */
  static isAdult(age) {
    const ADULT_AGE = 18;
    return age >= ADULT_AGE;
  }
  // Static methods are called on the class itself, not on an instance.
}

/**
 * Represents a student who inherits from Person.
 */
class Student extends Person {
  /**
   * @constructor
   * @param {string} name - The name of the student.
   * @param {number} age - The age of the student.
   * @param {string} major - The major subject.
   */
  constructor(name, age, major) {
    // Call the parent class constructor
    super(name, age);
    this._major = major;
  }

  /**
   * Gets the student's major.
   * @return {string} The student's major.
   */
  get major() {
    return this._major;
  }

  /**
   * Sets the student's major.
   * @param {string} newMajor - The new major to assign.
   */
  set major(newMajor) {
    if (typeof newMajor !== "string") {
      throw new Error("Major must be a string");
    }
    this._major = newMajor;
  }

  /**
   * Prints a studying message.
   * @return {string}
   */
  study() {
    return `${this._name} is studying ${this._major}.`;
  }
}

```

## TypeScript OOP Template

```typescript
class Person {
  private _name: string;
  private _age: number;

  constructor(name: string, age: number) {
    this._name = name;
    this._age = age;
  }

  public get name(): string {
    return this._name;
  }

  public set name(newName: string) {
    this._name = newName;
  }

  public get age(): number {
    return this._age;
  }

  public set age(newAge: number) {
    this._age = newAge;
  }

  public greet(): string {
    return `Hello! My name is ${this._name}, and I am ${this._age} years old.`;
  }

  public static isAdult(age: number): boolean {
    const ADULT_AGE = 18;
    return age >= ADULT_AGE;
  }
}

class Student extends Person {
  private _major: string;

  constructor(name: string, age: number, major: string) {
    super(name, age);
    this._major = major;
  }

  public get major(): string {
    return this._major;
  }

  public set major(newMajor: string) {
    this._major = newMajor;
  }

  public study(): string {
    return `${this.name} is studying ${this._major}.`;
  }
}

```


[🔙 Back to the main page](./README)
