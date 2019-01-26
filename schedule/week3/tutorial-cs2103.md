## Admin matters
**Team forming**: We will form teams at the beginning of the tutorial. Be sure to arrive on time.

<panel src="../../admin/project-teams.md#main" header="Admin {{ icon_embedding }} Team Forming :star:" minimized />

**All students**: 
* Confirm your team ID with the tutor. It should be of the form `TUTORIAL_ID-TEAM_NUMBER` e.g. `W09-1` (`W`ed `09`00 slot, team `1`)


## Suggested tutorial activities

### Coding standards
Consider the code given below:
```java
import java.util.*;

public class Task {
    public static final String descriptionPrefix = "description: ";
    private String description;
    private boolean important;
    List<String> pastDescription = new ArrayList<>(); // a list of past descriptions

    public Task(String d) {
      this.description = d;
      if (!d.isEmpty())
          this.important = true;
    }

    public String getAsXML() { return "<task>"+description+"</task>"; }

    /**
     * Print the description as a string.
     */
    public void printingDescription(){ System.out.println(this); }

    @Override
    public String toString() { return descriptionPrefix + description; }
}
```

Identify some basic coding standard violations.

### Refactoring

In Addressbook Level 1, apply the following refactorings, where applicable. Use the IDE to aid refactoring.
1. [Consolidate Conditional Expression](https://refactoring.com/catalog/consolidateConditionalExpression.html)
2. [Decompose Conditional](https://refactoring.com/catalog/decomposeConditional.html)
3. [Inline Method](https://refactoring.com/catalog/inlineMethod.html)
4. [Remove Double Negative](https://refactoring.com/catalog/removeDoubleNegative.html)
5. [Replace Magic Number with Symbolic Constant](https://refactoring.com/catalog/replaceMagicNumberWithSymbolicConstant.html)
6. [Replace Nested Conditional with Guard Clauses](https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html)
7. [Replace Parameter with Explicit Methods](https://refactoring.com/catalog/replaceParameterWithExplicitMethods.html)
8. [Reverse Conditional](https://refactoring.com/catalog/reverseConditional.html)
9. [Split Loop](https://refactoring.com/catalog/splitLoop.html)
10. [Split Temporary Variable](https://refactoring.com/catalog/splitTemporaryVariable.html)

