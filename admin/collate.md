
1.  Download `Collate-TUI.jar` from the [Collate Tool project](https://github.com/se-edu/collate).
2.  Mark your code with a `//@@author github-ID`. Note the double `@`. The comment syntax may vary based on file type e.g. for markdown, fxml, html
    ```
    <!-- @@author github-ID -->
    ```

    Here is a sample code file:
    ```
    //@@author johndoe
    method 1 ...
    method 2 ...
    //@@author sarahkhoo
    method 3 ...
    //@@author johndoe
    method 4 ...
    ```
3.  The `//@@author` tag should appear only at the beginning of the code a person wrote. The code up to the next `//@@author` tag or the end of the file (whichever comes first) will be considered as was written by that author.  
    However, you may put an empty `//@@author` (i.e. no GitHub ID) to indicate the end of the code segment you wrote, if you don't know who wrote the code segment below yours. The author of that code segment can add the GitHub ID to the empty tag later.
    
4. ==Claim only significant size code blocks that can be reviewed on its own== %%&nbsp;e.g., a class, a sequence of methods, a  method, a block of statements, a composite statement such as a loop or an if-else statement%%. If a code block was touched by more than one person, the `//@@author` tag should indicate the person who wrote most of that code block. 
   * :exclamation: We recommend that you **do not claim credit for tiny/trivial code fragments** as it will pollute your code with too many `@@author` tags.
   * If an enhancement required you to do tiny changes in many places, there is no need to collate all those tiny changes; you can describe those changes in the Project Portfolio page instead. 
   * :bulb: GitHub has a [_blame_ feature and a _history_](https://help.github.com/articles/tracing-changes-in-a-file/) feature that can help you determine who wrote a piece of code.     
   
5.  Do not put the `//@@author` inside java header comments as only the content below that tag will be collated.<br>
    :-1::arrow_heading_down:
    ```
    /**
      * Returns true if ...
      * @@author johndoe
      */
    ```
    :+1::arrow_heading_down:
    ```
    //@@author johndoe
    /**
      * Returns true if ...
      */
    ```
6.  If you wrote a significant amount of code that was not used in the final product,
    * Create a folder called `{project root}/unused`
    * Move unused files (or copies of files containing unused code) to that folder. 
    * use `//@@author github-ID` to mark unused code in those files.
    
    e.g.
    ```
    //@@author johndoe-unused
    method 1 ...
    method 2 ...
    ```
    
    Please put a comment in the code to explain why it was not used. 
    
7.  ==The `//@@author` tag should be used to mark *all* code/test you claim credit for. There is no need to mark documentation files.==
  You will be penalized if you try to boost the length of your collated files using dubious means such as duplicating the same code in multiple places. In particular, do not copy-paste test cases to create redundant tests. Even repetitive code blocks within test methods should be extracted out as utility methods to reduce code duplication.  
  Individual members are responsible for making sure their own collated files contain the correct content.  
  If you notice a team member claiming credit for code that he/she did not write, you can email us (after the final submission) to let us know.

  * **INCLUDE**: 
    * **All code/test-related work you contributed**. e.g. comments, test code, styling (e.g. css), xml, even test data files. But do not include chunks of text that were trivially copy pasted e.g. a test data file with 1000 persons that was used to test performance.
    * **Code you reused** from elsewhere: Mark such code as `//@@author github-ID-reused`
  
      e.g.
  
      ```
      //@@author johndoe-reused
      method 1 ...
      method 2 ...
      ```
  * **EXCLUDE** 
    * **Documentation files** (User guide, Developer guide etc.). Those will be evaluated under a different category.
    * **Code generated by the IDE/framework.** You may also mark such code `//@@author generated`

      e.g.       

      ```
      //@@author generated
      method 1 ...
      method 2 ...
      ```
    * **Code you modified in minor ways** e.g. adding a parameter. These can be left out of collated code but can be mentioned in the Project Portfolio page if you want to claim credit for them.
    

8. You need to put the,   
   * collated functional code in `collated/main` folder,
   * collated test code in `collated/test` folder, and
   * collated unused code in `collated/unused` folder
   
   Given below are DOS sample commands you can put in a batch file and run it to collate the code.
   
   ```
   java -jar Collate-TUI.jar collate from src/main to collated/main include java, fxml, css
   
   java -jar Collate-TUI.jar collate from src/test to collated/test include java
   
   java -jar Collate-TUI.jar collate from unused to collated/unused include java, fxml, css
   ```
   
   The output should be something like the structure given below.
   
   ```
   collated/
       main/
           johndoe.md
           sarahkhoo.md
           ravikumar.md
           ravikumarreused.md
       test/
           johndoe.md
           sarahkhoo.md
           ravikumar.md
       unused/
           johndoe.md
   ```

9. After running the collate tool, you are recommended to look through the generated **.md** files to ensure all your code has been extracted correctly. 

10. ==Push the *.md files created to a folder called /collated== in your repo.
