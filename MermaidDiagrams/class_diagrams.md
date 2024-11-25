```mermaid
classDiagram
    %% Define Classes
    class Inspector:::entity{
        +Int AM
        +Int roomNumber
        +Int availableHours
    }

    class Room:::entity{
        +Int numberOfSeats
        +Int roomNumber
        +Int selectedInstructor
        +availableHours() int
    }

    class Professor:::entity{
        +String name
        +String surname
        +String courses
        +String AM
        +assignExamDate() String
        +displayInformation() String
    }

    class Student:::entity{
        +Int AM
        +Int startYear
        +String name
        +String surname
        +signToClass() 
    }

    class Subject:::connector{
        +Int subjectCode
        +Int studentsPopulation
        +String professor
    }

    class Schedule:::logic{
        +checkAvailableTime()
    }

    %% Define Relationships
    Inspector --> Room : assignedTo
    Subject --> Room : heldIn
    Professor --> Subject : teaches
    Student --> Subject : enrolledIn
    Schedule o--> Room : schedules
    Schedule o--> Subject : schedules
    Schedule o--> Professor : consults
    Schedule o--> Inspector : assigns

    %%Define classes of style
    classDef entity fill:#f9f,stroke:#333,stroke-width:2px,color:#000,font-weight:bold;
    classDef logic fill:#9f9,stroke:#070,stroke-width:2px,color:#000,font-style:italic;
    classDef connector fill:#9cf,stroke:#006,stroke-width:2px,color:#000;

    %% Classes like Inspectors, Students, Professor, and Room represent key entities. Use one color for these.
    %% Schedule manages system logic, so it can have a distinct style.
    %% Subject connects students, professors, inspectors and rooms.
