# safe-trim
## install
```
npm install safe-trim
```
## use
```
import safeTrim from 'safe-trim'
safeTrim('    a      b  ')
```

## remove Invisible spaces

```
let str = '  "a":1    a \r\n\r\t  ᠎             　b       '
let ret = safeTrim(str)
expect(ret).toEqual('"a":1    a\n\nb')
```

## converted CR CR-LR into LR
```
a\r\n\r\nb  => 'a\n\nb'
a\r\rb => 'a\n\nb'
a\r\r\nb => 'a\n\nb'
```

## remove BOM
```
JSON.parse('﻿{"a":1}') // ❗️Error because BOM

JSON.parse(safeTrim('﻿{"a":1}')) // ✅
```