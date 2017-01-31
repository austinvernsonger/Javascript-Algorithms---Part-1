The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: \(you may want to display this pattern in a fixed font for better legibility\)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `PAHNAPLSIIGYIR`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string text, int nRows);
```

`convert("PAYPALISHIRING", 3)` should return `"PAHNAPLSIIGYIR"`.





#### SOLUTION

```
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var ans, max_column;

function dfs(x, y, s, n, numRows) {
  ans[x][y] = s[n];

  if (s.length === n) {
    max_column = y;
    return;
  }

  if (y % (numRows - 1) === 0 && x !== numRows - 1) 
    dfs(x + 1, y, s, n + 1, numRows);
  else 
    dfs(x - 1, y + 1, s, n + 1, numRows);
}

var convert = function(s, numRows) {
  if (numRows === 1) 
    return s;

  ans = [];

  for (var i = 0; i < numRows; i++)
    ans[i] = [];

  dfs(0, 0, s, 0, numRows);

  var tmp = '';
  for (var i = 0; i < numRows; i++)
    for (var j = 0; j <= max_column; j++)
      if (ans[i][j] !== undefined)
        tmp += ans[i][j];

  return tmp;
};
```



