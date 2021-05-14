# Opening 
![image of aspectJ Code](https://i.ibb.co/5rHhNsn/Screen-Shot-2021-05-07-at-3-28-10-PM.png)


In most large systems, the relationships between the requirements and the program components are complex. A single requirement may be implemented by a number of components and each component may include elements of several requirements. In practice, this means that implementing a change to the requirements may involve understanding and changing several components. Alternatively, a component may provide some core functionality but also include code that implements several system requirements.

Aspect-oriented software engineering (AOSE) is an approach to software development that is intended to address this problem and so make programs easier to maintain and reuse

AOSE is based around abstractions called aspects, which implement system functionality that may be required at several different places in a program

An important characteristic of aspects is that they include a definition of where they should be included in a program, as well as the code implementing the cross-cutting concern.

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
5. **Organizational concerns**
    * which are related to organizational goals and priorities

Programming language abstractions, such as procedures and classes, are the mechanism that you normally use to organize and structure the core concerns of a system. However, the implementation of the core concerns in conventional programming languages usually includes additional code to implement the cross-cutting, functional, quality of service, and policy concerns. This leads to two undesirable phenomena: tangling and scattering.

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

<br>

```The meaning of this is that before the execution of any method whose name starts with the string update, followed by any other sequence of characters, the code in the aspect after the pointcut definition should be executed.```

<br>

``The code to be executed is known as the ‘advice’ and is the implementation of the cross- cutting concern.``

<br>

``A join point is an event that occurs during the execution of a program; so, it could be a method call, the initialization of a variable, the updating of a field, etc``

**types of join points:**
* *call events:* calls to a method or a constructor
* *execution events:* the execution of a method or a constructor
* *initialization events:* class or object initialization
* *data events:* accessing or updating of a field
* *exception events:* the handling of an exception

A pointcut identifies the specific event(s) (e.g., a call to a named procedure) with which advice should be associated. This means that you can weave advice into a program in many different contexts

### depending on the join point model that is supported
1. Advice can be included before the execution of a specific method, a list of named methods, or a list of methods whose names match a pattern specification
2. Advice can be included after the normal or exceptional return from a method.
3. Advice can be included when a field in an object is modified; you can include advice to monitor or change that field.

Aspect weavers are extensions to compilers that process the definition of aspects and the object classes and methods that define the system

<br><br>
# Software engineering with aspects

Aspects were originally introduced as a programming language construct but, as I have discussed, the notion of concerns is one that really comes from the system requirements. Therefore, it makes sense to adopt an aspect-oriented approach at all stages of the system development process. In the early stages of software engineering, adopting an aspect-oriented approach means using the notion of separating concerns as a basis for thinking about the requirements and the system design. Identifying and modeling concerns should be part of the requirements engineering and design processes. Aspect-oriented programming languages then provide the technological support to maintain the separation of concerns in your implementation of the system

## Concern-oriented requirements engineering
![view ports image](https://i.ibb.co/GxgZ0MD/Screen-Shot-2021-05-07-at-3-39-37-PM.png)

A viewpoint-oriented approach to requirements engineering, where each viewpoint represents the requirements of related groups of stakeholders, is one way to separate core and secondary concerns, 

## Aspect-oriented design and programming
Aspect-oriented design is the process of designing a system that makes use of aspects to implement the cross-cutting concerns and extensions that are identified during the requirements engineering process.

<a href="https://ibb.co/0BgLwWZ"><img src="https://i.ibb.co/hXPNqnH/Screen-Shot-2021-05-07-at-3-56-59-PM.png" alt="Screen-Shot-2021-05-07-at-3-56-59-PM" border="0"></a>

<a href="https://ibb.co/WtHxhJ4"><img src="https://i.ibb.co/q5DySQ3/Screen-Shot-2021-05-07-at-3-57-13-PM.png" alt="Screen-Shot-2021-05-07-at-3-57-13-PM" border="0"></a>

## Developing an effective process for aspect-oriented design is essential if aspect- oriented design is to be accepted and used.

<a href="https://ibb.co/yWhyf3n"><img src="https://i.ibb.co/KFNq01j/Screen-Shot-2021-05-07-at-4-05-58-PM.png" alt="Screen-Shot-2021-05-07-at-4-05-58-PM" border="0"></a>

1. **Core system design:** you design the system architecture to support the core functionality of the system. The architecture must also take into account quality of service requirements such as performance and dependability requirements.

2. **Aspect identification and design:** Starting with the extensions identified in the system requirements, you should analyze these to see if they are aspects in themselves or if they should be broken down into several aspects. Once aspects have been identified, these can then be separately designed, taking into account the design of the core system features.

3. **Composition design:** At this stage, you analyze the core system and aspect designs to discover where the aspects should be composed with the core system.

4. **Conflict analysis and resolution:** A problem with aspects is that they may interfere with each other when they are composed with the core system. Conflicts occur when there is a pointcut clash with different aspects specifying that they should be composed at the same point in the program.

5. **Name design:** This is an important design activity that defines standards for naming entities in the program. This is essential to avoid the problem of accidental pointcuts. These occur when, at some program join point, the name accidentally matches that in a pointcut pattern.

<a href="https://ibb.co/WcKHCF9"><img src="https://i.ibb.co/1920cKV/Screen-Shot-2021-05-07-at-4-18-05-PM.png" alt="Screen-Shot-2021-05-07-at-4-18-05-PM" border="0"></a>

## Verification and validation
For aspect-oriented systems, the processes of validation testing are no different than for any other system. The final executable program is treated as a black box and tests are devised to show whether or not the system meets its requirements.