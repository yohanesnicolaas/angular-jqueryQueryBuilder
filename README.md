# angular-jqueryQueryBuilder

Angular directive for popular jquery plugin "jQuery query builder" (see https://github.com/mistic100/jQuery-QueryBuilder)

### Dependencies
 * Angular >= 1.3.0
 * jQuery >= 1.10
 
### Install
 
 - via bower: by running `$ bower install angular-jq-querybuilder` from your terminal
 
### Usage

Use folowing directive:

```html
<query-builder options="options" builder="qb"></query-builder>
```

### Attributes

#### options
Required attribute, plain js object. The same object as you use to initialize jQueryQueryBuilder with filters, rules and other fields: 
```js
$('#builder').queryBuilder({
    filters: [ ... ]
});
```

#### builder
Not required, plain js object. After builder initialization is completed will be populated by by property .builder which will contain builder object

### Enhancement

#### Additional events
- QueryBuilderValueChanged. Event fires after any changes in builder values has happened (value is changed, rule/group is added/deleted, operator is changed, group condition is changed)

### Notes

Please note that 2-way binding is not implemented so changes in 'options' attribute don't lead to builder update. You have to handle it by yourself:

- After rules change just call queryBuilder.setRules(newRules) method
- After any other options change (for instance in filter) you need to reinstantiate builder (because there is no API in jquery). The simpliest way to do this is add nd-if into directive and switch it to fals eand then back to true:

```html
<query-builder ng-if="builderVisible" options="options" builder="qb"></query-builder>
```

```js
reinitializeFilter = function() {
  scope.builderVisible = false
  $timeout(function() {
    return $scope.builderVisible = true;
  }, 50);  
}
```
