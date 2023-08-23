Q: _Is this a valid line of javascript code? If it is, what did it do if run?
```
{{{}}}
```
A: Yes it is. These are nested block scopes. Block scopes are created with a paior of curly braces {}

---
Q: *What will the consle output here?*
```
const mystery = 'answer';

const obj = {
p1: 10,
p2: 33,
f1() {},
f2: () => {},
[mystery]: = 42
}

console.log(obj.mystery)
```
A: Undefined. This is because the mystery property was defined with  the dynamic property syntax. In order to obtain the value of the property, you would need to use console.log(obj.answer) since that is the actual name of the property.

---
