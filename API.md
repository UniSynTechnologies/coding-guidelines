[Back to index](https://github.com/UniSynTechnologies/coding-guidelines)

## Concepts
### Method / Endpoint parameters
All methods / endpoints should be structured to answer 3 questions:  
"who" "what" and "where"  
3 easy questions every method / endpoint should ask.  
  
Sometimes methods like those that delete records have the what answered by the name. It is a delete method so the what is that it deletes. So you just pass "who" and "where"
In the case of a delete method:
```
Who, passed as a parameter, is the "who is getting deleted"
What, determined by the name of the method, is the "what we are doing is deleting"
Where, passed as a parameter, is the "on which accountID or siteID does the record exist"
```
In the case of an edit method:
```
Who, passed as a parameter, is the "who is getting edited"
What, passed as a parameter, is the "what are we editing on the record"
Where, passed as a parameter, is the "on which accountID or siteID does the record exist"
```

### Globals and how / where to use them
$GLOBALS should be used inside methods for non optional non flexible properties such as "the user who edited the record".  
The data in the globals object is populated by the API at a system level. Data like user details and the account ID requesting the API are determined by the API keys being used as a security measure. Passing globals as a parameter to a method instead of systematically using it internally opens the potential for a security flaw if someone passes user details or an account id that they do not have access too. You would have to do extra security checks to confirm they have access to the parameter value in order to close the security hole. These checks would not be needed by 99% of use cases where they are using the user details or accountID assigned to them by the system and so would just introduce unnecessary processing overhead in order to allow the extremely rare use case of needing to override the globals.
