# SUMMARY 
 
## Clean Coding Principles in C#
 - By Cory House 
https://www.pluralsight.com/

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
    *  #### "understanding he original programmer's intent is the most difficult problem. - Fjelstad & Hamlen 1979"
    * Self Documenting Code will have:
       * Clear Intent of what it meant to do
       * Layers of abstraction so that you can walk thorugh your code at different level of details as required
       * readable format
       * favors code over comments
       
* ##### Naming
    * Class: 
       * the name be self-descriptive and self explanatory
    * Methods:     
       * With a good method name, a reader does not have to read the method to know what it does.
       * Avoid name warning Signs such as 'And' or  'If' or  'Or'. It is sign that you are trying to do more than one thing in your method. May be you should consider splitting it into multiple methods. 
       * Avoid non-standard abbreviations
     * variables:
        * boolean should answer true false question as in open => isOpen or status => isActive
        * strive for symmentry for related values; symmetrical on/disable => on/off
* ##### Write conditionals that conveys intent
