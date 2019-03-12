---
title: Get dates diff formated with momentjs
date: 'Tue, 12 Mar 2019 14:38:18 -0700'
stacks:
    - javascript
    - momentjs
---

If you need get a diff in `dateA` and `dateB` to display formated use like this:


```javascript
function getDiff(dateA, dateB) {
    var init = dateA = moment(dateA)
    var end = dateB = moment(dateB)
    
    if (dateA.unix() < dateB.unix()) {
        init = dateB
        end = dateA
    }
    
	var diff = moment(init).diff(moment(end), 'minutes')
	var time

	if (diff >= 24 * 60 || diff < 0) {
		var days = moment(init).diff(moment(end), 'days')
        diff = moment(init).subtract(days, 'days').diff(moment(end), 'minutes')
        var h = diff / 60 | 0
		var m = diff % 60 | 0

		time = `${days} ${moment.utc().hours(h).minutes(m).format('HH:mm')}` // => 1 00:00
	} else {
		var h = diff / 60 | 0
		var m = diff % 60 | 0

		time = moment.utc().hours(h).minutes(m).format('HH:mm') // => 00:00
	}

	return time // => 00:00 || 0 00:00
}
```


