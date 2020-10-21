# Limesharp Developer Test

Please, **don't fork this repo**, clone it or download it locally and then commit changes after each task into a new repo of your own, and send us the link. We will get back to you shortly. 

Languages accepted: Javascript or PHP. 

### Task 1: 
Make this work (repeat 3 times the contents of an array):
```javascript
repeat([1,2,3]) //[1,2,3,1,2,3,1,2,3]
```
Your solution:

```php
<?php

function repeat(array $data): array
{
    $limit = 3;
    
    $result = [];
    for($x=0; $x<$limit; $x++) {
        $result = array_merge($result, $data);
    }
    
    return $result;
}
```

###### If we type in our console your function and repeat([1,2,3]) then the result should be [1,2,3,1,2,3,1,2,3] 

### Task 2:
Make this work (no vowels, lowercase except the first letter):
```javascript
reformat("liMeSHArp DeveLoper TEST") //Lmshrp dvlpr tst
```
Your solution:

```php
<?php

function reformat(string $data): string
{
    // convert string to all lower case
    $lowerCasedString = strtolower($data);
    
    // remove all vowels from string
    $noVowelString = preg_replace('/[aeiou]/i', '', $lowerCasedString);
    
    // return string with lowercase except first letter
    return ucfirst($noVowelString);
}
```

###### If we type in our console your function and reformat("liMeSHArp DeveLoper TEST") then the result should be Lmshrp dvlpr tst


### Task 3 (optional, for bonus points):
Make this work (without using any built in functions, only a `for` loop, return the next binary number in a string or as an array)
```javascript
next_binary_number([1,0]) // [1,1]

// possible test cases:
// [1,0] => [1,1]
// [1,1] => [1,0,0]
// [1,1,0] => [1,1,1]
// .......
// [1,0,0,0,0,0,0,0,0,1] => [1,0,0,0,0,0,0,0,1,0]
```
Your solution:

```php
<?php

function next_binary_number(array $data): string
{
    $dataCount = count($data);
    $isUpdateDone = false;
    $result = '';
    
    for($x=($dataCount-1); $x>=0; --$x) {
        
        switch(true) {
            
            case (($data[$x] === 0) && !$isUpdateDone):
                $result = '1' . $result;
                $isUpdateDone = true;
            break;
            
            case (($data[$x] === 1) && ($x > 0) && !$isUpdateDone):
                $result = '0' . $result;
            break;
            
            case (($data[$x] === 1) && ($x === 0) && !$isUpdateDone):
                $result = '10' . $result;
            break;
            
            default:
                $result = $data[$x] . $result;
            break;
        }
    }
    
    return $result;
}
```

###### If we type in our console your function and next_binary_number([1,0,0,0,0,0,0,0,0,1]) then the result should look like 1,0,0,0,0,0,0,0,1,0 (or as an array).

---

If you get invited to the first interview read the "What to expect.md" file.