# Clean Code - Robert C. Martin

   - Not a **feel good** book.
   - Learning Craftsmanship:
      - Knowledge (principles, patterns, practices, heuristics)
      - Work (Hard work, must sweat over it, watch others fail).
   ###
***

## Chapter 1: Clean Code

   1. ***There Will Be Code***
   
      ####
      -  We will never be rid of code (because code represents the details of the requirements and can not be ignored or abstracted, they have to be **specific**).
      -  Machines will not adapt what we need. So **there will always be code**.
      ####
   
   2. ***Bad Code***

      ####
      - Trying to go fast? In a rush?
      - Tired of working on a program and want it to be over ?
      - You choose to leave it for another day? 
      - Feel relief of seeing the messy program work?
      - Feel **working mess is better than nothing**?
      - But ... **Later equals never**!
      ####
   
   3. ***The Total Cost of Owning a Mess***

      ####
      Over time the mess becomes so big and deep and so tall, we can not clean it up. There is no way at all.
      ####

      <p align="center">
         <img src="images/chapter1/image1.png" />  
      </p> 

      ####
      Driving the productivity ever further toward ZERO
      ####

      3.1. ***The Grand Redesign in the Sky***
      ####
      3.2. ***Attitude***
      
      ####
      - If you don't do what the manager says, you'll be fired? Probably not!
      - Like a doctor with a durty hand? 
      - So too it's unprofessional for programmers to bend to **the will of managers who don't really understand the risks of making messes.**
      ####

      3.3. ***The Primal Conundrum*** [Primitive]
      ####
      The only way to make the deadline - the only way to go fast - is to keep the code as clean as possible at all times.
      ####

      3.4. ***The Art of Clean Code***
      ####
      - A programmer ***without "code-sense"*** can look at a messy module and recognize the mess *but will have no idea what to do about it.*
      #####
      - A programmer ***with "code-sense"*** will look at a messt module and see *OPTIONS & VARIATIONS*
      #####
      - In short, a programmer who writes clean code is an artist who can take a blank screen through a series of transformations **until it is an elegantly coded system.**
      ####

      3.5. ***What Is Clean Code?***
      ####
      - Some keywords: *elegant, efficient, straightforward logic, does one thing, simple, direct, well-written prose, create tensions, can be read, enhance by others, one way rather than many ways for doing one thing, proper error handling, clear and minimal API, CARE, runs all the tests, no duplication, minimize the number of entities (classes, methods, functions), make it looks like a language was made for the problem, make it simple as hell =))*
      ####

   4. ***School of Thought***
      ####
      - There are other school, other masters out there that have as much claim to professionalism as this book authors.
      - Something would be very controversial. Probably not agree with all of them.
      - The recommendations in this book are things they have thought long and hard about. They have learned them through decades of exprience and repeated trial and error. Thus, **whether you agree or disagree. it would be a shame if you did not see, and respect, their point of view.**
      ####

   5. ***We Are Authors***
      ####
      - Basically, authors are responsible for communicating well with their readers. The next time you write a line of code, remember you are an author, writing for readers who will judge your effort.
      - *The code you are trying to write today will be hard or easy to write depending on how hard or easy the surrounding code is to read. So if you want to go fast, if you want to get done quickly, **if you want your code to be easy to write, make it easy to read***
      ####

   6. ***The Boy Scout Rule***
      ####
      **"Leave the campground cleaner than you found it"**
      ####
      - It's not enough to write the code well. The code has to be kept clean over time. We've all seen code **rot** and **degrade** as time passes.
      - Checked-in our code a litter cleaner than we checked it out. -> not rot anymore
         - Change one variable name for the better
         - Break up one function that's a little too large
         - Eliminate one small bit of duplication
         - Clean up one composite *if* statement
      ####

   7. ***Conclusion***
      ####
      - This book can not make you a good programmer. Can not give the "code-sense"
      - **This book shows the thought processes, the tricks, techniques, and tools**
      - You will se good code and you will see bad code. You will see bad code transformed into good code.
      - You will see lists of heuristics, disciplines and techniques.
      - You will see a butt-load of code, example after example.
<<<<<<< HEAD
      - **PRACTICE MAKES PERFECT !!!**
      ##
 
=======
      - **PRACTICE MAKES PERFECT!**
      ###
***
>>>>>>> 7406c8ab2631ef636f687d760564b556c11bbd3d
## Chapter 2: Meaningful Names
   ###
   0. ***Introduction***
      #####
      - We name our variables, our functions, our arguments, classes and packages.
      - We name our source files and the directories.
      - We name our .jar file and .war file
      - name and name and name...
      #####
   1. ***Use Intention-Revealing Names*** (Tên thể hiện được ý định)
      #####
      - *"Choosing good names takes time but saves more than it takes"*
      - The problem is not the **simplicity** of the code but the **implicity** of the code (The degree to which the context is not explicit in the code itself)
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
      - The code implicitity requires that we know the answers to questions:
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
      - Notice that the simplicity of the code has not changed. It still has exactly the same number of operators and constants, with exactly the same number of nesting levels. ***But the code has become much more explicit.***
      ###

   2. ***Avoid Disinformation*** (false information - delibaretely)
      #####
      - *hp, aix* and *sco* would be poor variable names because they are the names of Unix platforms or variants. Even if you are coding a hypotenuse and *hp* looks like a good abbreviation, it could be **disinformative**.
      #####
      - *accountList* but not actually a *List* - *accountGroup, bunchOfAccounts* or just plain *accounts* would be better.
      #####
      - How long does it take to spot the subtle difference between a *XYZFindingSomethingInterestingToAddToTheStorage* in one module and elsewhere a little more distant, *XYZFindingSomethingInterestingToSearchInStorage*.
      #####
         ```java
            int a = 1;
            if(O == 1) 
               a = O1;
            else
               l = 01;
         ```
   ##
   3. ***Make Meaningful Distinctions*** (Difference)
      #####
      - Number-series naming (a1, a2, .. aN) is not disinformative - they are **noninformative**, they provide no clue to the author's intention. 
      ###
      ```java
      public static void copyChars(char a1[], char a2[]) {
            for (int i = 0; i < a1.length; i++) {
               a2[i] = a1[i]; //nonsense
            }
      }
      ```
      ###
      - Noise words: class *Product*. If you have another called *ProductInfo* or *ProductData*, you have made the names different without making them mean anything different. - so, *Info* and *Data* are indistinct noise words like *a, an* and *the*      
      #####
      - The word **variable** should never appear in a variable name. The word **table** should never appear in table name. How is **NameString** better than **Name**? Imagine finding one class named **Customer** and another named **CustomerObject**. What should you understand as the distinction? Which one will represent the best path to a customer's payment history? 
      #####
      - **moneyAmount** is indistiguishablle from **money**, **customerInfo** is indistinguishable from **customer**,  **accountData** is indistinguishable from **account** and **theMessages** is distinguishable from **message**. Distinguish names in such a way that the reader knows what the differences offer. 
      ##
   4. ***Use Pronounceable Names***
      #####
      - If you can not pronounce it, you can not discuss it without sounding like an idiot. "Well, over here on the bee cee arr three cee enn tee we have a pee ess zee kyew int, see?" This **matters** beacause programming is a social activity.
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
      - Now, this conversation is now **possible** "Hey, Shawn, take a look at this recored! The generation timestamp is set to tomorrow's date! How can that be? =)) "
      ##
   5. ***Use Searchable Names***
      #####
      - Single-letter names can *ONLY* be used as local variables inside short methods. 
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
      - *WORK_DAYS_PER_WEEK* is much easier to find than all the places where **5** was used and filter the list down to just the intances with the intended meaning.
      ##
   6. ***Avoid Encodings***
      #####
      
      #####


   ###


## Chapter 3: Functions

## Chapter 4: Comments

## Chapter 5: Formatting

## Chapter 6: Objects and Data Structures

## Chapter 7: Error Handling

## Chapter 8: Boundaries

## Chapter 9: Unit Tests

## Chapter 10: Classes

## Chapter 11: Systems

## Chapter 12: Emergence

...