[Back to index](https://github.com/UniSynTechnologies/coding-guidelines)

## Promises
Promises should be used when loading data from an external source in order to let the consumer know when data is finally loaded.

Create the "promise" object like this
```
var defer = $q.defer();
```

If an error happens in your function, you will do this to let the consumer know they need to handle an error
```
defer.reject('Something went wrong and I am telling you what the error was.');
```

If the function is successful, you will do this to tell the consumer the function is done and you can pass parameters here to send data back to the consumer
```
defer.resolve(myDataVariable);
```

At the end of your function you return the promise from the promise object like this
```
return defer.promise;
```

So an example would be like this
```
function getUserDetails() {
    var defer = $q.defer();
    User.get({}, function(userDetails, error) {
        if (typeof(error) !== 'undefined' && error.length) {
            defer.reject('Failed to load user details. ' + error);
        }
        else {
            defer.resolve(userDetails);
        };
    });
    return defer.promise;
}
```

Then when you call the function you can do this
```
getUserDetails.then(function(userDetails) {
    $scope.userDetails = userDetails;
    $scope.checkForNewsfeedPermit();
    dataLoaded();
}, function(error) {
    var loadUserDetailsErrorToast = $mdToast.simple()
        .hideDelay(9000)
        .textContent('Failed to load user details. ' + error)
        .position('top right')
        .parent(angular.element("#adminContent"))
        .toastClass('loadUserDetailsErrorResponse');
    $mdToast.show(loadUserDetailsErrorToast);
});
```
The first function is the resolve success function and the second is the reject error function.
