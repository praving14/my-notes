# SUMMARY 
 
## Clean Coding Principles in C#
 - By Cory House 
https://app.pluralsight.com/library/courses/csharp-clean-coding-principles/table-of-contents

#### Key points learnt from this course:
* ##### Make sure you have the right tool for the job
* ##### Maximize Signal to noise ratio: It aids in comprehension, speeds code reading, and reduces confusions.
   * Signal : Follow the TED rule for your codes.
       * "TED Rule" : T = Terse, E = Expressive, D = Does one thing
   * Noise => 
       * "RULE OF 7" limits : Humans can hold around 7 items in a short-term memory
         So, in a basic level, at least limit 
              * (a) # of parameters per method
              * (b) # of method in a class,
              * (c) # of variable in a currently in scope
        * "DRY Principle": Don't Repeat Yourself
               -- Copy and Past is often a sign of a design problem
* ##### Try to make your code self documenting so that comments becomes more of an additional resource than a necessity
    *  #### "understanding the original programmer's intent is the most difficult problem. - Fjelstad & Hamlen 1979"
    * Self Documenting Code will have:
       * Clear Intent of what it meant to do
       * Layers of abstraction so that you can walk thorugh your code at different level of details as required
       * readable format
       * favors code over comments
       
* ##### Naming
    * Class: 
       * the name should be self-descriptive and self explanatory
    * Methods:     
       * With a good method name, a reader does not have to read the method to know what it does.
       * Avoid name warning signs such as 'And' or  'If' or  'Or'. This might be a sign that you are trying to do more than one thing in your method. May be you should consider splitting it into multiple methods. 
       * Avoid non-standard abbreviations
     * variables:
        * boolean should answer true false question as in open => isOpen or status => isActive
        * strive for symmentry for related values; symmetrical on/disable => on/off
* ##### Write conditionals that conveys intent
     * Compare booleans implicity;   if(loggedIn === true)  => if(loggedIn)
     * Assign boolean values exlicitly;   bool goingToWatchAMovie = cashInWallet > 50.00;    
     * Prefer positive conditionals;  if(!isNotLoggedIn)  => if (loggedIn)
     * Ternaries are beautiful; int ticketFee = isMale ? 0 : 50
     * Be Strongly Typed not "Stringly" typed
          * if(employeeType == 'Manager') => if (employeeType == EmployeeType.Manager) -- use enums when necessary
     * Avoid magic Number
          * if ( age > 65)   =>  const int retirementAge = 65; if(age < retirementAge);
          * if ( status == 2)  => if(status == status.ACTIVE) 
     * Handle complex conditionals ( multiple conditionals) by use of intermediate variables
     * Encapsulate complex conditionals by extracting code into another method
     * Prefer Polymorphism over enums in switch statement  -- redundant codes
     * Be declarative; sometimes Linq-to-objects provides more expressive codes thah your ad-hoc procedural lengthy codes
     * Table driven methods
          * Avoid hard coding value that changes; save it in the db
          * It is great for dynamic logic, allows changes without code deployment, avoids complex data structure, helps avoid hardcoding, and less codes


* ##### Writing clean methods
     * Create methods to: 
        * avoid duplication
        * Excessive Indentation [BIG WARNING!!!]  look out for deep nesting arrow chain codes. 
        * Convey Intent
     * Prevent Excessive Indentation by:
        * Extracting methods when required like footnotes
        * Always failing fast: Usually using gaurd clauses or default like in case of switch statement
        * Returning early
        * Conveying Intent 
        * Doing ONE and ONE thing ONLY!!
     * Mayfly Variable
         * In methods, try to declare varibale close to the first use: allows for better readabiltiy!!
     * Strive for 0-3 parameters
         * Remember the "RULE OF 7"
     * Watch out for bool paramters or flag arguments
         * It might be a strong sign a function is trying to do too many things
     * Avoid long methods. Watch out for signs such as 
         * Lots of Whitespaces and comments
         * Scrolling required
         * Difficulty coming up with consise method Names
         * multiple conditionals
         * multiple layer of abstractions
         * "Rarely over 20 lines; Rarely over 3 parameters" -- things to consider
         * "Simple functons can be longer. Complex function should be short." -- YES!!
     * Only catch exceptions that you can handle; sometimes swallowing exception is OK (rare ocassions!)
  
* ##### Writing clean Classes
    * Class responsibility should be strongly related
    * Kepp Class names specific and descriptive
         * Class with broad and generic names often grow quickly 
    * Watch out for standalone methods
    * Watch out for classes that changes too often 
         * Sometimes if a particular class is getting too much commits, maybe it is a sign that it is doing too much
    * Avoid low cohesion and Keep high cohesion
    * Classes too small -- rare scenario
         * If two classes realy heavily on each other or call a lot of each others method. maybe it is a sign that these can be merged into one class 
    * Group related data into a class
         * private void SaveUser(string firstName, string lastName, string State, string zip, string eyeColor, string phone, string fax, string maidenName) -- BAD!!
         * private void saveUser(User user) -- MUCH BETTER!!  --- RULE OF 7
 
* ##### Clean Comments:
    * Over reliance on comments might be a sign of a CODE SMELL!
    * Always pprefer Expressive Codes over Comments"
    * Comments to avoid
         * Redundant comments
         * Intent comments
         * Apology or warning comments
         * Divider Comments -- maybe REFACTOR!!
         * Brace Tracker Comments -- commonly used to mark end of long blocks -- maybe REFACTOR!!
         * Bloated header and Defect Log Comments -- not so necessary -- that informations saved somewhere else
         * ZOMBIE Codes!! --  commented out bulk codes like these increase ambiguity, and also affects searcher and refactoring!
    * Clean Comments
         * To Do
         * Summary
         * Documentation
         
* ##### REFACTORING!!
    * When to refactor?
         * refactor only codes that you are currently working on
         * If it ain't broke, dont <s>fix</s> or refactor it. 
         * Useful when you find that the code you are editing or working on is difficult to comprehend or change
    * Add tests for regression protection --THIS HELPS!! to make sure that your refactoring did not break ANYTHING!!

Robert C. Martin said:

> Leave the code you're editing a little better than you found it
