---
title: Update url search without reload
date: 'Thu, 7 Mar 2019 10:47:17 -0800'
stacks:
    - javascript
    - vue
    - angularjs
---

Searching how I can update window location search query with `vuejs router`, I found that it is not exactly possible, since the components are recharged and the seam with the property `this.$route.query` for get the new value.

This has a problem when you only ned update a query search value to only view or when user go to another part of you page and go back (or reload same page) get same info.

But I know it's possible, I used in `AngularJS` like this


```javascript
$state.go($state.current, {}, { reload: true })
```


So, if it's possible in Angularjs, I can use in `Vuejs` or in `vanilla`, and that I did.

Using browser propertyes I can change the state url without reload the page, the problem has been vue don't detect the change in current view, so the value in `this.$route` it's same and don't updated. But it's not a problem when you only need update this state to recobery data on reload or go back from next stage.


```javascript
import queryString from 'queryString' // Used for convert data object/array to string query

/**
 * @method $updateState
 * @param {String} path - Current path like 'users' = '/users'
 * @param {Object | Array} data - Data to query value
 */

function $updateState(path, data) {
    var url = `${path}?${queryString.stringify(data)}` // => 'user?page=1&perPage=10'
    history.pushState(url)
    return
}
```


And that is all, now you can update any page url without reload currentView.


