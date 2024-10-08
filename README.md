# JavaScript Fast + Thorough Revise

## Array: 
- Array in Js is different than the rest of languages. Array in JS can contain items of different datatypes.
- Declaration: 
```
const arr = [];
const arr2 = new Array();
```
- Traversal:
```
1. 
arr.forEach(elem, idx){
}

2.
for(let i = 0; i< arr.length; i++){
  ---
  ---
}

3.
 for(let x of arr){
  ---
  ---
]
```
- Sorting
```
// Ascending:
arr.sort() //O(nlogn)

// Decending:
arr.sort((a, b) => b-a) // if b-a is +ve swap else noSwap
```

- Misc.

```
// Addition:
// At End: O(1)
arr.push(x) //This will add the element at the last of array
// At Front: O(n)
arr.unshift(x) //This will add the elemet at start of array
// Specific items 
arr.splice(startIdx, 0, elmesTobeAdded, ..., );


// Deletion:
// At End:O(1)
const lastElem = arr.pop() // This will delete and return the last item of array
// At Front:O(n)
const firstElem = arr.shift() // This will delete and return the first item of array
// Specific items 
arr.splice(startIdx, numOfElmesToDelete);

// Slicing the array
const subArray = arr.slice(startIdx, EndIdx); // [start, end)


// Copy
// Shallow Copy
const copyArray = arr; //Both are pointing to same array

// Deep Copy
const copyArray = [...arr] //Will create separate array called copyArray
OR
const copyArray = Array.from(arr);
OR
const copyArray = arr.concat();

// Merge multiple Arrays
const MergeArray = [...arr1, ...arr2]
OR
const copyArray = arr1.concat(arr2);

// Comparing two array
if(arr1.length === arr2.length && arr1.every((ele, i) => arr1[i] === arr2[i])){
  return true;
}else{
  return false;
}

// Reversing Array 
arr.reverse();

// Flattening the nested array
const flatArray = arr.flat(depth);

```
- Important(Map, filter and reduce)
```
// Map : Take callback function and run it on every element of array
const newArr = arr.map((elem, idx) => elem*elem); //Square every elem of array

// Filter : Take callback function as condition in it and run it for every elem of array and when condition fullfills then elemet get added in newArr
const newArr = arr.filter((elem, idx) => elem > 0); //will give every positive elem of array

// Find : As filter will add all values satisfying condition it will return all values. Find will return first value which satisfyies the condition
const elem = arr.find((elem, idx) => elem > 0);

// Reduce : The reduce method applies a function (callback) against an accumulator and each element in the array to reduce it to a single value. It’s particularly useful when you need to derive a single result (like a sum, product, or average) from an array.

const result = arr.reduce((accumulator, currentElem, idx, array) => {
    // logic using accumulator and currentElem
    return newAccumulatorValue;
}, initialValue);

  e.g. const arr = [1, 2, 3, 4, 5];
      // Sum all elements in the array
      const sum = arr.reduce((accumulator, currentElem) => accumulator + currentElem, 0);
      console.log(sum); // Output: 15
```
