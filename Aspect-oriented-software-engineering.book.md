# Opening 
In most large systems, the relationships between the requirements and the program components are complex. A single requirement may be implemented by a number of components and each component may include elements of several requirements. In practice, this means that implementing a change to the requirements may involve understanding and changing several components. Alternatively, a component may provide some core functionality but also include code that implements several system requirements.

Aspect-oriented software engineering (AOSE) is an approach to software devel- opment that is intended to address this problem and so make programs easier to maintain and reuse

AOSE is based around abstractions called aspects, which implement system functionality that may be required at several different places in a program

An important characteristic of aspects is that they include a definition of where they should be included in a program, as well as the code implementing the cross- cutting concern.

The key benefit of an aspect-oriented approach is that it supports the separation of concerns

By representing cross-cutting concerns as aspects, these concerns can be understood, reused, and modified independently, without regard for where the code is used.

**example:** For example, user authentication may be represented as an aspect that requests a login name and password. This can be automatically woven into the program wherever authentication is required. Say you have a requirement that user authentication is required before any change to personal details is made in a database. You can describe this in an aspect by stat- ing that the authentication code should be included before each call to methods that update personal details. Subsequently, you may extend the requirement for authentication to all database updates. This can easily be implemented by modifying the aspect. You simply change the definition of where the authentication code is to be woven into the system. You do not have to search through the system looking for all occurrences of these methods. You are therefore less likely to make mistakes and introduce accidental security vulnerabilities into your program.

# Separation of concerns 

The separation of concerns is a key principle of software design and implementation. It means that you should organize your software so that each element in the program (class, method, procedure, etc.) does one thing and one thing only. You can then focus on that element without regard for the other elements in the program

Concerns certainly are more than simply functional elements but the more general definition is so vague that it is practically useless

concerns are really reflections of the system requirements and priorities of stakeholders in the system

It is easier to trace concerns, expressed as a requirement or a related set of requirements, to the program components that implement these concerns. If the requirements change, then the part of the program that has to be changed is obvious.

## There are several different types of stakeholder concern: 
1. **Functional concerns**
    * which are related to the specific functionality to be included in a system
2. **Quality of service concerns** 
    * which are related to the non-functional behavior of a system. These include characteristics such as performance, reliability, and availability
3. **Policy concerns**
    * which are related to the overall policies that govern the use of a system. Policy concerns include security and safety concerns and concerns related to business rules.
4. **System concerns**
    * which are related to attributes of the system as a whole, such as its maintainability or its configurability.
4. **Organizational concerns**
    * which are related to organizational goals and priorities

Programming language abstractions, such as procedures and classes, are the mechanism that you normally use to organize and structure the core concerns of a system. However, the implementation of the core concerns in conventional program- ming languages usually includes additional code to implement the cross-cutting, functional, quality of service, and policy concerns. This leads to two undesirable phenomena: tangling and scattering.

The changes to the system are not all located in one place and so you have to spend time looking for the components in the system that have to be changed. You then have to change each of these components to incorporate the required changes. This may be expensive because of the time required to analyze the components and then make and test the changes. There is always the possibility that you will miss some code that should be changed and so the statistics will be incorrect. Furthermore, as several changes have to be made, this increases the chances that you will make a mistake and introduce errors into the software.

# Aspects, join points, and pointcuts
By designing the system using a component-based approach, different instantiations of the system can be configured. 

## terminology

**advice**: The code implementing a concern.

**join point**: An event in an executing program where the advice associated with an aspect may be executed.

**pointcut**: A statement, included in an aspect, that defines the join points where the associated aspect advice should be executed.

**aspect**: A program abstraction that defines a cross-cutting concern. It includes the definition of a pointcut and the advice associated with that concern.

**join point model**: The set of events that may be referenced in a pointcut.

**weaving**: The incorporation of advice code at the specified join points by an aspect weaver.

---

![image of aspectJ Code](https://i.ibb.co/HFc0NX4/Screen-Shot-2021-05-07-at-2-53-11-PM.png)

In an aspect-oriented system, you can represent these cross-cutting concerns as separate aspects

An aspect includes a specification of where the cross-cutting concern is to be woven into the program, and code to implement that concern

**poincut**
> before: call (public void update* (..))
