
# steveml-language README

  

## Features

  

Syntax highlighting for SteveML, a personal markup language used by yours truly for writing dialogue trees for games

  

## Usage

  

SteveML is an extremely simple markdown format with only four concepts:
* Scene Headers
* Actors
* System Calls
* User Choices

There are no delimiters in SteveML, and it instead relies on proper indentation

### Scene Headers
Scene headers mark the beginning of a scene. All content below the scene header is considered part of the scene until the next scene header is found. A scene header looks like so:

    ##MY_SCENE
This defines a new scene called MY_SCENE which can then be referenced by system calls, or however else the developer sees fit
### Actors
Actors are used to indicate who is speaking the lines in a scene. An actor is one indentation deep into a scene, and their spoken lines are two indentations deep. 
Example:

    ##MY_SCENE
		THE actor™
			wow
			i am speaking the dialogue
		other actor
			very cool

### System Calls
System calls can be used for various things, but currently they are only used for pointing to scenes, setting variables, and conditionally rendering dialogue. A system call is prefixed by two colons (::) followed by an instruction, with all subsequent arguments being separated by two colons (::). Currently supported instructions are:
* GOTO
	* Goes to a scene header
* SET
	* Sets a variable to either TRUE or FALSE
* IF/ELIF/ELSE/ENDIF
	* Conditional statements

Example:

    ##MY_SCENE
	    ::SET::MY_VARIABLE::FALSE
	    ::SET::MY_OTHER_VARIABLE::TRUE
	    ::IF::MY_VARIABLE
		THE actor™
			hey! MY_VARIABLE is true!
		::ELIF::MY_OTHER_VARIABLE
		THE actor™
			hey! MY_VARIABLE was false...
			but at least MY_OTHER_VARIABLE is true!
		::ELSE::
		THE actor™
			this sucks! none of my variables were true!!
		::ENDIF::
		other actor
			yeah man that does suck, sorry to hear.
			well, guess we better get on to the next scene
		::GOTO::MY_OTHER_SCENE
			
### User Choices  
User choices are ways to branch the dialogue tree based on user input. A user choice is surrounded by two starting and ending angle brackets (<<>>), with the text between them being the label for the option. A user choice should have either a GOTO or a SET system call indented on the line below it. 
Example:

    ##MY_SCENE
	    THE actor™
		    user... you must choose
		    do you want to continue the scene, or go somewhere else?
	    <<continue>>
		    ::NULL::
		<<continue with rizz>>
		    ::SET::RIZZIN::TRUE
		<<go to another scene>>
			::GOTO::MY_OTHER_SCENE
		::IF::RIZZIN
		THE actor™
			oh... wow. that's, um, unique.
			yeah you know i totally forgot i have somewhere else to be
			that's like, not here
			so uhhh, i'm gonna leave now. bye.
		::GOTO::END
		::ENDIF::
		THE actor™
			it seems you chose to continue. a bold choice
			but choice is an illusion, so we're going to the other scene anyway.
		::GOTO::MY_OTHER_SCENE
		
## Release Notes

  

Users appreciate release notes as you update your extension.

  

### 1.0.0

  

Initial release of SteveML

  

## For more information

  

* Contact me on Discord (@nanospectro)