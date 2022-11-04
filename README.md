# rrule.js-cheat-sheet
rrule.js cheat sheet with the most needed stuff..


<br><br>
<br><br>








## parseString

<br><br>

### Parse rrule string, change dtstart and then create new rrule object
```javascript
var options = RRule.parseString('FREQ=DAILY;INTERVAL=6')
options.dtstart = datetime(2000, 2, 1)
var rule = new RRule(options)
```


<br><br>
<br><br>
_________________________________________________________
_________________________________________________________

<br><br>
<br><br>


## rrulestr

<br><br>

### Parse a RRule string, return a RRule object

```
// Parse a RRule string, return a RRule object
rrulestr('DTSTART:20120201T023000Z\nRRULE:FREQ=MONTHLY;COUNT=5')

// Parse a RRule string, return a RRuleSet object
rrulestr('DTSTART:20120201T023000Z\nRRULE:FREQ=MONTHLY;COUNT=5', {
  forceset: true,
})

// Parse a RRuleSet string, return a RRuleSet object
rrulestr(
  'DTSTART:20120201T023000Z\nRRULE:FREQ=MONTHLY;COUNT=5\nRDATE:20120701T023000Z,20120702T023000Z\nEXRULE:FREQ=MONTHLY;COUNT=2\nEXDATE:20120601T023000Z'
)
```


















<br><br>
<br><br>
_________________________________________________________
_________________________________________________________

<br><br>
<br><br>









## .all()

<br><br>

### Get Array with dates from RRule string
```javascript
const rrule = 'DTSTART:20120201T023000Z\nRRULE:FREQ=MONTHLY;COUNT=5'
const rule = RRule.fromString(rrule)
const allRules = rule.all()
```

<br><br>


### Filer not needed dates from all rules array
```javascript
// Remove rules which are in included in array skipped
const filteredRules = allRules.filter(date => {
    const dateString = date.toISOString()

    // Check if skipped rule is same like current rule date
    const foundSkippedRules = skipped.filter(rule => {
        // Push when skipped rule is equal to date 
        const res = rule === dateString ? rule : false
        return res
    }) 

    // Push date to filteredRes when checkSkipped is empty
    const res = _.isEmpty(foundSkippedRules) ? date : false
    return res
})
```















