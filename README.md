# angular-reactor

(Placeholder) extremely lightweight implementation of the Flux pattern for Angular 1.*

## Example

```
angular.module(‘myApp’, [’reactor’])
.factory(‘glomStore’, function($reactor) {
	var reactor = $reactor.$new();
	reactor.handle(‘happen’, function(x) {
		reactor.commit({
			happened: true
		})
	})
	return reactor.store;
})
.controller(‘glomController’, function($scope, $reactor, glomStore) {
	glomStore.bind($scope, ‘glom’)
	$scope.select = function select() {
		$reactor.dispatch(‘happen’)
	}
})
```

## API's

```
$reactor.create() —> reactor
$reactor.dispatch(eventType)
reactor.handle(eventType, Function(eventData))
reactor.commit(Object)
reactor.store.bind(Scope, scopeVariableName)

```
