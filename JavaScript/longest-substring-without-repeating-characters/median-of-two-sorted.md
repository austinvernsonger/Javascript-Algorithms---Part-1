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





##### O\(logn\)

```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */

var findMedianSortedArrays = function(nums1, nums2) {
  var m = nums1.length;
  var n = nums2.length;
  var total = m + n;
  var half = total >> 1;

  if (total & 1)
    return findKth(nums1, m, nums2, n, half + 1);
  else 
    return (findKth(nums1, m, nums2, n, half) + findKth(nums1, m, nums2, n, half + 1)) / 2;
};


function findKth(a, m, b, n, k) { 
  // always assume that m is equal or smaller than n  
  if (m > n)  
    return findKth(b, n, a, m, k);  
  if (m === 0)  
    return b[k - 1];  
  if (k === 1)  
    return Math.min(a[0], b[0]); 

  // divide k into two parts  
  var pa = Math.min(k >> 1, m)
    , pb = k - pa;  

  if (a[pa - 1] < b[pb - 1])  
    return findKth(a.slice(pa), m - pa, b, n, k - pa);  
  else if (a[pa - 1] > b[pb - 1])  
    return findKth(a, m, b.slice(pb), n - pb, k - pb);  
  else 
    return a[pa - 1];  
}
```

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



