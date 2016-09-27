# Swift — Optional Property

## Objectives

1. Use optionals as properties on a class.
2. Print optional properties to observe results.
3. Write a designated initializer for setting an optional property.
4. Write a convenience initializer that passes `nil` into an optional property.

Paste the following code snippets in a new Xcode Playground file to see them in action.

## Optional Properties

Optional properties can be used as part of a class just like other non-optional Types. Any property on a class must have a value assigned to it when it's declared or during the initialization of the class. An exception to this rule is when the property is an optional.

By default optionals have the absence of a value which is referred to as `nil`. This comes in handy when certain properties on a class may or may not ever have a value. For example, a `Student` class could have a property called `middleName` that's declared as an optional. This assumes the application does not **_need_** the middle name for its records. Therefore, when the student record is first created, the user will not be required to provide a middle name (_it_ _will_ _be_ _optional_).

```swift
class Student {

    // Value must be assigned during initialization
    let username: String

    // Optionals
    var firstName: String?
    var lastName: String?
    var email: String?
    var phone: String?

    // Declared with a value
    var gpa: Double = 0.0

    init(username: String) {
        self.username = username
    }

}
```

```swift
// Instance of Student class
let joe = Student(username: "joelovescode")

print("username: \(joe.username)")
print("firstName: \(joe.firstName)")
print("lastName: \(joe.lastName)")
print("email: \(joe.email)")
print("phone: \(joe.phone)")
print("GPA: \(joe.gpa)")
```
This will print:

```
username: joelovescode
firstName: nil
lastName: nil
email: nil
phone: nil
GPA: 0.0
```

If values are assigned to the optional properties, they will remain wrapped and require optional binding to check for a value.

```swift
// Values assigned to optional properties
joe.firstName = "Joe"
joe.lastName = "Burgess"
joe.email = "joe@flatironschool.com"
joe.phone = "212-555-1212"

print("firstName: \(joe.firstName)")
print("lastName: \(joe.lastName)")
print("email: \(joe.email)")
print("phone: \(joe.phone)")
```
This will print:

```
firstName: Optional("Joe")
lastName: Optional("Burgess")
email: Optional("joe@flatironschool.com")
phone: Optional("212-555-1212")
```
Use optional binding to unwrap and assign values to temporary constants.

```swift
// Unwrapped optional properties
if
    let firstName = joe.firstName,
    let lastName = joe.lastName,
    let email = joe.email,
    let phone = joe.phone {

    print("firstName: \(firstName)")
    print("lastName: \(lastName)")
    print("email: \(email)")
    print("phone: \(phone)\n")

}
```
This will print:
```
firstName: Joe
lastName: Burgess
email: joe@flatironschool.com
phone: 212-555-1212
```

### Initializers With Optionals

Even though optional properties are not required for the initialization of a class, they can still be used on initializers. Here's an updated version of the current `Student` class.

```swift
class Student {

    // Value must be assigned during initialization
    let username: String

    // Optionals
    var firstName: String?
    var lastName: String?
    var email: String?
    var phone: String?

    // Declared with a value
    var gpa: Double = 0.0

    // Designated initializer with optionals
    init(username: String, firstName: String?, lastName: String?) {
        self.username = username
        self.firstName = firstName
        self.lastName = lastName
    }

}
```
The original initializer that only took a username argument can now be used as a convenience initializer (Notice that the convenience initializer must include a call to the designated initializer). If multiple initializers seem confusing, remember that they are there to allow for creating instances of class objects under varying circumstances. In the example below the convenience initializer can be used when you know only a username will be provided by the user. 

```swift
class Student {
    
    // Value must be assigned during initialization
    let username: String
    
    // Optionals
    var firstName: String?
    var lastName: String?
    var email: String?
    var phone: String?
    
    // Declared with a value
    var gpa: Double = 0.0
    
    // Designated initializer with optionals
    init(username: String, firstName: String?, lastName: String?) {
        self.username = username
        self.firstName = firstName
        self.lastName = lastName
    }
    
    // Convenience initializer
    convenience init(username: String) {
        self.init(username: username, firstName: nil, lastName: nil)
    }
    
}
```

<a href='https://learn.co/lessons/swift-optional-property' data-visibility='hidden'>View this lesson on Learn.co</a>
