mplement atoi to convert a string to an integer.

**Hint:** Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

**Notes:** It is intended for this problem to be specified vaguely \(ie, no given input specs\). You are responsible to gather all the input requirements up front.

#### SOLUTION

```
/**
 * @param {string} str
 * @return {number}
 */
var myAtoi = function(str) {
  str = str.trim();

  var pattern = /^(\-|\+)?[0-9]+/;
  var tmp = pattern.exec(str);

  if (tmp) {
    var num = Number(tmp[0]);
    if (num < -2147483648)
      return -2147483648;
    if (num > 2147483647)
      return 2147483647;
    return num;
  }

  return 0;
};
```



