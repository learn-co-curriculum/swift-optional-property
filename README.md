# Swift — Optional Property

## Objectives

<<<<<<< HEAD
1. Use optionals as properties.
2. Allow an optional property to be initialized to `nil`.
3. Write a designated initializer for setting an optional property.
4. Write a convenience initializer that passes `nil` into an optional property.


Paste the following code snippets in a new Xcode Playground file to see them in action.

## Optional Properties

Optionals can be used as properties, too, and just like other Types, behave in the same ways that you would expect a loose optional to behave. Unlike non-optional properties, however, optional properties cannot be implicitly typed—they must have a type annotation defining them as an optional—, but they do not require an initial value since they're able to contain `nil`.

An optional property that is not given a default value is automatically initialized to `nil`, allowing those properties to not be covered by initializer. Instead of writing our `Student` class with empty strings as default values:

```swift
//  Student.swift

import Foundation

class Student {
    let username: String
    var firstName = ""
    var lastName = ""
    var email = ""
    var phone = ""
    
    init(username: String) {
        self.username = username
    }
}
```

```swift
let mark = Student(username: "markedwardmurray")
         
print("username: \(mark.username)")
print("firstName: \(mark.firstName)")
print("lastName: \(mark.lastName)")
print("email: \(mark.email)")
print("phone: \(mark.phone)")
```
This will print:

```
username: markedwardmurray
firstName: 
lastName: 
email: 
phone: 
```
We can instead choose to make these optional properties, allowing them to be implicitly initialized to `nil`:

```swift
//  Student.swift

import Foundation

class Student {
    let username: String
    var firstName: String?
    var lastName: String?
    var email: String?
    var phone: String?
    
    init(username: String) {
        self.username = username
    }
}
```

```swift
let mark = Student(username: "markedwardmurray")
         
print("username: \(mark.username)")
print("firstName: \(mark.firstName)")
print("lastName: \(mark.lastName)")
print("email: \(mark.email)")
print("phone: \(mark.phone)")
```
This will print:

```
username: markedwardmurray
firstName: nil
lastName: nil
email: nil
phone: nil
```

However, setting those properties to values of the optional's type will save them as optionals that still need to be unwrapped:

```swift
let mark = Student(username: "markedwardmurray")
mark.firstName = "Mark"
mark.lastName = "Murray"
mark.email = "markymark@funkybun.ch"
mark.phone = "(314) 159-2654"
         
print("username: \(mark.username)")
print("firstName: \(mark.firstName)")
print("lastName: \(mark.lastName)")
print("email: \(mark.email)")
print("phone: \(mark.phone)")
```
This will print:

```
username: markedwardmurray
firstName: Optional("Mark")
lastName: Optional("Murray")
email: Optional("markymark@funkybun.ch")
phone: Optional("(314) 159-2654")
```

### Initializers With Optionals

While the argument types of initializers are defined separately from the properties that they initialize, it's best to keep them synchronized. Optional properties that are covered by initializers should probably accept an optional as well. This is as simple as changing the initializer's argument types to optionals:

```swift
//  Student.swift

import Foundation

class Student {
    let username: String
    var firstName: String?
    var lastName: String?
    var email: String?
    var phone: String?
    
    init(username: String, firstName: String?, lastName: String?) {
        self.username = username
        self.firstName = firstName
        self.lastName = lastName
    }
}
```
We can then set up a convenience initializer that passes in `nil` to the optional arguments on the designated initializer (this is in contrast to passing in an empty string in previous examples without the use of optionals):

```swift
//  Student.swift

import Foundation

class Student {
    let username: String
    var firstName: String?
    var lastName: String?
    var email: String?
    var phone: String?
    
    init(username: String, firstName: String?, lastName: String?) {
        self.username = username
        self.firstName = firstName
        self.lastName = lastName
    }

    convenience init(username: String) {
        self.init(username: username, firstName: nil, lastName: nil)
    }
}
```
=======
## Introduction
<a href='https://learn.co/lessons/swift-optional-property' data-visibility='hidden'>View this lesson on Learn.co</a>
>>>>>>> master
