#### SOLUTION

```
/**
 * @param {number} x
 * @return {number}
 */

var reverse = function(x) { // The int32 range: -2^31 ~ 2^31-1
  var minn = - (1 << 30) * 2;
  var maxn = (1 << 30) * 2 - 1;
  var ans;
  var arr = x.toString().split('');
  if (x < 0) 
    arr.shift();  // remove '-'
  ans = Number(arr.reverse().join(''));
  if (x < 0)
    ans *= -1;
  console.log(minn, maxn)
  if (ans < minn || ans > maxn)
    return 0;
  else
    return ans;
};
```



