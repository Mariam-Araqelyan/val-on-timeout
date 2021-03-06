val-on-timeout
==============

val-on-timeout improves the user experience for forms.  When the user has stopped activity in a field, validation errors will be displayed.

## Features

* Configurable timeout after pause in typing
* Configurable timeout on focus
* Configurable timeout on blur

## Usage

Simply include as a dependency in your module.

```js
angular.module('SuperAwesomeApp', ['calendee.valOnTimeout'])
```

## Examples

### Detect When User Stops Typing
NOTE : The default timeout for typing is 1250ms.

```html
<input
        type="text"
        placeholder="Your First Name Please"
        name="givenName"
        ng-model="user.givenName"
        ng-minlength="10"
        ng-maxlength="100"
        ng-required="true"
        val-on-timeout
/>

<small class="error" ng-show="testing.givenName.$error.minlength && testing.givenName.$timedout">We don't accept people with short names. Go big or go away.</small>
<small class="error" ng-show="testing.givenName.$error.maxlength && testing.givenName.$timedout">That name is super long.  We don't like you.  Go away.</small>
<small class="error" ng-show="testing.givenName.$error.required && testing.givenName.$timedout">People with no names don't exist.  Go away.</small>

```

### Detect When User Stops Typing With Custom Timeout Limit

```html
<input
        type="text"
        placeholder="Your First Name Please"
        name="givenName"
        ng-model="user.givenName"
        ng-minlength="10"
        ng-maxlength="100"
        ng-required="true"
        val-on-timeout
        typing-limit="2000"
/>

<small class="error" ng-show="testing.givenName.$error.minlength && testing.givenName.$timedout">We don't accept people with short names. Go big or go away.</small>
<small class="error" ng-show="testing.givenName.$error.maxlength && testing.givenName.$timedout">That name is super long.  We don't like you.  Go away.</small>
<small class="error" ng-show="testing.givenName.$error.required && testing.givenName.$timedout">People with no names don't exist.  Go away.</small>

```

### Detect When Field Has Had Focus For Too Long

If a user focuses on a field but fails to begin typing, the timeout can be detected.
The default focus timeout is 5000ms.  It can be configured by providing any value with the attribute.

```html
<input
        type="text"
        placeholder="Your First Name Please"
        name="givenName"
        ng-model="user.givenName"
        ng-minlength="10"
        ng-maxlength="100"
        ng-required="true"
        val-on-timeout
        typing-limit="2000"
        focus-limit="3000"
/>

<small class="error" ng-show="testing.givenName.$error.minlength && testing.givenName.$timedout">We don't accept people with short names. Go big or go away.</small>
<small class="error" ng-show="testing.givenName.$error.maxlength && testing.givenName.$timedout">That name is super long.  We don't like you.  Go away.</small>
<small class="error" ng-show="testing.givenName.$error.required && testing.givenName.$timedout">People with no names don't exist.  Go away.</small>

```

### Detect When Field Blurred

If a field loses focus, you can apply the timeout to display errors.
The default focus timeout is 500ms.  It can be configured by providing any value with the attribute.

```html
<input
        type="text"
        placeholder="Your First Name Please"
        name="givenName"
        ng-model="user.givenName"
        ng-minlength="10"
        ng-maxlength="100"
        ng-required="true"
        val-on-timeout
        typing-limit="2000"
        focus-limit="3000"
        blur-limit="750"
/>

<small class="error" ng-show="testing.givenName.$error.minlength && testing.givenName.$timedout">We don't accept people with short names. Go big or go away.</small>
<small class="error" ng-show="testing.givenName.$error.maxlength && testing.givenName.$timedout">That name is super long.  We don't like you.  Go away.</small>
<small class="error" ng-show="testing.givenName.$error.required && testing.givenName.$timedout">People with no names don't exist.  Go away.</small>

```

## Demo
To run a demo, start a local Python server from the repository's root directory :

```
python -m SimpleHTTPServer 3001
```

Then, go to : http://localhost:3001/example/

## Testing
From the project root directory, run `karma start`.

## Authors

**Justin Noel**

+ <https://twitter.com/calendee>
+ <https://github.com/calendee>

## Acknowledgements
Thanks to Ari Lerner (@auser) for the inspiration for this directive.  His ngFocus directive lead the way.

I whined about my complaints with Angular JS validation to Sharon DiOrio (@sharondio) while at #ng-conf.  She didn't take pity and suggested I do something about it.  Thanks for the push.

## LICENSE

val-on-timeout is licensed under the MIT Open Source license. For more information, see the LICENSE file in this repository.