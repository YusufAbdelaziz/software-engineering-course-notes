# Software Project Secrets - Book Notes

### It’s important to note that this book was released back in 2005, so stats may not reflect the status quo of the modern software industry, but other practices and advice mentioned in the book are super useful, so have fun !

## CH1 - Introduction

- What is the difference between commercial and noncommercial software?
    - Commercial software is produced by companies for profit, some of them are written specifically for individual clients and some are generic products like Microsoft Word.
    - Noncommercial software is often called **open source,** which means that anyone can read its source code. Users can find out how it works, make some changes to fix bugs or adding features. **Open source shapes our software world**.

## CH2 - Why Software is different?

- Comparing software development to road building.
    - Software projects are affected by external events as road building may be affected by weather.
    - For example, if a third-party component isn’t available on time, then similar delays can occur.
- Unique characteristics scheme that affects software development and their relationships.
    
    ![Untitled](Software%20Project%20Secrets%20-%20Book%20Notes%20568fb7d509ea4bef90973a6e17180db6/Untitled.png)
    
- Software unique characteristics.
    - Characteristics based on Software nature.
        - 1 - Software Is Complex.
            - In software development, reducing complexity is the most important and hardest task to accomplish and it’s what makes software unique.
            - Any software appears as a sequence of instructions.
            - An instruction may be a single line in a text or may span to multiple lines. It can copy a piece of data, perform some arithmetic, manipulate text, or decide which parts of the program to execute and in what order.
            - Your software may contain blank lines to separate groups of instructions, comments, and elements that help define the structure of the program.
            - The most important part of the code is the instructions.
            - Complexity is not measured by the number of lines you’ve written. 100k-line program is not necessarily more complex than 10k-line program. It mainly depends on the **interaction** between these instructions.  A 100k-line program has ten times as many instructions interacting with ten times as many instructions, so the former is expected to be more complex than the latter.
            - Skilled developers endeavor to reduce the complexity by separating their system into small chunks of code called objects, or bigger chunks called components. The complexity can be therefore hidden by applying ***encapsulation*** which is one of the 4 main pillars of object oriented programming.
            - Consider a system with 12 items that interact with each other, dividing these items into smaller assemblages may reduce the total number of interactions, but how may I calculate the total number of interactions ?
                
                $$
                Number\space Interactions \space = \space \frac{n(n-1)}{2}
                $$
                
                Where $n$ is the number of interactions.
                
            
            - So the total number of interactions is reduced from 66 to 18.
                
                ![Untitled](Software%20Project%20Secrets%20-%20Book%20Notes%20568fb7d509ea4bef90973a6e17180db6/Untitled%201.png)
                
            - How to calculate the increase or decrease percentage ?
                
                $$
                \%\space Incease/Decrease\space =\space\frac{Bigger - smaller}{smaller} * 100
                $$
                
            - Although engineers exploit every possible technique to reduce the complexity of their code, but the complexity of a software increases faster than its size.
        - 2 - Software Is Abstract.
            - You can’t physically touch software, unlike the a route or road which you can easily touch the material and walk on it.
            - Software is a **codification** of a huge set of behaviors. It’s a sequence of events, if this happens then that should happen. One can visualize individual behaviors, but we’d have a great difficulty visualizing large numbers of behaviors or their interactions.
            - In chess, for example, a single piece’s behavior is meaningless in isolation but what gives its significance is its relationship to the previous moves and the future moves.
            - The same things that makes software hard to visualize make it hard to draw blueprints of that software.
            - Summarizing is removing essential details and these details can cause the software to fail catastrophically or -worse- subtly and insidiously.
            - Encapsulation is very useful in reducing the system’s overall complexity, but doesn’t avoid the burden of defining each and every instruction in our system.
            - Creating a map or blueprint for a piece of software is great to simplify the representation of that software but you’d face incorrectness and inaccuracy if you don’t want to be verbose. But in case you want to go with full details, you can’t represent every single detail of your software because you’re just duplicating your software in another form.
        - 3 - Requirements Are Incomplete.
            - It’s uniquely difficult to define a complete set of requirements for a software before the beginning of development.
            - Software is made to fulfill the needs of users and managers, yes they don’t understand the complexity of the system and the main flows of behavior, but they can identify whether the business needs are fulfilled or not.
            - When software is taking shape, the users will gain more insights into their needs because the software is getting less abstract and they can try each possible scenario.
            - That’s why users’ opinions are very crucial. Hence both the developers and the users should cooperate to refine the requirements for the software.
            - Adding more functionality to the software, the users can revise the new features based on their testing experience when the software was under construction.
            - Unlike software, road building has straightforward specifications which can be set clearly before start building the road.
    - Characteristics based on technology used in software production.
        - 4 - Technology Changes Rapidly.
            - We all know that software changes quickly but we don’t know how quickly it changes, and what impact this has on any new software we try to build.
            - Nowadays (2005), any significant software is built with an enterprise application framework like Java 2 Enterprise Edition or Microsoft .NET.
            - Some important terminology :
                - **Framework** : A framework is a toolkit. Stating it more specifically, it’s a set of pre-made building blocks that are proven to be useful in building certain types of software. These building blocks can save a huge amount of time for the developer. Such ready-to-use functionalities include getting data from database, drawing a window, parsing a JSON, and more.
                - **Application** : The word application can vary from the one-person desktop application like Microsoft Word, to multiuser applications that run on a local network like email or accounting, and beyond different web applications like [Amazon.com](http://Amazon.com) and google search page.
                - **Enterprise** : We may think of this word as “as big as you want”. A good example is google search page which serves more than 1k user per second (Nowadays, Google receives about 63k queries per second), so enterprise technology allows many computer to work together for a single application, and also provides the connectivity to allow lots of people to access it at the same time. It’s good to note that enterprise application can go with small applications not just major applications in big companies.
            - Back to our comparison, we’ve been building roads for thousands of years. The problems faced are understood, and the technologies change slowly.
            - In summary, software development technologies change faster than other construction technologies.
        - 5 - Best Practices Are Not Mature.
            - **Fragile code** is the code that may harm a system functionality when trying to extend or adding more functionalities to that system.
            - A **best practice** is a process or technique that has a proven record of success in providing sufficient improvement to the results of an activity.
            - Experience allows the programmers to define the best practices, in other words, how to use a technology well.
            - OOP was around since 1980 but the GoF (Gang Of Four) published their book ***Design Patterns*** in 1995 which provided a significant architectural solutions to “anti-patterns” (a.k.a code smells) or design problems that faced the engineers.
            - So the key point is that new technologies need some time (maybe long time) to have mature best practices that can be used efficiently.
        - 6 - Technology Is a Vast Domain.
            - An enterprise application frameworks contain large number of functionalities (routines) and you may also use third-party software that has components that contain other functionalities. A single application may use a portion of these routines and components. Therefore, a developer won’t be able to gain experience with all technologies, he’d only have the experience with the portion he worked with.
            - Summary ⇒ **Software development has far more technologies, and its technologies have far more complexity than a single individual can hope to gain expertise with**.
        - 7 - Technology Experience Is Incomplete.
            - New technologies are introduced to the field every few years, even existing technologies may change differently from their early releases.
            - A developer may use some parts from a framework, but can’t use that experience in another projects that utilizes different parts of the same framework.
            - The bulk of the technical knowledge required for a project will normally be learned on the job.
            - Therefore, long lists of desired technology skills we see in job ads are useless.
            - Some skills are common between different projects like “soft skills” which make a good developer or team leader, but unfortunately they’re rarely mentioned in job ads.
            - **Summary** ⇒ Expertise with particular software development technologies is very quickly outdated, and therefore most specific skills are learned on the job.
        - 8 - Software Development Is Research.
            - As we said before about incompleteness of the requirements, clients aren’t software experts, they don’t know what is possible and what is not, or know what trade offs are available. Hence cooperation between the developers and clients must be established.
            - So software development is the process of discovering whether a technology is suitable for a specific purpose. In other words, we’re trying to discover the upcoming setbacks or dead ends when a technology is chosen to implement a software.
            - Software projects are simply the process of discovering the unknown, once the unknowns are known, then the project is effectively at an end.
            - Summary ⇒ Software development isn’t just a process of creating software; it’s also a process of learning how to create the software that is best suited for its purpose.
        - 9 - Repetitive Work Is Automated.
            - Common tasks in software development is already done and automated.
            - Frameworks have the common tasks and services already done so the developer can use them directly, also more specialized ones exist with third-party software.
            - **Summary** ⇒ Software development has been automated to a greater degree than other project-based activities.
    - Characteristics based on how customers interact with development team.
        - 10 - Construction Is Actually Design.
            - In road building, the first step is to perform the planning and design, which results in a set of plans and blueprints.
            - Once this step is completed, the construction can start because all phases after the designing phase are well-defined and require less highly skilled workers.
            - In contrast, software development is a process of research. So at no point you can define plans or blueprints to start the implementation of your design.
            - Since software is abstract, construction tasks is the same as performing the work. So there’s no separation between the construction and the design.
            - In software, we’re designing on smaller and smaller scales.
            - So a developer implements a new feature, he has to define each instruction in his code, but each instruction itself is a design decision.
            - Programming is more than just writing code. Each step requires the developer to analyze some portion of the problem and design some aspects of the solution.
            - **Summary** ⇒ Unlike other products, software is not constructed, but rather designed into existence.
            
        - 11 - Change Is Considered Easy.
            - Once a section of a road is built, there’s no way back. Roads are extended or widened, or can be modified by adding a new section alongside another one.
            - Changes happen in civil engineering but they don’t change the nature of the product, you’d get a road at the end of the day.
            - In software, changes can be done anytime. You can just rewrite any portion in your code and your software would be different.
            - But when a software is modified, you have to revise the architecture of that software so to prevent creating a mess and make the software more fragile.
            - It’s important for the architecture you choose to be flexible and accommodate changes.
            - Alongside designing the architecture, designing the development process to support change is crucial.
            - **Summary** ⇒ Software can be modified rapidly, and this pace is expected, but it’s better to implement the changes properly.
        - 12 - Change Is Inevitable.
            - Since software development is an ongoing design process and some requirements are getting clearer as the project progresses, then it’s clear that software is changing continuously.
            - Clients often change their mind at any point, therefore the software face different changes.
            - Since changes are inevitable, building the software for extension and modification would make the changes more easier and prevent the code from being fragile.
            - **Summary** ⇒ No software is perfect as first envisioned; it will always require changes to make it best suit its role.
            
    - Summary
        
        ![Untitled](Software%20Project%20Secrets%20-%20Book%20Notes%20568fb7d509ea4bef90973a6e17180db6/Untitled%202.png)
        

## CH5 - The new Agile Methodologies.

- Go to Agile page and head to Crystal and XP parts.