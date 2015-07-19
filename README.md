# DCSA v0.1.0

> Yet another alternative approach to MVC

# What is it?

DCSA is the design pattern dedicated for frontend programming. It aims to serve as an alternative to the traditional MVC pattern.

DCSA consists of 4 separate parts. Each stands for as follows.

- D stands for Domain
- C stands for Component
- S stands for Service
- A stands for Application

## Domain

Domain is the domain in the sense of DDD architectural pattern of Eric Evans. This is similar to the model concept of the MVC pattern. This basically handles the data interaction of the software but it's a bit different from the model of MVC.

## Component

*Components* (or *Pure Components*) are the classes which only interact with DOMs, jQuery APIs and other Pure Components. They never interact with domain and services (or service components) because they don't "know" about the domain at all. Components can be seen as the wrapper or abstraction of the DOM APIs or jQuery APIs.

## Service

*Service* handles both (pure) components and domain concepts. Service itself can be realized as a component, so then in that case it is called *Service Component*.

The name has come from the Domain Service in DDD. Domain Service is the class which handles the interaction between Domain Models in the Domain. Service in DCSA terminology handles the interaction between Domain Models as well as Components. Actually Components are like domain models in the world of dom tree (the world of visual components). Then the class which handles domain models of both domain can be seen as Domain Service in the enhanced sense.

## Application

Application is the ultimate consumer of everything else. Applications use services, components and domain models and only serve directly to the users. In other words classes in the system never use application, the application always use others and never opposite.


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
