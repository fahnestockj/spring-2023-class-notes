# Assignment 1
Jacob Fahnestock
5/15/2022 
Professor Rawlins
ELEC3225

### Assumptions Made
The assignment states the derived classes methods should just print what they plan to do when completed later. The "class search functionality" was assumed to be searching based on a couple relevant properties like name, teacher, and id. The course object is assumed to be something that's stored in a relational database with a class object to act as a DTO. It's unclear whether this class should be made as a write or read model (or both.) Because of this the course class was kept minimal. The array of student objects on the course class was removed in cpp to push off picking a tool for working with dynamic arrays in cpp until an assignment requires it.

### Description and Proof of Work
To build a user interface three derived classes extend a base user class. The base user class sets a first and last name as well as an id. The base class is the most concrete and tested. Here's two test cases (shown in java) run through all three languages with their respective outputs.

#### Test Case 1
```java
    IUser user1 = new IUser("User1", "lastName", 1); 
    System.out.println(user1.toString()); 
    user1.setFirstName("firstName");
    System.out.println(user1.toString());
```

#### Java Output
```
IUser [firstName=User1, lastName=lastName, id=1]
IUser [firstName=firstName, lastName=lastName, id=1]
```
#### C++ Output
```
User: User1 lastName 1
User: firstName lastName 1
```
#### Python Output
```
firstName=User1 lastName=lastName id=1 
firstName=firstName lastName=lastName id=1
```

#### Test Case 2
```java
    IStudent student1 = new IStudent("Student1", "lastName", 1);
    student1.addCourseById(1234);
    student1.removeCourseById(1234);
```

#### Java Output
```
Adding course with id: 1234
Removing course with id: 1234
```
#### C++ Output
```
Adding course: 1234
removing course: 1234
```
#### Python Output
```
Adding course: 1234
Removing course: 1234
```

The base class is then extended by the student, admin, and instructor class. These classes call the base constructor, add no new properties, and only add methods which print what they plan to do when written. 

### Advantages / Disadvantages

 Language      | Advantages  | Disadvantages
 ----------- | ----------- | ------------
 Java      | Strict typing while offering dynamic arrays | Strict typing takes a little longer to write
 Python | Weak typing with tons of flexibility | Bad at catching type errors prior to runtime
 C++ | Strict typing for better error checking | Headaches whenever you need to use dynamic arrays especially of custom objects
