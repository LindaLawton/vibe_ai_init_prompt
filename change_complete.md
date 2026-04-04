# after the AI has address an issue.  
When the AI has addressed the issue, or maybe i should say when it says it has addressed the issue.  I have found it is often not done.  
- There may be bugs
- Things it left unfinished
- Unit tests not passing
- Things it did not consider
- Not following best practice.

# Fix

to address this i like to have the AI check itself.  I send it this prompt
```
I would like you to now. 
	1. check the work you just did. 
		a. Verify that all the changes were completed as they should be.
		b. Ensure that you have followed best practice.
		c. Ensure that your changes have not effected other parts of the system.
		d. Ensure that you did not forget anything.
		e. Ensure that we are not leaving our self open for something that might bite us in the butt in the future.
		f. Ensure that all unit tests needed to fully test the feature were created.
		g. Ensure that all unit tests pass not just the ones you created for this feature.
```

# Usage.

Evertime it finds something i tell it to keep reviewing its self with the above prompt. Nomrally it takes two or three runs for it to agree its done.  That will depend greatly on the size of the change.
