# DCSA v1.0.0a0

> Alternative approach to MVC or MVW

# What is it?

DCSA is the design pattern focused on frontend programming. It aims to serve as an alternative to the traditional MVC pattern.

DCSA consists of 4 separate parts. Each stands for as follows.

- D - Domain
- C - Component
- S - Service
- A - Application

## Domain

*Domain* is where all of your business logic go. This is the same as the domain in the sense of DDD pattern of Eric Evans. This is similar to the model concept of the MVC pattern. This basically handles the data interaction of the software but it's a bit different from Model concept of MVC.

- Domain should implements all of the business logic.
- Domain shouldn't touch any of visual element.
- Domain can handle any request about Domain models from the other parts of the system.

## Component

*Components* are the classes which only interact with visual elements, such as DOMs, jQuery APIs and other Pure Components. They never use the Domain nor Services because they don't "know" about them at all.

Components can be seen as the wrapper or abstraction of the DOM APIs or jQuery APIs.

- Components don't know anything about Domain, even don't know the names of domain models.
- If a component needs to change its behaviour depending on the state of domain model, then service or application should inject them into components. Components should never call domain interfaces directly.

## Service

*Service* is the place where the data and visual elements interact, or in other words, the place where the Domain and Components interact. Any interaction between the data and visual elements should be implemented here and nowhere else.

A service should have one topic and be focused on it which it handles. The interfaces of a service should make sense under the view from its topic.

- Service use both the Domain and Components and they interact only there.
- Service shouldn't implement any business logic. If you need to write new business logic to complete the service, then first enhance your Domain to make it meet your needs.
- Service shouldn't do things in details. Implement such bahviour in the Component layer or in the Domain.
- A service class should be focused on a topic and its interfaces are dedicated to its purpose, not to the technical or environmental requirement.

## Application

*Application* is the ultimate consumer of everything else. Applications use services, components and domain models and only serve directly to the users. Application is the highest structure in the system and is not used by anything else.

Application can be void if the service can directly serve as an application. This structure is necessary only when the services cannot serve the user directly because of the system's requirement.

- Application layer is necessary only when it's technically necessary. If services can directly serve as uppermost interface, then there's no need of Application layer.
- Application can use any other components in the system, such as domain, pure components or services.
- Application should focus on the flow of the system.
- Application shouldn't do things in detail. It should delegate details to Service or Components, business logic to Domain.
- Application should never be used by any other part of the system.


# Hierarchical View

```text

Application

-----------

Services

------------------

Domain | Components

```

# Comparison with MVC

## Similar, just refinement

DCSA is basically similar to MVC. Domain is, in my view, a refined version of *Model*. Component is similar to *View*, but has more strict rules about its construction and range of the responsibility. Service and Application are similar to *Controller*. Separation of the concern is the major principle behind DCSA as well as in MVC. The difference is that DCSA put emphasis on *more* separation of the concern.

## View is over simplification

View is too simple. Component assumes it has layered structure, which is necessary idea in frontend programming.

## Strict separation of Visuals and Entities

In traditional MVC view often knows too much about entities. For example the rendering function of a view often takes model itself as argument. That was ok in the server side. But in the frontend that kind of implmenetation causes responsibility ambiguity and thus problems.

## Constraints on the consume-provide relationship

In DCSA the relationships between nodes are stricter. Who is the consumer of the interface or who is the provider is defined hierarchically and they shouldn't violate it. So there must be less confusion about who's user and who's provider.



# License

The license of this document is CC0.
