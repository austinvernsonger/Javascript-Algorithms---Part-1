Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**

Could negative integers be palindromes? \(ie, -1\)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?



#### SOLUTION

```
/**
 * @param {number} x
 * @return {boolean}
 */
 
var isPalindrome = function(x) {
    return x.toString() == x.toString().split('').reverse().join('');
};
```



