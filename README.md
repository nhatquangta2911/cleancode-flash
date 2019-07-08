# Clean Code - Robert C. Martin

-  Not a **feel good** book.
-  Learning Craftsmanship:
   -  Knowledge (principles, patterns, practices, heuristics)
   -  Work (Hard work, must sweat over it, watch others fail).

###

---

## Chapter 1: Clean Code

1. **_There Will Be Code_**

   ####

   -  We will never be rid of code (because code represents the details of the requirements and can not be ignored or abstracted, they have to be **specific**).
   -  Machines will not adapt what we need. So **there will always be code**.

   ####

2. **_Bad Code_**

   ####

   -  Trying to go fast? In a rush?
   -  Tired of working on a program and want it to be over ?
   -  You choose to leave it for another day?
   -  Feel relief of seeing the messy program work?
   -  Feel **working mess is better than nothing**?
   -  But ... **Later equals never**!

   ####

3. **_The Total Cost of Owning a Mess_**

   ####

   Over time the mess becomes so big and deep and so tall, we can not clean it up. There is no way at all.

   ####

   <p align="center">
      <img src="images/chapter1/image1.png" />  
   </p>

   ####

   Driving the productivity ever further toward ZERO

   ####

   3.1. **_The Grand Redesign in the Sky_**

   ####

   3.2. **_Attitude_**

   ####

   -  If you don't do what the manager says, you'll be fired? Probably not!
   -  Like a doctor with a durty hand?
   -  So too it's unprofessional for programmers to bend to **the will of managers who don't really understand the risks of making messes.**

   ####

   3.3. **_The Primal Conundrum_** [Primitive]

   ####

   The only way to make the deadline - the only way to go fast - is to keep the code as clean as possible at all times.

   ####

   3.4. **_The Art of Clean Code_**

   ####

   -  A programmer **_without "code-sense"_** can look at a messy module and recognize the mess _but will have no idea what to do about it._

   #####

   -  A programmer **_with "code-sense"_** will look at a messt module and see _OPTIONS & VARIATIONS_

   #####

   -  In short, a programmer who writes clean code is an artist who can take a blank screen through a series of transformations **until it is an elegantly coded system.**

   ####

   3.5. **_What Is Clean Code?_**

   ####

   -  Some keywords: _elegant, efficient, straightforward logic, does one thing, simple, direct, well-written prose, create tensions, can be read, enhance by others, one way rather than many ways for doing one thing, proper error handling, clear and minimal API, CARE, runs all the tests, no duplication, minimize the number of entities (classes, methods, functions), make it looks like a language was made for the problem, make it simple as hell =))_

   ####

4. **_School of Thought_**

   ####

   -  There are other school, other masters out there that have as much claim to professionalism as this book authors.
   -  Something would be very controversial. Probably not agree with all of them.
   -  The recommendations in this book are things they have thought long and hard about. They have learned them through decades of exprience and repeated trial and error. Thus, **whether you agree or disagree. it would be a shame if you did not see, and respect, their point of view.**

   ####

5. **_We Are Authors_**

   ####

   -  Basically, authors are responsible for communicating well with their readers. The next time you write a line of code, remember you are an author, writing for readers who will judge your effort.
   -  \*The code you are trying to write today will be hard or easy to write depending on how hard or easy the surrounding code is to read. So if you want to go fast, if you want to get done quickly, **if you want your code to be easy to write, make it easy to read\***

   ####

6. **_The Boy Scout Rule_**

   ####

   **"Leave the campground cleaner than you found it"**

   ####

   -  It's not enough to write the code well. The code has to be kept clean over time. We've all seen code **rot** and **degrade** as time passes.
   -  Checked-in our code a litter cleaner than we checked it out. -> not rot anymore
      -  Change one variable name for the better
      -  Break up one function that's a little too large
      -  Eliminate one small bit of duplication
      -  Clean up one composite _if_ statement

   ####

7. **_Conclusion_**
   ####
   -  This book can not make you a good programmer. Can not give the "code-sense"
   -  **This book shows the thought processes, the tricks, techniques, and tools**
   -  You will se good code and you will see bad code. You will see bad code transformed into good code.
   -  You will see lists of heuristics, disciplines and techniques.
   -  You will see a butt-load of code, example after example.
   -  **PRACTICE MAKES PERFECT!**
   ###

---

## Chapter 2: Meaningful Names

###

0. **_Introduction_**
   #####
   -  We name our variables, our functions, our arguments, classes and packages.
   -  We name our source files and the directories.
   -  We name our .jar file and .war file
   -  name and name and name...
   #####
1. **_Use Intention-Revealing Names_** (Tên thể hiện được ý định)

   #####

   -  _"Choosing good names takes time but saves more than it takes"_
   -  The problem is not the **simplicity** of the code but the **implicity** of the code (The degree to which the context is not explicit in the code itself)

   #####

   ```java
   public List<int[]> getThem() {
   List<int[]> list1 = new ArrayList<int[]>();
   for (int[] x : theList)
      if (x[0] == 4)
      list1.add(x);
      return list1;
   }
   ```

   #####

   -  The code implicitity requires that we know the answers to questions:
      1. theList ?
      2. Zero subscript theList[0] ?
      3. === 4 ?
      4. How to use return ?

   #####

   ```java
   public List<int[]> getFlaggedCells() {
   List<int[]> flaggedCells = new ArrayList<int[]>();
   for (int[] cell : gameBoard)
      if (cell.isFlagged())
      flaggedCells.add(cell);
      return flaggedCells;
   }
   ```

   ######

   -  Notice that the simplicity of the code has not changed. It still has exactly the same number of operators and constants, with exactly the same number of nesting levels. **_But the code has become much more explicit._**

   ###

1. **_Avoid Disinformation_** (false information - delibaretely)
   #####
   -  _hp, aix_ and _sco_ would be poor variable names because they are the names of Unix platforms or variants. Even if you are coding a hypotenuse and _hp_ looks like a good abbreviation, it could be **disinformative**.
   #####
   -  _accountList_ but not actually a _List_ - _accountGroup, bunchOfAccounts_ or just plain _accounts_ would be better.
   #####
   -  How long does it take to spot the subtle difference between a _XYZFindingSomethingInterestingToAddToTheStorage_ in one module and elsewhere a little more distant, _XYZFindingSomethingInterestingToSearchInStorage_.
   #####
   ```java
      int a = 1;
      if(O == 1)
         a = O1;
      else
         l = 01;
   ```

##

3. **_Make Meaningful Distinctions_** (Difference)
   #####
   -  Number-series naming (a1, a2, .. aN) is not disinformative - they are **noninformative**, they provide no clue to the author's intention.
   ###
   ```java
   public static void copyChars(char a1[], char a2[]) {
         for (int i = 0; i < a1.length; i++) {
            a2[i] = a1[i]; //nonsense
         }
   }
   ```
   ###
   -  Noise words: class _Product_. If you have another called _ProductInfo_ or _ProductData_, you have made the names different without making them mean anything different. - so, _Info_ and _Data_ are indistinct noise words like _a, an_ and _the_
   #####
   -  The word **variable** should never appear in a variable name. The word **table** should never appear in table name. How is **NameString** better than **Name**? Imagine finding one class named **Customer** and another named **CustomerObject**. What should you understand as the distinction? Which one will represent the best path to a customer's payment history?
   #####
   -  **moneyAmount** is indistiguishablle from **money**, **customerInfo** is indistinguishable from **customer**, **accountData** is indistinguishable from **account** and **theMessages** is distinguishable from **message**. Distinguish names in such a way that the reader knows what the differences offer.
   ##
4. **_Use Pronounceable Names_**
   #####
   -  If you can not pronounce it, you can not discuss it without sounding like an idiot. "Well, over here on the bee cee arr three cee enn tee we have a pee ess zee kyew int, see?" This **matters** beacause programming is a social activity.
   #####
   Compare
   #####
   ```java
   class DtaRcrd102 {
      private Date genymdhms;
      private Date modymdhms;
      private final String pszqint = "102";
   };
   ```
   #####
   To
   ```java
   class Customer {
      private Date generationTimestamp;
      private Date modificationTimestamp;
      private final String recordId = "102";
   };
   ```
   #####
   -  Now, this conversation is now **possible** "Hey, Shawn, take a look at this recored! The generation timestamp is set to tomorrow's date! How can that be? =)) "
   ##
5. **_Use Searchable Names_**
   #####
   -  Single-letter names can _ONLY_ be used as local variables inside short methods.
   ###
   ```java
   int realDaysPerIdealDay = 4;
   const int WORK_DAYS_PER_WEEK = 5;
   int sum = 0;
   for (int j=0; j < NUMBER_OF_TASKS; j++) {
      int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
      int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
      sum += realTaskWeeks;
   }
   ```
   ###
   -  _WORK_DAYS_PER_WEEK_ is much easier to find than all the places where **5** was used and filter the list down to just the intances with the intended meaning.
   ##
6. **_Avoid Encodings_** (Tránh trùng bảng mã)

   #####

   -  We have enough **encodings** (bảng mã hóa) to deal with without adding more to our burden.

   #####

   -  **_Member Prefixes_**: Don't need to prefix member variables with **m\_** anymore. Your classes and functions should be small enough that you don't need them. The more we read the code, the less we see the prefix.

   #####

   -  **_Interfaces and Implementations_**
      #####
      -  IShapeFactory or ShapeFactory for Abstract Factory ?
      #####
      -  We don't want our clients knows we send them an interface. We just want to give them a ShapeFactory.
      #####
      -  Thus, you must encode either the interface or the implementation.
      #####

   #####

   -  **_Avoid Mental Mapping_**
      #####
      -  There is a problem with single-letter variable names. Certainly a loop counter may be named **i, j** or **k**. So traditional!
      #####
      -  One difference between a smart programmer and a professional programmer is that the professional understands that **clarity is king**. Professionals use their powers for good and write code that others can understand.
      #####

   #####

   -  **_Class Names_**: Classes and objects should have noun or noun phrase names like _Customer, WikiPage, Account, AddressParser_. Avoid words like _Manager, Processor, Data, Info_ in the name. A class name should not be a verb.

   #####

   -  **_Method Names_**
      #####
      -  Methods should have verb or verb phrase names like _postPayment, deletePage, handleSubmit, save_
      #####
      -  _getName, setName, isPaid_ is the common standards.
      #####
      ```java
      Complex fulcrumPoint = new Complex(23.0); //BAD
      ```
      Use this: (Keep this constructor private)
      ```java
      Complex fulcrumPoint = Complex.FromRealNumber(23.0); //Much more better
      ```
      #####

   #####

   -  **_Don't be cute_**
      #####
      -  _HolyHandGrenade_ with _DeleteItems_ ??
      -  _whack()_ or _kill()_ ??
      -  _eatMyShorts()_ or _abort()_ ??
      -  **Say what you mean. Mean what you say.**
      #####
   -  **_Pick One Word per Concept_**
      #####
      -  fetch, retrieve, get ??
      -  controller, manager ??
      -  DeviceManager & ProtocolController ?? (Why not the same ??)
      #####
   -  **_Don't Pun_** (Chơi chữ)
      #####
      -  **add**
      -  In case you want put a single param into a collection ??
      -  Why you don't use **insert, append**
      #####
   -  **_Use Solution Domain Names_**

      #####

      -  Those who read your code will be **programmer**, so go ahead and use CS terms, algorithm names, pattern names, math terms, and so forth.

      #####

      -  How about **JobQueue** using instead of **AccountVisitor** =))

      #####

      -  _Like a big solution when reading this name =))_

      #####

   -  **_Use Problem Domain Names_**

      #####

      When there is no "programmer-eese" for what you're doing, use the name from _problem domain_. At least the programmer who maintains your code later can ask a domain expert what it means.

      #####

   -  **_Add Meaningful Context_**
      #####
      -  firstName, lastName, street, houseNumber, city, state, zipcode. Taken together it's pretty clear that they form an address. But what if you just saw the **state** outside alone in a method?
      #####
      -  You can add context by:
         #####
         -  Using prefixes: addrFirstName, addrLastName, addrState, and so on.
         -  Better solution is to create a class named **Address**.
         #####
      #####
   -  **_Don't Add Gratuitous Context_** (vô nghĩa, vu vơ, vô cớ)
      #####
      -  "Gas Station Deluxe" - GSD
      -  MailingAddress and GSDAccountAddress ?
      -  Address, PostalAddress, MAC, URI,...
      ##
      **If we pay off in the short term and continue to pay in the long run!!!**

   ##

## Chapter 3: Functions

###

-  In the early days of programming we composed out system of **routines and subroutines**. Then we composed our system of **programs and subprograms and functions**. Nowadays only the function survives from those early days.

###

-  Problems: Too many different levels of **abstraction**?? Too many strange, curious, and odd functions calls mixed in with doubly nested **if** statements controlled by flags.

###

1. **_SMALL !_**
   ####
   -  The first rule of functions is that they should be small. The second rule of functions is that _they should be smaller than that._
   ######
   -  Every function was just two or three or four lines long. Each was transparently obvious. **Each told a story.**
   ###
2. **_Blocks and Indenting_**
   ####
   -  Blocks within **if, else, while** statements, should be one line long. Probably that line should be a function call.
   ####
   -  Functions should not be large enough to hold nested structures. Thus, the **indent level** of a function should not be greater than 1 or 2.
   ###
3. **_Do One Thing_**
   ####
   -  **_FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY._**
   ####
   HOW???
   ####
   We can describe the function by describing it as a brief **TO** paragraph:
   ##
   ~ **TO** DoSomethingInSpecific..., we check...., and if so....In either case....
   ##
   In the end, the reason we write functions is to **decompose** a larger concept into a set of steps at next level of abstraction. (In other words, we decompose the name of the function). So it is clearly doing more than one thing.
   ##
   Another way to know that a function is doing more than "one thing" is if you can extract another function from it **with a name** that is not merely a restatement of its implementation.
   ##
   **_Sections within Functions_**: If you can divided the function into **sections** such as _declarations, initializations and sieve (filter)_. This is an obvious sympton of doing more than one thing. Functions that do one thing cannot be reasonably divided into sections.
   ##
4. **_One Level of Abstraction per Function_**
   ###
5. **_Reading Code from Top to Bottom: The Stepdown Rule_**
   ###
   To include the setups and teardowns, we include setups, then we include the test page con-
   tent, and then we include the teardowns.
      - To include the setups, we include the suite setup if this is a suite, then we include the
      regular setup.
      - To include the suite setup, we search the parent hierarchy for the “SuiteSetUp” page
      and add an include statement with the path of that page.
      - To search the parent.
   ###
6. ***Switch Statements***
   ###
   It's super hard to make a switch statement that does one thing. Unfortunately we can't always avoid switch statements, but we can make sure that each switch statement is buried down in a low-level class and is never repeated. Of course, with **polymorphism**
   ###
7. ***Use Descriptive Names***
   ###
   - Don't be afraid to make a name long. A long descriptive name is better than a short bullshit name. A long descriptive name is better than a long descriptive comment.
   #####
   - Don't be afraid to spend time choosing a name. Indeed, you should try several different names and read the code with each in place.
   #####
   - Be consistent in your names. Use the **same phrases, nouns, verbs**. 
   ###
 8. ***Function Arguments***  
      ###
      The ideal number of arguments for a function is **ZERO** (niladic). Next comes one (monadic), two (dyadic), three (triadic) should be avoided where possible.
      ###
      8.1. Common Monadic Forms (2 reasons)
      ####
      - You may be asking a question about that argument
         #####
         ```java
         boolean isFileExists("C://myfilePath");
         ```
         #####
      - You may be operating on that argument, transforming it into something else and returning it. 
         #####
         ```java
         InputStream fileOpen("C://myfilePath");
         ```
         #####
      ###
      8.2. Dyadic Functions
      ###
      "The parts we ignore are where the bugs will hide."
      ###
      - There are times where 2 arguments are appropriate. For example:
      #####
      ```java
         Point p = new Point(0, 0);
      ```  
      ###
      8.3. Triads
      ###
      Significantly harder to understand than dyads
      ###
9. ***Flag Arguments***
   ###
   - Flag arguments are **ugly**
   - Passing a boolean into a function is a truly terrible practice.
   ###
10. ***Argument Objects***
   ###
   ```java
   Circle makeCircle(double x, double y, double radius);
   Circle makeCircle(Point center, double radius);
   ```
   ###
11. ***Have No Side Effects***
   ###
   - checkPassword() + Session.initialize() --> side effect
   - It supposes to be checkPasswordAndInitializeSession()
   ###
12. ***Command Query Separation***
   ###
   - Functions should either do somwthing or answer something, but **not both**. 
   ```java
   public boolean set(String attribute, String value);
   if(set("username", "shawn"))... XXX
   ```
   ###
   - SOLUTION: Separate the command (do something) from the query (answer question) so that the ambiguity cannot occur.
   ```java
   if(attributeExists("username")) {
      setAttribute("username", "shawn"); OK
   }
   ``` 
   ###
13. ***Prefer Exceptions to Returning Error Codes***
   ###
   - Use **exceptions** instead of returned error codes. Then the error processing code can be separated from the happy code and can be simplified.
   ```java
   if(deletePage(page) == E_OK) XXX
   ```
   In comparison with
   ```java
   try {
      deletePage(page);
   }
   catch(Excetion e) {
      logger.log(e.getMessage());
   }
   ```
   ###
14. ***Extract Try/Catch Blocks & Error Handling Is One Thing***
   ###
   Try/Catch blocks are ugly in their own right.
   ```java
      public void delete(Page page) {
         // Should do one thing
         // And only for handling error 
         try {
            deletePageAll(page); // in stead of a mass of code here
         }
         catch(Exception e) {
            logError(e);
         }
      }
   ```
   ###
   **Function should do one thing. Error handling is one thing.**
   ###
15. ***Don't Repeat Yourself***
      ###
      Many principles and practices have been created for the purpose of controlling and eliminating it. Object Oriented Programming, Structured Programming, Aspect Oriented Programming, Component Oriented Programming, are all, strategies for ***eliminating duplication***
      ###
16. ***Structured Programming***
   ###
   - Every function, every block within a function, should ***have one entry and one exit***
   - So, *return, break, continue, goto* break this rule.
   - So if you keep your functions small, then the occasional multiple return, break, or continue statement does no harm and can sometimes even be more expressive than the single-entry,single-exit rule.
   ###
17. ***How Do You Write Functions Like This?***
      ###
      *I don't write them that way to start. Refine later on!*
      ##
18. ***CONCLUSION***
      ###
      Functions are the **verbs** of that language, and classes are the **nouns**
      #####
      "Master programmers think of systems as stories to be told rather than the programs to be written."
      - 
      ###
--- 
## Chapter 4: Comments
   ###
   Inaccurate comments are far worse than no comments at all. They delude and mislead. They set expectations that will never be fullfiled.
   ###
   1. ***Comments Do Not Make Up for Bad Code***
      #####
      One of the more common motivations for writing comments is bad code. We write a module and we know it is confusing and disorganized. **We know it's a mess, it totally suck.**
      ###
   2. ***Explain Yourself in Code***
      ###
      ```java
         // Check to see if the employee is eligible for full benefits
         if ((employee.flags & HOURLY_FLAG) &&
            employee.age > 65)
      ```
      Or
      #####
      ```java
         if(employee.isEligibleForFullBenefit())
      ```
      ###
      In many cases it's simply a matter of creating a function that says the same thing as the content you want to write.
      ###
   3. ***Good Comments*** 
      ###
      The comment you found a way not to write
      -
      ###
   4. ***Legal Comments***
      ###
      Sometimes our corporate coding standards **force** us to write comments for legal reasons.
      ###
      At the beginning of every source file 
      // Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
      // Released under the terms of the GNU General Public License version 2 or later.
      ###
   5. ***Informative Comments***
      ###
      Still, it might have been better and clearer, if the code had been moved (conveyed) to a special class that converted the formats of ... Then the comment would likely have been superfluous. (redundant) 
      ###
   6. ***Explanation of Intent***
      ###
      For example: When comparing two objects, the author decided that he wanted to sort objects of his class higher than objects of any others.
      ###
      So he returned 1; 
      **// we are greater because we are the right type** =)) best
      ###
   7. ***Clarification***
      ###
      TO BE CONTINUED...
      ###

      ###
   


##
## Chapter 5: Formatting

## Chapter 6: Objects and Data Structures

## Chapter 7: Error Handling

## Chapter 8: Boundaries

## Chapter 9: Unit Tests

## Chapter 10: Classes

## Chapter 11: Systems

## Chapter 12: Emergence

...
