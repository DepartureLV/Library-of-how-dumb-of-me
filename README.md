# Library-of-how-dumb-of-me
A eureka code collections from Codewar after I struggled to solve the problem for a long but some guy just used an alternative and clever method to solve it in one second.

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
