# DCSA v1.0.0a0

> Yet another alternative approach to MVC

# What is it?

DCSA is the design pattern dedicated for frontend programming. It aims to serve as an alternative to the traditional MVC pattern.

DCSA consists of 4 separate parts. Each stands for as follows.

- D stands for Domain
- C stands for Component
- S stands for Service
- A stands for Application

## Domain

*Domain* is the domain in the sense of DDD architectural pattern of Eric Evans. This is similar to the model concept of the MVC pattern. This basically handles the data interaction of the software but it's a bit different from Model concept of MVC. Google DDD for details.

- Domain should implements all of business logic.
- Domain shouldn't touch any of visual aspect.
- Domain can handle any of requests about the Domain model.

## Component

*Components* (or *Pure Components*) are the classes which only interact with DOMs, jQuery APIs and other Pure Components. They never interact with domain and services (or service components) because they don't "know" about the domain at all. Components can be seen as the wrapper or abstraction of the DOM APIs or jQuery APIs.

- Components don't know anything about Domain, even don't know the names of domain models.
- If a component needs to change its behaviour depending on the state of domain model, then service or application should inject them into components. Components should never call domain interfaces directly.

## Service

*Service* handles both (pure) components and domain concepts. Service itself can be realized as a component, so then in that case it is called *Service Component*.

The name has come from the Domain Service in DDD. Domain Service is the class which handles the interaction between Domain Models in the Domain. Service in DCSA handles the interaction between Domain Models as well as Components. Actually Components are like domain models in the world of dom tree (the world of visual components). Then the class which handles domain models of both domain can be seen as Domain Service in the enhanced sense.

- Service can handle both visual things and invoke business logic.
- Service shouldn't implement business logic itself. Service can use Domain but is not a part of Domain.
- Service is the place where you pipe the Pure Components and Domain.
- Service shouldn't do things in details. Leave them to Pure Components as much as possible.

## Application

*Application* is the ultimate consumer of everything else. Applications use services, components and domain models and only serve directly to the users. In other words classes in the system never use application, the application always use others and never opposite.

- Application can use any other components in the system, such as domain, pure components or services.
- Application should focus on the flow of the system.
- Application shouldn't do things in detail. It should delegate details to Service or Components, business logic to Domain.
- Application should never be used by any other part of the system.


# Hierarchical View

```text

Application

-----------

Service Components

------------------

Domain | (Pure) Components

```

# License

The license of this document is CC0.
