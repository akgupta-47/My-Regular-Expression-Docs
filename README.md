# My-Regular-Expression-Docs
use this link to try them out\
https://regex101.com/ \
**Regular expressions help us to check a string of characters to look for possible matches**

they are always enclosed in these / /
`/ put expression here /`
it is case sensetive
-------------------------------------------------
Examples: \
string: basketball is a good sport and basketball-games are thrilling

exp: `/basketball/` 
"it searches the first occurance of basketball regardless of what is before or after it like 'rubbasketballtu' it will detect basketball in it too"

`/basketball/g` "this g flag at end considers all the occurances of basketball like there are 2 in above string"

`/basketball/i` "this i flag makes exp case insensetive that means it will also catch 'Basketball'"\
`/basketball/ig` "this makes it case insensetive and matches all (note //ig or //gi doesn't matter)"

-------------------------------------------------

**Define characterset**\
a character set will look for any character in the set for match\
`/[abc]asketball/ \`
"now it will detect asketball basketball and casketball" \
"but it only considers one at a time like [ab]asketball will only detect basketball not abasketball in a string"

`/[^abc]asketball/` "now this excludes every such word with a b or c at start"

-------------------------------------------------
**Define ranges**\
`/[a-z]asketball/` or `/[h-l]asketball/` "to define large ranges"\
`/[a-zA-Z]asketball/` "if i flag not used then we can use this too"\
`/[0-9]asketball/`

`/[0-9]+/` "UNLIMITED NUMBERS DETECTED"\
`/[0-9]{10}/` "detect a string of 10 numbers like for a phone number"\
`/[0-9]{10,15}/` "now it will detect number string either 10,11,12..15 long"\
`/[0-9]{10,}/` "this will match 10 chars to infinity chars"

-------------------------------------------------
**Meta characters**\
`\d` "digits [0-9]"\
`\w` "any word a-z A-Z 0-9 underscores"\
`\s` "white space"\
`\t` "tabs space "\
Examples:\
`/\d\s\w/` "it will match '1 f'"\
`/\d{3}\s\w{5}/` "matches '123 david' "

-------------------------------------------------
**Special characters**\
`+` "one or more quantifier"\
`\` "escape character"\
`[]` "define characterset"\
`[^]` "negate symbol of character set"\
`?` "0 or one quantifier(makes precedin char optional)"\
`.` "matches any char whatsoever (excluding newline char)"\
`*` "zero or more quantifier"

Examples:\
`/adios?/` "it will match 'adios' and 'adio' because ? makes presence of 's' optional"\
`/a[a-z]?/` "it matches 'a' or any 2 letter word with a at start 'ad' 'ar' "\
`/indi./` "matches by replaces the . with any charater number or symbol like 'india' 'indi@' 'indi4' "\
`/indi.?/` "matches all above and 'indi' too"\
`/.+/` "matches any string of any length (length>1)"\
`/a[a-z]*/` "matches any string with a at start 'a' or 'atergwerg' or 'ae' "\
`/abc\*\?\.\+/ "\` escapes and prints 'abc*?.+' "

-------------------------------------------------
**Tips and Tricks**\
Task 1: design a exp. to match a field in a form for a 5 letter string only (no more no less)\
step 1 : create a match for any 5 letter string = `/[a-z]{5}/`\
step 2 : now restrict it from having anything before = `/^[a-z]{5}/`\
	currently it matches first 5 letter of any string of length\
step 3 : now restrict its length to 5 by adding restriction at end too = `/^[a-z]{5}$/`\
	finally it will only and only string of length of strictly 5 letters not more not less
	
-------------------------------------------------
**OR operator**\
`/rajat|karan/` "it matches rajat or karan"\
`/(p|t)yre/` "use () when only one letter is common ,it matches tyre or pyre"\
Use () also to define range of two or more options\
`/(rajat|karan|badri) number/` "it matches 'rajat number', 'karan number' .... " but it wont have worked in case of\
`/rajat|karan number/` "it might have matcher 'rajat' or 'karan' but not 'rajat number' "\
`/(boy|girl)? married/` "this makes presence of boy or girl optional, it will also match ' married' "

-------------------------------------------------
**Other way to write REGeX**\
in javaScript we can also use\
`let regEx = new RegExp(/karan/, 'g', 'i');` \
new RegExp(expression, flags)

-------------------------------------------------
**RegExp for User Form**\
phone number: `/^\d{10}$/`\
user name: `/^[a-z\d]{5,12}$/`\
password: `/^[\w@-]{8,20}$/`\
email: `/^([a-z\d\.]+)@([a-z\d]+)\.([a-z]{2,6})(\.[a-z]{2,6})?/`
