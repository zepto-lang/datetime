# datetime

A minimal datetime converter for zepto, more or less
based on Python datetime (but heavily inspired by it).

It is not done yet (i.e. time zones are probably implemented
wrongfully).

# Usage

The following endpoints are exposed:
```clojure
(define x 
  (datetime:make-datetime 2015 8 2 #{"hours" 15 "minutes" 58 "seconds" 12 "useconds" 12 "tmz" "GMT"}))
; the hash-map is optional (you can specify 0-all args in all combinations)
(datetime:to-ordinal x)
; returns the gregorian ordinal for the datetime object
(datetime:from-ordinal 120)
; returns a datetime object based on the ordinal
(datetime:weekday x)
; gets the datetimes weekday (0-indexed)
(datetime:weekday-string x)
; gets the weekday string
(datetime:month-string x)
; gets the month string
(datetime:to-unix-timestamp x)
; returns an unix timestamp based on the
(datetime:from-unix-timestamp 14378000)
; returns a datetime object based on the unix timestamp
(datetime:to-string x)
; returns a string akin to the bash date command, like so: Sun 2 Aug 2015 15:58:12.000012 GMT
```

Please not that information about timezone and usecs gets lost when doing somethin akin to:
```clojure
(datetime:from-unix-timestamp (datetime:to-unix-timestamp foo-date))
```

This is due to the nature of timestamps.

# Example

A silly, contrived example script:
```clojure
(load "zpbash.zp")
(load "datetime.zp")

(datetime:from-unix-timestamp (bash:unix-timestamp))
; this will probably be wrong if you are not okay with UTC/GMT.
; Where I live for example (Berlin CEST, +2 hours), this is
; almost exactly 2 hours behind.
```

<br/>

*Have fun!*
