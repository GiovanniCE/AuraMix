# Specification Document

Please fill out this document to reflect your team's project. This is a living document and will need to be updated regularly. You may also remove any section to its own document (e.g. a separate standards and conventions document), however you must keep the header and provide a link to that other document under the header.

Also, be sure to check out the Wiki for information on how to maintain your team's requirements.

## AuraMix



### Project Abstract


The goal of this project is to create an AR interface for a DJ to use during a set. This program will enable DJ's to step outside of their conventional setups, and add body movement to control to their set. The interface will also include a Heads-Up Display (HUD) showing essential information, and will allow for the user to focus more on the performance instead of a laptop screen. 

### Customer

This app will be tailored to new and experienced live DJ performers. This app will bring a new element of DJ'ing, and would be a great opportunity for users new to the hobby to get experience. 
<!--A brief description of the customer for this software, both in general (the population who might eventually use such a system) and specifically for this document (the customer(s) who informed this document). Every project will have a customer from the CS506 instructional staff. Requirements should not be derived simply from discussion among team members. Ideally your customer should not only talk to you about requirements but also be excited later in the semester to use the system.-->

### Specification

<!--A detailed specification of the system. UML, or other diagrams, such as finite automata, or other appropriate specification formalisms, are encouraged over natural language.-->



<!--Include sections, for example, illustrating the database architecture (with, for example, an ERD).-->

<!--Included below are some sample diagrams, including some example tech stack diagrams.-->

#### Technology Stack
```mermaid
flowchart TD
    %% Entities
    DJ("The Physical DJ (Performer)")
    FLX4[/"DDJ-FLX4 Controller (Hardware INPUT)"/]
    
    subgraph XR_Layer ["XR Compute Layer (The Headset)"]
        Quest["Meta Quest 3 (Tracking & Display)"]
        Unity(["Unity Engine 'AuraMix' App (Frontend & Logic)"])
    end

    subgraph Audio_Layer ["Audio Processing Layer (The Laptop)"]
        DAW[/"Laptop running DAW (Rekordbox/Ableton Backend)"/]
        Speakers("Audio Output (Sound System)")
    end

    %% Connections & Data Flow
    DJ ==>|1. Skeletal Movements & Gestures| Quest
    DJ ==>|2. Tactile Knob/Fader Turns| FLX4
    
    Quest -.->|Raw Sensor Data| Unity
    FLX4 ==>|3. USB MIDI Data| Unity
    
    Unity ==>|4. Processed OSC Commands| DAW
    FLX4 -->|Audio Signal Path| DAW
    DAW ==>|5. Final Master Audio| Speakers

    %% Styling
    classDef software fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:#000;
    classDef hardware fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#000;
    classDef human fill:#e8f5e9,stroke:#388e3c,stroke-width:2px,color:#000;
    
    class Unity,DAW software;
    class FLX4,Quest,Speakers hardware;
    class DJ human;
```


#### Database

```mermaid
---
title: Sample Database ERD for an Order System
---
erDiagram
    Customer ||--o{ Order : "placed by"
    Order ||--o{ OrderItem : "contains"
    Product ||--o{ OrderItem : "included in"

    Customer {
        int customer_id PK
        string name
        string email
        string phone
    }

    Order {
        int order_id PK
        int customer_id FK
        string order_date
        string status
    }

    Product {
        int product_id PK
        string name
        string description
        decimal price
    }

    OrderItem {
        int order_item_id PK
        int order_id FK
        int product_id FK
        int quantity
    }
```

#### Class Diagram

```mermaid
---
title: Sample Class Diagram for Animal Program
---
classDiagram
    class Animal {
        - String name
        + Animal(String name)
        + void setName(String name)
        + String getName()
        + void makeSound()
    }
    class Dog {
        + Dog(String name)
        + void makeSound()
    }
    class Cat {
        + Cat(String name)
        + void makeSound()
    }
    class Bird {
        + Bird(String name)
        + void makeSound()
    }
    Animal <|-- Dog
    Animal <|-- Cat
    Animal <|-- Bird
```

#### Flowchart

```mermaid
---
title: Sample Program Flowchart
---
graph TD;
    Start([Start]) --> Input_Data[/Input Data/];
    Input_Data --> Process_Data[Process Data];
    Process_Data --> Validate_Data{Validate Data};
    Validate_Data -->|Valid| Process_Valid_Data[Process Valid Data];
    Validate_Data -->|Invalid| Error_Message[/Error Message/];
    Process_Valid_Data --> Analyze_Data[Analyze Data];
    Analyze_Data --> Generate_Output[Generate Output];
    Generate_Output --> Display_Output[/Display Output/];
    Display_Output --> End([End]);
    Error_Message --> End;
```

#### Behavior

```mermaid
---
title: Sample State Diagram For Coffee Application
---
stateDiagram
    [*] --> Ready
    Ready --> Brewing : Start Brewing
    Brewing --> Ready : Brew Complete
    Brewing --> WaterLowError : Water Low
    WaterLowError --> Ready : Refill Water
    Brewing --> BeansLowError : Beans Low
    BeansLowError --> Ready : Refill Beans
```

#### Sequence Diagram

```mermaid
sequenceDiagram

participant ReactFrontend
participant DjangoBackend
participant MySQLDatabase

ReactFrontend ->> DjangoBackend: HTTP Request (e.g., GET /api/data)
activate DjangoBackend

DjangoBackend ->> MySQLDatabase: Query (e.g., SELECT * FROM data_table)
activate MySQLDatabase

MySQLDatabase -->> DjangoBackend: Result Set
deactivate MySQLDatabase

DjangoBackend -->> ReactFrontend: JSON Response
deactivate DjangoBackend
```

### Standards & Conventions

<!--This is a link to a seperate coding conventions document / style guide-->
[Style Guide & Conventions](STYLE.md)
