# juno-packages
- [std.juno](#stdjuno)
  - [cp](#cp)
  - [isdef](#isdef)
- [array.juno](#arrayjuno)
  - [array](#array)
  - [array_set_s](#array_set_s)
  - [array_set_i](#array_set_i)
  - [array_set_f](#array_set_f)
  - [array_push_s](#array_push_s)
  - [array_push_i](#array_push_i)
  - [array_push_f](#array_push_f)
  - [array_get](#array_get)
  - [array_len](#array_len)
  - [array_last](#array_last)

## std.juno
### desciption:
a package providing functionality needed in almost every script.
### dependencies
*none*
### functions
#### cp
a function used to copy a variable from one scope to another.

signature: `dec cp > name:s newScope:s newName:s`

paramterers:
- name
  - type: s (string)
  - the name of the variable that will be copied
- newScope
  - type: s (string)
  - the scope in which to save the copied variable
- newName
  - type: s (string)
  - the name of the variablen when copied

example:
```
scp sub
out &msg # msg

scp main
set a s "Hello World"
!cp a sub msg

scp sub
out &msg # Hello World
```

#### isdef
a function used to check if a given variable is defined. it "returns" `true` or `false` as a string depending on the existance of the variable.

signature: `dec isdef > var_name:s var_save:s`

parameters:
- var_name
  - type: s (string)
  - the name of the variable that will be checked
- var_save
  - type: s (string)
  - the name of the variable in the original scope that is used to store the result

example:
```
!isdef msg existsMsg
out &existsMsg # false

set msg s "Hello World"
!isdef msg existsMsg
out &existsMsg # true
```

## array.juno
### desciption:
a package providing support for simple arrays with elements of mixed type
### dependencies
- [std.juno](#stdjuno)
### functions
#### array
this function creates a new scope with the given name holding an empty array

signature: `dec array > name:s`

paramterers:
- name
  - type: s (string)
  - the name of the array that will be created

example:
```
!array testArray
```
#### array_set_s
add a string to the array with the given key

signature: `dec array_set_s > arr:s key:s value:s`

paramterers:
- arr
  - type: s (string)
  - the array to use
- key
  - type: s (string)
  - the key in the array
- value
  - type: s (string)
  - the value to insert

example:
```
!array testArray
!array_set_s testArray msg "Hello World"
```
#### array_set_i
add an integer to the array with the given key

signature: `dec array_set_i > arr:s key:s value:i`

paramterers:
- arr
  - type: s (string)
  - the array to use
- key
  - type: s (string)
  - the key in the array
- value
  - type: i (integer)
  - the value to insert

example:
```
!array testArray
!array_set_s testArray count 5
```
#### array_set_f
add a float to the array with the given key

signature: `dec array_set_f > arr:s key:s value:f`

paramterers:
- arr
  - type: s (string)
  - the array to use
- key
  - type: s (string)
  - the key in the array
- value
  - type: f (float)
  - the value to insert

example:
```
!array testArray
!array_set_s testArray pi 3.14159
```
#### array_push_s
add a string to the array at the last numerical index

signature: `dec array_push_s > arr:s value:s`

paramterers:
- arr
  - type: s (string)
  - the array to use
- value
  - type: s (string)
  - the value to insert

example:
```
!array userNames
!array_push_s userNames "John Doe"
```
#### array_push_i
add an integer to the array at the last numerical index

signature: `dec array_push_i > arr:s value:i`

paramterers:
- arr
  - type: s (string)
  - the array to use
- value
  - type: i (integer)
  - the value to insert

example:
```
!array userAges
!array_push_i userAges 42
```
#### array_push_f
add a float to the array at the last numerical index

signature: `dec array_push_f > arr:s value:f`

paramterers:
- arr
  - type: s (string)
  - the array to use
- value
  - type: f (float)
  - the value to insert

example:
```
!array userBalance
!array_push_s userBalance 12.09
```
#### array_get
get the value of the given array with the given key

signature: `dec array_get > arr:s key:s save_var:s`

paramterers:
- arr
  - type: s (string)
  - the array to use
- key
  - type: s (string)
  - the key from which to read the value
- save_var
  - type: s (string)
  - the name of the variable in the current scope used to save the result

example:
```
!array userNames
!array_push_s userNames "John Doe"
out &firstUser # firstUser
!array_get userNames 0 firstUser
out &firstUser # John Doe
```
#### array_len
used to get the length of an array

signature: `dec array_len > arr:s var_save:s`

paramterers:
- arr
  - type: s (string)
  - the array to use
- var_save
  - type: s (string)
  - the name of the variable in the current scope used to save the result

example:
```
!array userNames
!array_push_s userNames "John Doe"
out &userCount # userCount
!array_len userNames userCount
out &userCount # 1
```
#### array_last
get the last value of the given array with the given key

signature: `dec array_last > arr:s save_var:s`

paramterers:
- arr
  - type: s (string)
  - the array to use
- save_var
  - type: s (string)
  - the name of the variable in the current scope used to save the result

example:
```
!array userNames
!array_push_s userNames "John Doe"
!array_push_s userNames "Jane Doe"
out &lastUser # lastUser
!array_lst userNames lastUser
out &lastUser # Jane Doe
```





