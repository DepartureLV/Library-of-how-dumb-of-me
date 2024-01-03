# Library-of-how-dumb-of-me
A eureka code collections from Codewar after I struggled to solve the problem for a long but some guy just used an alternative and clever method to solve it in one second.


## Javascript
This section is a collection of clever and artistic javascript

## Sort and join unique values
### How dumb of me
```javascript
function longest(s1, s2) {
  let result = [];

  const first = s1.split('');
  const second = s2.split('');

  if (first.length > 0) {
    result.push(first[0]);
  } else if (second.length > 0) {
    result.push(second[0]);
  } else {
    return;
  }

  for (let i = 0; i < first.length; i++) {
    if (!result.includes(first[i])) {
      result.push(first[i]);
    }
  }

  for (let i = 0; i < second.length; i++) {
    if (!result.includes(second[i])) {
      result.push(second[i]);
    }
  }

  result = result.sort().join('');
  console.log(result);

  return result;
}
```
### How some guy solve it
```javascript
const longest = (s1, s2) => [...new Set(s1+s2)].sort().join('')
```
### What I learnt
[Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) is are collections of values. A value in the set may only occur once. **This replaces most of my code instantly, Leftover is just sort().join().**
___
## Sort and join unique values
Source > [Codewar Challenge](https://www.codewars.com/kata/56a5d994ac971f1ac500003e)
### How dumb of me
```javascript
function longestConsec(strarr, k) {
  // check validation
  if (strarr.length == 0 || k > strarr.length || k <= 0) {
    return '';
  }

  let result = [];

  // slice and join by number of k elements
  for (let i = 0; i < strarr.length - k + 1; i++) {
    result.push(strarr.slice(i, i + k).join(''));
  }

  // find longest (probably return final longest if have many matches)
  let longest = result.reduce(function (a, b) {
    return a.length > b.length ? a : b;
  });

  // find first longest
  for (let i = 0; i < result.length; i++) {
    if (result[i].length === longest.length) {
      return result[i];
    }
  }
}
```
### How some guy solve it
I found this solution, but the problem with this solution is the same as mine. The problem with runtime = n * 2k time is still exist.
```javascript
function longestConsec(strarr, k) {
  let longest = "";
  for(var i=0;k>0 && i<=strarr.length-k;i++){
    var tempArray = strarr.slice(i,i+k);
    var tempStr = tempArray.join("");
    if(tempStr.length > longest.length){
      longest = tempStr;
    }
  }
  return longest;
}
```
if you have a better version. please tell me :)

### What I learnt
**slice()**
> The slice() method of Array instances returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.
```
slice()
slice(start)
slice(start, end)
```
**end**
> Zero-based index at which to end extraction, converted to an integer. slice() extracts up to but **not including end.**
```javascript
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2, 4));
// Expected output: Array ["camel", "duck"] (camel is at index 2, start slice here (include camel), duck is not in index 4 => result = index 2,3 only (exclude elephant))
```
