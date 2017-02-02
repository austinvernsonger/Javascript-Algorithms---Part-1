There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays.

The overall run time complexity should be O\(log \(m+n\)\).

#### Example 1:

nums1 = \[1, 3\]

nums2 = \[2\]

The median is 2.0

#### Example 2:

nums1 = \[1, 2\]

nums2 = \[3, 4\]

The median is \(2 + 3\)/2 = 2.5

---

#### NOTES

##### 

##### O\(n\)

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */

var findMedianSortedArrays = function(nums1, nums2) {

  var s = merge(nums1, nums2);

  var len = s.length;


  if (len & 1) return s[~~(len / 2)];
  else return (s[len / 2 - 1] + s[len / 2]) / 2;
};

function merge(left, right) {
  var tmp = [];

  while (left.length && right.length) {
    if (left[0] < right[0])
      tmp.push(left.shift());
    else
      tmp.push(right.shift());
  }

  return tmp.concat(left, right);
}
```

##### O\(nlogn\)

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */

// the test data is weak, so..

var findMedianSortedArrays = function(nums1, nums2) {
  var s = nums1.concat(nums2);
  s.sort(function(a, b) {
    return a - b;
  });

  var len = s.length;
  if (len & 1) return s[~~(len / 2)];
  else return (s[len / 2 - 1] + s[len / 2]) / 2;
};
```



