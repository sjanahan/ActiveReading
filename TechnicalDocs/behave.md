# Pre-reading questions
## 1. What will the text be about?
* A getting started guide to behave tests. What they are, what the different parts mean
## 2. What questions am I looking to answer?
* What exactly is a behave test?
* What exactly is the given, when, and then clauses?
* How do I run a behave test
* How do I incorporate them into my existing Flask Application?
* How do I choose what to write behave tests about?
## 3. What do I know about the topic already?
* They have a given, when, and then clause
* They are form of integration testing
* They can be used in conjunction with a Flask application
## 4. Skim the text to get an idea for the structure of the text
* Seems to be interspersed with definitions and then snippets of code to use to try out the sections.
    
# During reading notes
## 1. Turn headers and sub-headers into questions. After a meaningful chunk, take the time to summarize the major points
###### 1. How does behave work?
* We have a `feature` file with a description of what should happen
* We have a `steps` file to define English to code translation
* We run behave at the command line

###### 2. What are features?
* They describe how a piece of the application should work
* This is the minimum setup:
    ```
    features/
    features/everything.feature
    features/steps/
    features/steps/steps.py
    ```
* Can run behave with a `-v` flag for more verbose output

###### 3. What are feature files?
* Has a natural language format describing a feature or part of a feature with representative example of expected outcomes
* Given - a known state of the system BEFORE the user starts interacting
* When - we take a key action. This is the interaction with the system
* Then - we observe outcomes

###### 4. What are scenario outlines?
* Sometimes a certain scenario should be run with a set of known states
* You can use a scenario outline to achieve this

###### 5. What is step data?
* You can use scenario outlines inline with a step. It will be available in the .text attribute of the context object

###### 6. What are python steps? How are they implemented?
* Corresponding python code to execute for the features
* Must be in the steps directory
* If you use an `and` or `but` those will get internally converted into the decorator that preceded it

###### 7. What are step parameters?
* You can parameterize very common phrases
```
    Scenario: look up a book
      Given I search for a valid book
       Then the result page will include "succe
    Scenario: look up an invalid book
      Given I search for a invalid book
       Then the result page will include "failure"
```
With the corresponding steps.py
```
@then('the result page will include "{text}"')
def step_impl(context, text):
   if text not in context.response:
       fail('%r not in %r' % (text, context.response))
```
* There are several parsers: parse, cfparse, and re.
* You can specify which parser to use with the following directive
    
    ``` use_step_matcher(parser) ```
    
###### 8. What is a context?
* It's an object that allows you to share data with behave.
* It has layers to it - think of it as scope bound
* Behave adds the following attributes to the context: table, text, failed
* The context variable in all cases is an instance of behave.runner.Context.

###### 9. What are the Environmental Controls?
* Can define steps to run before or after all steps/scenarios/tags/features

###### 10. How can I control things with tags?
* Scenarios can be annotated and then those tags can be passed to behave as a command line parameter
```behave --tags=–tags=wip,slow```

###### 11. What is Works in Progress?
* Can pass -w to behave to run only those scenarios which are marked with @wip

###### 12. What does debug on error do?
* It starts the debugger automatically if any step fails
* Should only be enabled if running interactively

# Post reading
1. Come up with a few questions that you'd ask someone else to gauge how well they comprehended the text.
    * What is behave?
    * What are the core components of behave?
    * What do the given, when, and then steps describe?
    * How do feature files get turned into executables?
    * What is the context?
    * What are some different ways we can parameterize our feature files?
    * How does setup and teardown work in behave?
    * What are tags and how are they helpful?
    * What does the -w flag do in behave?
    * What is the debug on error functionality?
