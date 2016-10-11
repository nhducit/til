# til

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse


```
Given a date string of "March 7, 2014", parse() assumes a local time zone, but given an ISO format such as "2014-03-07" it will assume a time zone of UTC (ES5 and ECMAScript 2015). Therefore Date objects produced using those strings may represent different moments in time depending on the version of ECMAScript supported unless the system is set with a local time zone of UTC. This means that two date strings that appear equivalent may result in two different values depending on the format of the string that is being converted.
```
  
```
new Date("2016-07-15")
Fri Jul 15 2016 07:00:00 GMT+0700 (ICT)
new Date("2016-7-15")
Fri Jul 15 2016 00:00:00 GMT+0700 (ICT)
```

```
moment("2016-07-15").format()
"2016-07-15T00:00:00+07:00"
moment("2016-7-15").format()
global.js:282 Deprecation warning: value provided is not in a recognized ISO format. moment construction falls back to js Date(), which is not reliable across all browsers and versions. Non ISO date formats are discouraged and will be removed in an upcoming major release. Please refer to http://momentjs.com/guides/#/warnings/js-date/ for more info.
Arguments: 
[0] _isAMomentObject: true, _isUTC: false, _useUTC: false, _l: undefined, _i: 2016-7-15, _f: undefined, _strict: undefined, _locale: [object Object]
Error
    at Function.createFromInputFallback (http://momentjs.com/static/js/global.js:309:98)
    at configFromString (http://momentjs.com/static/js/global.js:2048:32)
    at configFromInput (http://momentjs.com/static/js/global.js:2408:13)
    at prepareConfig (http://momentjs.com/static/js/global.js:2391:13)
    at createFromConfig (http://momentjs.com/static/js/global.js:2358:44)
    at createLocalOrUTC (http://momentjs.com/static/js/global.js:2445:16)
    at local__createLocal (http://momentjs.com/static/js/global.js:2449:16)
    at utils_hooks__hooks (http://momentjs.com/static/js/global.js:16:29)
    at <anonymous>:1:1
"2016-07-15T00:00:00+07:00"
```

`Don't`

```
moment(new Date("2016-07-15"))
```

`Do`

```
moment("2016-07-15")
```
