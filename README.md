angular-google-places-autocomplete
================

Angular directive for the Google Places Autocomplete component.

Installation
------------

Install via bower: `bower install angular-google-places-autocomplete-callback`

Or if you're old skool, copy `src/autocomplete.js` into your project.

Then add the script to your page (be sure to include the Google Places API as well):

```html
<script src="https://maps.googleapis.com/maps/api/js?libraries=places"></script>
<script src="/bower_components/angular-google-places-autocomplete/src/autocomplete.js"></script>
```

You'll probably also want the styles:

```html
<link rel="stylesheet" href="/bower_components/angular-google-places-autocomplete/src/autocomplete.css">
```

Usage
-----

First add the dependency to your app:

```javascript
angular.module('myApp', ['google.places']);
```

Then you can use the directive on text inputs like so:

```html
<input type="text" g-places-autocomplete ng-model="myScopeVar" />
```

The directive also supports the following _optional_ attributes:

* forceSelection &mdash; forces the user to select from the dropdown. Defaults to `false`.
* options &mdash; See [google.maps.places.AutocompleteRequest object specification](https://developers.google.com/maps/documentation/javascript/reference#AutocompletionRequest).

**The original directive fires an event called "g-places-autocomplete:select" with the prediction as parameter. My patch adds the possibility to add a callback when that event is fired, ie: when a new place is selected.
To use it, just add an attribute: on-place-updated="myCallback(prediction)" to your directive. In your controller, define $scope.myCallback(place). That function will be called every time a new place is selected from the directive.

eg.

html:
```html
<input type="text" name="address" on-place-updated="vm.googlePlaceComponentsFilter(place)"  ng-model="vm.contact.addresses[0].address_line_1" g-places-autocomplete/>
```

controller:
```javascript
        vm.googlePlaceComponentsFilter = googlePlaceComponentsFilter;
        function googlePlaceComponentsFilter(place){
            //do whatever you want to do with place data.
            console.log(place);
        }
```
Examples
--------

* [Basic](example/basic.html)
* [Options](example/options.html)
* [Force selection](example/force-selection.html)
* [Custom Places](example/custom-places.html)

Issues or feature requests
--------------------------

Create a ticket [here](https://github.com/kuhnza/angular-google-places-autocomplete/issues)

Contributing
------------

Issue a pull request including any relevant testing and updated any documentation if required.
