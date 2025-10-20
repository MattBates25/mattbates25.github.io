---
title: Matthew Bates Weight Tracking Application ePortfolio for CS 499
---

# Final Project e-Portfolio

Welcome! This site hosts my final project video, artifacts, and a professional self-assessment.

## Professional Self-Assessment
  I have been attending SNHU's Computer Science program since the beginning of 2023. I've had the opportunity to work on numberous projects and with
  countless different technologies and systems. Just working on the three enhancement areas for my Weight Tracking Application has shown what a transformative
  experience it has been. I've moved from knowing nothing about software development or programming to having an appreciation for software engineering principles.
  I've learned that being a successful developer is more than writing code that 'just works.' It means being passionate about delivering products meant for users,
  considering serious ethical questions around your implementations and how your software can be used or interpreted, and it means putting effort into building products
  that are robust, secure, and user centric. I've taken shareholder goals and turned them into concrete designs. Through vulnerability assessments I demonstrated
  the ability to analyze source code for potential security flaws and recommend mitigation strategies aligning with OWASP secure coding standards. I simulated working as
  part of an Agile development team, learning how iterative development, collaboration, and security reviews work together to produce robust software solutions.
  The artifacts in my ePortfolio show that I can design with users in mind, build reliable features, reason about performance, and defend against common failure points.
  The weight tracking application I iterated on over the last seven weeks showcases my ability to work on a full-stack application within a single, cohesive project.
  I implemented modern polished UI/UX design, I implemented strong database principles, I implemented a dynamic sorting feature demonstrating algorithmic trade-offs.

## Project Video
<!-- Replace YOUR_VIDEO_ID -->
<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;border-radius:12px;">
  <iframe src="https://www.youtube.com/embed/iecwKq3W6-E"
          title="Code Review" frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          allowfullscreen
          style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>
[Watch on YouTube](https://www.youtube.com/watch?v=iecwKq3W6-E)


## Artifacts
- [Weight Tracker (Android) – repo](https://github.com/MattBates25/ePortfolio)
  
- [Matthew's Weight Tracking Application, Initial Artifact](https://github.com/MattBates25/ePortfolio/tree/v1.0-Initial)

Matthew’s Weight Tracking Application is an android application written in Java using the Android Studio IDE.
 This artifact features logic for account creation and logging in, navigation between screens utilizing a bottom navigation bar,
 the setting of a weight goal and phone number, and the addition and deletion of weight entries to track their weight in a grid on a screen within the app.
 It was originally written in October 2024 for my CS 360 Mobile Architecture and Programming course.
I selected this artifact as it is a showcase of a full-stack application that provides a comprehensive showcase of my abilities in both crafting a functional and feature rich backend and a visually impressive and usable frontend.
 I’m given the opportunity to demonstrate a holistic understanding of what it takes to create a robust, secure, and professional application that offers a practical way to demonstrate my skills.

 ## Enhancement One: Software Engineering and Design
 - [Enhancement1](https://github.com/MattBates25/ePortfolio/tree/v1.1-Enhancement1)

The most visible improvement to the application is the complete redesign of all screens. I transitioned from using the original application’s LinearLayouts to a more modern and fluid ConstraintLayout architecture in the Login, Home, Goal, and Progress screens. This demonstrates proficiency in the use of modern and efficient layout tools and standards, as well as the ability to stick to best practices when it comes to user facing design. I fixed a critical bug in the logic for the deletion of weight entries on the Progress screen. I originally used the non-unique ‘date’ string as an identifier. I refactored and modified the ProgressItem model to include the unique ‘weight_id’, as well as updating WeightAdapter to track selections based on the unique ID. I replaced my previously flawed database method for deletion with a new method that operated on primary keys. This demonstrates my ability to analyze and identify risks in backend logic across multiple layers of an application, including the Model, View-Adapter, Controller/Fragments, and the Database. I also made sure to implement enforcement of foreign key constraints to ensure data integrity. I implemented previously missing comprehensive validation for all user inputs, showcasing a focus on security and user experience, switching from using Toast messages to the implementation of contextual feedback using setError. I added checks for empty fields, number formatting, and even complex password requirements during registration. I demonstrated my focus on creating maintainable code by refactoring all “magic strings” used for SharedPreferences into a centralized java file, reducing the risk of typos and showcasing a forward-thinking mindset.
I met each of the course outcomes in my enhancement. I build environments that encourage collaboration and a diverse audience by adding comprehensive comments to every class. The complete overhaul of the app’s UI acts as a direct demonstration of the second outcome by demonstrating the ability to design professional quality visual communications that convey the intended design for users to interact with. I designed and evaluated solutions that solved the problem of deletion and SMS notification logic lacking in function by increasing complexity in exchange for guaranteed correctness. The fourth outcome was met by demonstrating the ability to use a wide-range of tools and techniques such as the ConstraintLayout to implement a computer solution that delivers immediately visible value to the end user through an improved user experience. The fifth outcome is met by implementing strict password validation and crash-prevention.
I learned about how much goes into refactoring a software application with so many interconnected classes and files. I thought that the bug with deleting weight entries would be simple, but fixing it required deep alteration of every layer of the application. The DatabaseHelper query, ProgressItem data model, and the WeightAdapter all had to have significant changes to the methods and logic contained within. I learned the practical application of modern UI design principles. It was initially difficult as ConstraintLayout felt more complex than LinearLayout, however learning about using chains and bias and how they weren’t just direct replacements for space tags helped me understand how much more depth there is when it comes to building a responsive and flexible UI. My biggest challenge was working through the Java classes and fragments to find every instance of the date being deleted or interacted with rather than the correct weight_id.

## Enhancement Two: Algorithms and Data Structures
- [Enhancement2](https://github.com/MattBates25/ePortfolio/tree/v1.2-Enhancement2)

The Weight Tracking Application is improved via the implementation of a new sorting feature in the ProgressFragment, acting as a direct showcase of my skills in leveraging existing, high-performance algorithms, as well as designing custom ones. This is demonstrated in my delegation of sorting to the database whenever possible. The getAllWeightEntries method was enhanced in my DatabaseHelper class to build and append an SQL ORDER BY clause. I used ORDER BY date DESC/ASC and ORDER BY weight DESC/ASC to leverage SQLite’s build-in sorting algorithms, which are highly optimized and efficient when acting on indexed data. My “Sort by Distance from Goal” function showcases my ability to design and implement a custom algorithm for a non-trivial sorting metric. I followed my pseudocode to fetch the necessary data, the goal weight and the list of weight entries. I then used a calculation to derive the absolute distance from the goalWeight for each weight entry. This is not stored in the database and is calculated at runtime. This logic was implemented with a custom Java comparator, allowing the sorting of my array of progress objects based on the custom distance metric rather than the natural order, showing that I can translate a logical requirement into a functional Java implementation.
	The course outcomes met specifically by this enhancement include the design, development, and delivery of professional-grade visual communications through the implemented spinner that provides all available sorting options to the user. This makes a potentially complex feature intuitive to the end-user. Outcome three is also met directly. I used an ArrayList data structure to hold the weight entries and an ArrayAdapter for the spinner. A custom sorting algorithm was also implemented using a comparator. I managed trade-offs in my design by utilizing a hybrid solution. I used the standard sorting in the database where it was more efficient, and accepted a higher performance cost by pulling the data from the two tables operated on into the application layer where complex comparison could be more easily made. Outcome four was met by utilizing a Spinner with an OnItemSelectedLister for when the UI is tapped or otherwise selected by the user, along with the use of SQL clauses and Collections.sort for my custom algorithm, showcasing the use of a standard tool to implement a solution in the program.
	While performing the enhancement on my mobile application I learned about how useful it can be to separate implementations between different layers of an application, that sometimes the best solution is a hybrid one that lets each part of the application do what it’s best at. The database is very fast and efficient when it comes to indexed sorting, and the Java code is better for complex, in-memory custom logic. I experienced a challenge in that sorting by distance from goal initially would cause the application to crash when the user had no set a goal weight due to it being null. I had to address this by adding a null check and displaying a message to the user.

  ## Enhancement Three: Databases
  - [Enhancement3](https://github.com/MattBates25/ePortfolio/tree/v1.3-Enhancement3)

I was able to demonstrate an understanding of database performance and foresight towards future expansion of the dataset within the app by adding indexes. I knew that the user_id and date were the most frequently queried columns for filtering and sorting purposes. By creating an index for the columns in my DatabaseHelper’s onCreate method I am ensuring that the lookups will remain fast and efficient, even with hundreds or thousands of weight entries added. This shows my dedication towards building scalable applications that will avoid degradation in performance over time.
	The culmination of changes made in this enhancement and through my other enhancements transformed my database from a simple data store into a robust and professional-grade layer of my application. It now no longer deletes based on the incorrect data, it prevents data corruption via foreign keys, and it is now scalable, remaining performant as the data grows.
	This specific enhancement in adding indexing meets the third outcome of evaluating solutions using algorithmic principles and computer science practices and standards appropriate while managing trade-offs. I am trading off a small amount of disk space for a significantly faster read time on queries, a worthwhile exchange for a read-heavy application.
	Adding an index and enforcing a foreign key doesn’t result in any immediately noticeable visual change, but it is critical despite that. I have learned that a significant portion of professional software development is about proactive architectural improvement that prevents future problems instead of just fixing current ones.

