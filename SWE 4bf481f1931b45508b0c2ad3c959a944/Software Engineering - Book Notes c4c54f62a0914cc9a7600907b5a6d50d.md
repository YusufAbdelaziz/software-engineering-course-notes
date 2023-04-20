# Software Engineering - Book Notes.

## Chapter 3 - Agile Software Development.

- Introduction.
    - Since our world is full of businesses and each business is operating in a competitive environment, some businesses may consider deploying a software quickly at the expense of quality and requirements is a no-brainer.
    - Software requirements are changing due to the changing environment and the customer can’t predict how a system will affect working practices and how it’d interact with other systems. The requirements become clear once the system is delivered and user experience is gained, but some external factors may change the requirements a little bit.
    - Plan-driven software development processes (Waterfall) that completely specify the requirements and then design, build, and test the system are not practical because the requirements are changing and thus some of the work has to be redesigned and therefore retested. As a consequence, the waterfall model takes a long time.
    - Using plan-driven approach (waterfall) might be essential in safety-critical control systems, where a complete analysis of the system is essential. But in a fast-moving business environment, development processes that focus on rapid software development and delivery are essential.
    - Faster software development processes really took off in the late of 1990s with the idea of “agile methods” such as Extreme Programming (1999), Scrum (2001), and DSDM (2003). Agile methods are aimed to produce useful software quickly.
    - Common characteristics between different agile methods.
        - The processes of specifications, design, and implementation are interleaved. Design documentation is minimized or generated automatically. The user requirements document outlines the most important characteristics of the system.
        - The system is developed in a series of increments. End-users are involved in specifying and evaluating each increment. The users may propose changes to the software and new requirements that should be implemented in later versions.
        - Different tools may be used such as tools for automated testing, tools to support configuration management, and system integration. Such tools are used to support the development process.
    - Agile methods are incremental development methods. Each increment include a new version or release of the system that are made available to the customer every two or three weeks. They also include customer involvement to get rapid feedback and apply changes to the requirements.
    - Documentation is minimized by using informal communications like daily meetings rather than formal meetings with written documents.
    - In agile methods, design and implementation are central activities that may be incorporated with other activities such as requirements elicitation and testing.
    - A plan-driven approaches software engineering by identifying separate stages in the software process. The output of each stage is used as a basis for planning for the following stage.
    - Distinction between plan-driven and agile approaches.
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled.png)
        
        - In plan-driven development process, an iteration occurs **within** activities with formal documents used to communicate with different stages. So requirements would produce a requirements specification that is used to be an input to design and implementation stage.
        - In agile approaches, an iteration occurs **across** activities, so the requirements and the design are developed together rather than separately.
        - We can see later that both agile and plan-driven development processes may be used together
        
    
- 3.1 - Agile Methods.
    - In the 80s and early 90s, there was a widespread view that good software is achieved by careful project planning, formalized quality assurance, use of analysis and design methods supported by software tools and rigorous software development processes.
    - This view has come from large teams that worked for different companies.
    - The type of the software that may require such careful planning is **control systems** for a modern aircraft. Such systems may take up to 10 years from initial specification to deployment.
    - Since such large and huge systems may require a lot of people to maintain such software over its life time, an overhead in planning, documenting, and designing the system is necessary to facilitate the coordination between the teams.
    - But that overhead becomes insensible in small to medium-sized business systems, as it dominates the software development so you’re spending much time on planning rather than development and testing.
    - Due to the continuous requirement changes, the specification and design had to change with the program, thus rework is essential.
    - Heavyweight approaches led to the development of agile methods in late 90s.
    - These methods allowed development teams to focus more on the software rather than large documentation, and to release software quickly to the customer and wait to proposed changes.
    - New changes proposed by the client lead to changes in the requirements that may be implemented in later iterations.
    - These methods also eliminate dubious and long-term documentations that will probably never be used.
    - Agile manifesto and principles details.
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%201.png)
        
        Description for each principle :
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%202.png)
        
    - Two kinds of system development that agile have been successful with.
        - **Product development** where a software company is developing small to medium-sized product for sale.
        - **Custom system development** within an organization, where there’s a clear commitment from the customer to become involved in the development process.
    - Agile works very well in the previous situations as continuous interaction between the product manager or customer and the development team is required or if the system itself is a stand-alone system that is not tightly integrated with other underdevelopment systems.
- 3.2 - Agile Development Techniques.
    - XP
        - Extreme programming (XP) is considered to be the most significant approach that changed the software development culture.
        - The method was developed by Kent Beck back in 1998 and it was named “extreme” due to pushing good practices such as iterative development to extreme levels.
        - In XP, requirements are expressed as user stories, which are implemented as a series of tasks. Programmers work in pairs (pair programming) and develop tests for each task before writing code (test-first development). All tests must pass when new code is integrated into the system. There’s also a short time gap between releases.
        - XP Practices :
            
            ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%203.png)
            
        
        - Turns out in practice, the application of XP as it was originally proposed has been proved to be more difficult than expected. It cannot be integrated with the management practices and culture of most businesses. Therefore, companies adopting agile might pick and choose some of XP practices in conjunction with other agile method like Scrum.
    - Important practices in XP.
        - 3.2.1 - User Stories.
            - A user stories are scenarios of use that might be expected by a system user.
            - There’re no separate requirements engineering in agile, but they’re integrated with development.
            - A system customer collaborates with the development team to come up with use-case scenarios. They together develop a story card that describes a story that encapsulates the customer needs. After that, the development team tries to implement these scenarios in future releases.
            - An example of story card for Mentcare system for prescribing medication for a patient:
                
                                                                                                                                                                                                                                                                                           
                
                ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%204.png)
                
            - These story cards are broken into tasks by the development team with defining the estimates for the required efforts and resources to implement each task.
                
                ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%205.png)
                
            - The customer then prioritizes the stories for implementation, choosing which stories needs to be implemented first for useful business support.
            - Due to requirements changes, some unimplemented stories may be changed or discarded.
            - If changes are required for a system that is already delivered, then new stories are developed and the customer can decide whether these changes are prioritized over new functionalities for the system.
            - The principle problem with user stories is completeness. It’s difficult to judge whether all requirements are covered in a user story and whether it also gives a true picture of an activity.
        - 3.2.2 - Refactoring.
            - A fundamental principle in traditional software engineering is that you should design for change. That is, you should expect future changes and make your software ready for such changes.
            - But XP discards this principle on the basis that designing for change is often a wasted effort as XP encourages for simple design that just satisfies the task.
            - Of course, changes will always have to be made to the code being developed. So the XP developers suggested that code being developed should be refactored constantly.
            - Refactoring means that the programming team should constantly look for code improvements and apply them immediately even though these improvements may be irrelevant for a task that they’re currently working on .
            - A fundamental problem of incremental development is that local changes tend to degrade the software structure. Therefore, further changes to the software become harder to implement. Refactoring your code may increase the overall software structure and readability so you can avoid the structural deterioration that may occur when software is changed.
            - Examples of refactoring may include the reorganization of a class hierarchy to remove duplicate code, tidying up and renaming attributes, and replacement of similar code sections.
            - When refactoring is part of development process, the software should always be easy to understand and ready for changes.
            - In practice, this is not always the case because sometimes developing new functionalities is prioritized over refactoring existing code. Also some new features and changes may require a modification in the system’s architecture, so code-level refactoring may not be enough.
        - 3.2.3 - Test-first Development.
            - One of the main differences between incremental development and plan-driven development is the way that the system is tested. There’s no testing specifications in incremental development unlike plan-driven development so you can’t actually make use of external testing team.
            - In XP, testing is automated and is the central of the development process, and development cannot proceed until all tests have been successfully executed.
            - The key features of testing in XP.
                - Test-first development.
                - Incremental test development from scenarios.
                - User involvement in the test development and validation.
                - The use of automated testing frameworks.
            - Test-first development in XP has now evolved to TDD ( Test-Driven Development ) which assumes writing tests before writing the code. This means that you can run the test as the code is being written and discover problems during development.
            - Writing tests implicitly defines both an interface and specification of behavior for the feature that is being developed so misunderstanding may be reduced.
            - Test-first development require a clear relationship between requirements and the code implementation of these requirements. In XP, this relationship is clear because user stories represents the requirements that are broken down into tasks that can be implemented.
            - In test-first development, the specification must be clear and understandable to the developers so they can write tests properly before the implementation begins. This can also avoid the problem of “test-lag” that might happen when implementation is further ahead than the testing which might end in skipping tests to meet the development schedule.
            - Notice that XP’s test-driven development assumes that user stories are successfully developed, and also broken down to tasks.
            - Test case description for dose checking :
                
                ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%206.png)
                
            
            - The role of the customer is to help develop acceptance tests for the stories that are to be implemented in the next phase.
            - Test automation is essential in test-first development. Test are written as executable components before the task is implemented. Each component should be stand-alone and should simulate the submission of input to be tested, and should check that the result meets the expected output. An example of an automated testing framework is **Junit** for testing Java programs.
            - Since the testing is automated, whenever you add a new functionality, you can run the previously written tests as well as the tests you’ve just written for the new feature and check if the new code introduces any issues.
            - Problems in ensuring whether test coverage is complete.
                - Programmers prefer programming to testing, thus writing incomplete tests that may not cover all use cases that may cause exceptions.
                - Some tests can be very difficult to write incrementally like in complex user interfaces where it’s hard to write tests for the “display logic” and workflow between different screens.
            - It’s usually hard to make sure that your set of tests are complete. You may have a lot of written tests in your system but maybe some other crucial parts are not covered, hence bugs may appear during system releases.
        - 3.2.4 - Pair Programming.
            - Pair programming is a practice that was introduced by XP, in which each pair sit together on the same computer to develop the software. Pairs are created dynamically so team members work with each other during software development.
            - Advantages of pair programming.
                - It supports the idea of collective ownership. This means that each team member knows what’s going on with each part of the software, so any team member can tackle any issue in the software rather than each one of them knows only his/her part of the software.
                - It helps in reviewing the code informally because two people are looking at the same code which may lead in reducing some bugs. But unfortunately, that comes at the expense of quick software development, which means that there’ll be some delays. Also it’s beneficial in finding some errors but not as effective as code inspections.
                - It encourages refactoring to improve the software structure.
            - Some companies are suspicious of pair programming and do not use it. Other companies may mix between pair and individual programming by making an experienced developer work with less experienced one.
            - Some studies say that pair-programming productivity is comparable to two programmers work individually, other studies state the opposite.
            - What makes pair-programming worthwhile is sharing experience between developers which reduces the overall risks that a team may face when one member leaves.
            
- 3.3 - Agile project management.
    - An advantage that plan-driven software development has is that managers know what’s going on under the hood. Some questions are answered like who is working on the software development, when should we deliver the software, or whether the proposed budget would be enough for the development.
    - Unfortunately, agile methods clashed with this business requirement for visibility. Teams are self-organized, did not produce documentation, and planned development in very short cycles.
    - That may be enough for small companies that are delivering software, but for larger ones, this is unacceptable because managers need to know what is really going on.
    - To address visibility issue, the Scrum agile method was developed to provide a framework for organizing agile projects and to provide external visibility of what is going on.
    - **Important Scrum terminology**.
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%207.png)
        
    - **What is the difference between a project manager and a scrum master** ?
        - **Scrum master** is responsible for ensuring the Scrum process is followed and guides the team towards the effective use of Scrum. He or she is responsible of ensuring that the team is not diverted by outside interference.
        - **Project manager** is responsible of making sure that a software is delivered on time within budget, and with their goals fulfilled.
    - Scrum is a project organization method, it does not propose or mandate the use of specific development practices like pair programming and test-first development in XP method.
    - Agile methods have become a mainstream, and Scrum is considered to be the most widely used method.
    - **Scrum cycle.**
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%208.png)
        
        - Each process iteration produces a product increment that could be delivered to customers.
        - The scrum process starts with the product backlog. Product backlog is the list of items such as product features, requirements, or engineering docs. The initial backlog is filled from a requirement document, a list of user stories, or other description of the software to be developed.
        - Product backlog can also contain items like system architecture or to develop system documentation.
        - The product backlog may contain items with different level of detail, and it’s the responsibility of product owner to make each item as clear as possible to get the work done.
        - A backlog item could be a full user story or an instruction like “refactor UI code”.
        - Each sprint cycle lasts for about 2 to 4 weeks. The product owner prioritize the items that current cycle should finish.
        - Sprints cannot be extended to finish unfinished work, instead, unfinished work is returned to the product backlog.
        - It’s the responsibility of the team to estimate how much time it takes to finish the items in the sprint, the velocity (which is number of items in the backlog covered in a sprint) attained from previous sprints is used for the estimation.
        - The team is self-organized so they can decide who will work on what.
        - Daily meetings are held (Scrums) to review progress, and reprioritize work. During the Scrum, all members share information, what kind of problems each one of them faced, and what they’ll do for the following day.
        - At the office, there’s a scrum board which is a whiteboard that includes information about the whole team progress and what work remains to be done.
        - At the end of a sprint, a review meeting is held to discuss the process improvements, and to know the product state for the product backlog review that precedes the next sprint.
        
    - Some scrum success stories.
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%209.png)
        
    - Scrum was intended for use with co-located teams where all members are in the same place and can attend standup meetings. But distributed teams require Scrum method to be also distributed.
    - Distributed Scrum requirements.
        
        ![Untitled](Software%20Engineering%20-%20Book%20Notes%20c4c54f62a0914cc9a7600907b5a6d50d/Untitled%2010.png)