# Homework 1

Please answer the following questions in this document, under each question, and submit your work on Gradescope by, Tue, Feb 11, at 11:00 PM ET. (You must push your final submission to GitHub first, and then submit on Gradescope.)

## Personal Information

* Your full name as it appears on Gradescope: Mrishika Kannan Nair
* The link to this repository:https://github.com/cs425sp25-homework/homework-1-MrishikaNair/

## Scenario

There is a contest where you can vote for your favorite TV series. The contest features ten popular TV series, including Friends, Game of Thrones, The Big Bang Theory, Breaking Bad, and others. The contest will last for a few hours.

We need to develop an application to support this voting contest. The voting application should cater to a regional audience across the entire U.S. and be accessible on both mobile and desktop platforms. We want to prevent users from voting multiple times, but we also want to avoid the complexities and frictions of traditional user registration and authentication.

Administrators of the voting application should have access to the current vote count. Due to the short voting period, we anticipate a high frequency of votes, potentially reaching tens of thousands per second.

## Question 1

Identify at least four stake holders and two user roles for the app based on the provided scenario. 

**Ans**

Primary Stake holders
1. Movie audience(voters)
2. Contest Organizers or administrators (Manage the vote count, etc)
Other Stake holders
4. Movie Producers
5. Sponsors & Advertisers
6. Application Developers

User roles
1. Voters - Audience who cast their vote
2. Vote Administrator – Monitors vote counts, ensures there are no anomalies in the voting process.

## Question 2

Write three functional requirements based on the scenario provided. There are many ways to write functional requirements; you need to write three distinct requirements each based off one of the following types: 

* User stories: As a [type of user], I want [some goal/feature] so that [some reason/benefit].
* Problem stories: In order to [solve some problem], we will build [some feature].
* Job stories: When [some situation], I want [some feature/motivation] so that [expected outcome].

**Ans**

* User stories: As a voter, I want to have the freedom to change my vote before the period ends so that I dont regret making hasty decisions.
* Problem stories: In order to solve the problem of a voting tie, we will implement a tiebreaker mechanism that extends the voting period or selects a winner based on criterias such as the earliest vote received.
* Job stories: When the system crashes during the voting period, I want an automatic failsafe or recovery mechanism so that voting can resume without any data loss.

## Question 3

Write three non-functional requirements based on the scenario provided. You should write two system quality attributes (choose from: availability, performance, scalability, and reliability) and one system constraint (choose from: technical, business, legal). Label each requirement accordingly, e.g., #scalability or #legal. While ideally you must make these requirements measurable, it is not required for this homework.

**Ans**

Availability: Since the voting period is only for a few hours, the system must be accesible to the votters 99.99% of the time during the contest.

Performance: The system should be able to handle close to 10K concurrent users with minimum latency.

Reliability: The system must record and store all the submitted votes accurately (consider caching), so there is no problem even in the case of system faliures.

Technical: The voting application must work on both mobile and desktop platforms, across different operating systems without a need for additional software installation(cater to a regional audience).

Business: The application must be developed withing the span of 10weeks, and should not exceed the budget of $10,000.

## Question 4

The scenario provided is high-level and lacks details. Write three clarifying questions you would ask an interviewer if they had asked you to design the software described above. One question should clarify a functional requirement, and the other two should clarify non-functional requirements. Label them to indicate which is which. For each question, further explain why you are asking it, i.e., how it affects your design.

**Ans**

Functional requirement questions : 
* Can the users make changes to their votes till the process is over or is their submission final?
  
  Reason - This would affect the database design to ensure that only the latest submission of the user is recorded, otherwise it could just be a running count without storing the user details in the database. This is also important in terms of fraud detection or voting anomalies.

Non-functional requirement questions :
* Technical - Should the application have a native mobile application or would a web-app platform suffice?
  
  Reason - Web app should be able to handle high traffic and concurrent users effectively, but a native app can ensure seamless user exerience when thereis a network issue or can provide reminders. Its a design choice in terms of complexity or better user experience.

  
* Availability - How long should vote records be stored after the contest ends?
  
  Reason - This will affect the database design, whether the votes should be archived or not, etc. It could also be in terms of transparency for audit purposes or future contest reference.

## Question 5

Draw an Entity Relationship Diagram (ERD) for the voting application. The ERD should include entities like Users, TV Series, and Votes. Ensure your model is in third normal form (3NF).
![ERD](link-to-image)
> [!NOTE]
> You must provide a polished ERD. You can use any tool to draw the ERD, but it must be clear and readable. For example, you can use <https://app.diagrams.net/> or any other tool of your choice. Export the ERD as an image and include it in your submission. You should link to the image in this document using markdown syntax: `![ERD](link-to-image)`.

> [!TIP]
> GitHub renders Mermaid.js syntax for ERDs. You can use it to draw the ERD directly in this document. Please consult the [Mermaid.js documentation](https://mermaid.js.org/syntax/entityRelationshipDiagram.html) for more information.

## Question 6

Suppose the TV series voting application expanded its features allowing users to register, create profiles, and review TV series, seasons, or episodes. Update your ERD to capture the data model for this expanded application. Ensure your model is in third normal form (3NF).
