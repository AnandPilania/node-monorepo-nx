# modulith-node

Modular Monolith Backend Node Application

# Description

CRUD Backend Application made with Modular Monolith architecture, structured with Nx Monorepo.

# Concepts

## Modular Monolith

A monolith system is a system that has one and only one deployment unit. Meanwhile, modularity means a separation of concern based on functionality of each components. It fulfills three main assumptions: independent and interchangeable, has everything necessary to provide for desired functionality, and is encapsulated or has defined interface. A modular monolith system is a monolith system created in modular way.

## Monorepo

A monorepo is a single repository containing multiple distinct projects with well-defined relationships.

## Dissection of Gojek App

In Gojek application, there are many services implemented to support the execution of the application itself. The main service is of course the user service, which organize and is responsible for the user itself. Other than the user, we might see the services are sliced based on their domains. For example, we might see GoFood services, GoRide services, GoMart services, GoSend services, GoPlay services, and much more. These services would likely to be implemented as separate services due to their differences on handling different themes. Gojek would also likely to have its own authorization and authentication services, transaction service which forwards an event generated by user to corresponding services, payment services (including payment using internal payment method such as GoPayLater which might also be implemented as a single service, or external payment gateway such as Jago), GoPay and GoPay coins e-wallet service, and even separate driver service. There are many more features in GoPay, which means that there are also many more services possibly implemented in the Gojek application.

## Implemented Services

In the Kejog application, there will be three services implemented. Aside from user servicen which handles general user things such as updating profiles and authentication-authorization, there are also restaurant service and food order service, namely GoFood. The restaurant service is intended for merchant-side interface, meaning that restaurant merchants can manage and customize their own profile through these services, including adding new menu. The order service is specifically created for users to create food order, and hopefully, through this service, the interaction between services can be demonstrated.

## Entities Definition

In regards of the services, there will only be several entities defined, including user for user service, restaurant and cuisine service for restaurant service, and order for GoFood service. The definition and relationship of each entities can be seen in the depicted Entity Relationship Diagram shown below. Here is an example of how to interpret the notation I used in the ERD. The restaurant and cuisine is connected with the menu relationship. In this case, a restaurant can have many cuisines menu, but not the other way. Hence, the defined relationship is one-to-many, as represented with arrow and non-arrow end of the line. We also see that a restaurant may not have any menu at all (might be because the merchant hasn't registered any), but not the other way around. In this case, the defined relationship is a partial-to-complete participation, as defined with thick and double lines for each relationship. Note that for simplicity sake, the entities defined are not really detailed.

![ERD for Kejog Entities](docs/img/erd_kejog.png 'ERD for Kejog Entities')

# Setting Up

1. Install all the dependencies with `npm install`.
2. Configure the environment variables in `.env`.

# How to Run

## Server

Execute `nx serve modulith-node` to run the server. This will automatically build all the modules defined in Nx, equivalent to running `npx nx build modulith-node`.

## Nx

### Library Generator

Execute `nx g @nx/node <lib_name> --buildable --directory=<dir_path>` to automatically scaffold a new library to the project.

### Module Dependencies Graph

Execute `nx graph` to open up a window in browser to see the dependencies between every modules. Below is the said graph for current modules implementation.

![Module Dependencies Graph for Kejog](docs/img/dependencies_graph.png 'Module Dependencies Graph for Kejog')

# Things to Improve
