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

## String: 
- Strings can’t be changed (Immutable) in JavaScript. It is impossible to change a character
- Functions
```
string str = "rushikesh"

1. Character Finding in string
char ch = str.charAt(idx); //This will return the character at the given index
OR
char ch = str[idx];
OR
char ch = str.charCodeAt(idx); // will return the index characters ASCII value

2. Searching of substr in string
str.include(Key); //Return true if key is present in str else false
str.includes(substr, pos)

str.indexOf(key); //Return the index of the first occurence of the key in str
str.indexOf(substr, position); // str.indexOf('a', 3) will return index of 3rd occurence of the key a.

str.lastIndexOf(key); //Return the index of the last occurence of the key in str
str.lastIndexOf(substr, position);

str.search(key); //Return the index of key in str, else -1

str.startsWith("key"); // Will return true if str starts with key else false
str.endsWith("key");

3. Changing Case of str
str.toUpperCase(); //UPPERCASE 
str.toLowerCase(); //LOWERCASE

4. Getting a substring
const subStr = str.substring(fromIdx, toIdx); // Return the sub string, it only accepts positive idxs
const subStr = str.slice(fromIdx, toIdx); // Return the sub string, it accepts positive + negative idxs

5. Comparing the strings
str.localCompare(str2); //Return 0 if same else -1

6. Replacing the substr in string
str.replace(toReplace, withToReplace); //It replaces the toReplace word with withToReplace.(only one)
str.replaceAll(key, withToReplace); //This will replace all places

7. Seperating the String
const arr = str.split('.'); //Return the array with . separated values of str.

8. Joining the sub strings
const str = arr.join(' '); //Return the string with joining the each element of arr with space.

9. Trimming the string
str.trim(); //Will trim all white spaces from front and back of str.
str.trimStart();
str.trimEnd();

10. Converting to String
const num = 123 // Integer
num.toSting(); //num becames string '123'
const obj = {
  age: '11',
  name: "RUshi"
}
JSON.Stringify(obj); //Convert object to string

11. Concatinition
str.concate(str2);
OR
const ans = str + str1;
OR
const ans = `${str} ${str1} huehue`;
```

## Searching Algorithms

### Linear Search
```
for(let i = 0; i<arr.length; i++){
  if(arr[i] === target){
    return i;
  } else {
    return -1;
  }
}

T.C: O(n) S.C: O(1)
```

### Binary Search 
```
1. Iterative:
const l = 0, r = arr.length-1;
while(l<=r){
  let mid = Math.floor((l+r)/2);
  if(arr[mid] === key) return mid;
  if(arr[mid] < key){
    l = mid +1;
  } else {
    r = mid -1;
  }
}
T.C: O(log(n)) S.C: O(1)

2.Reccursive:
var search = function(nums, target) {
    return BS(nums, 0, nums.length, target);
};

function BS(arr, start, end, key){
    if(start>end) return -1;

    let mid = Math.floor((start + end)/2);

    if(arr[mid] === key) return mid;

    if(arr[mid]<key){
        return BS(arr, mid+1, end, key);
    } else {
        return BS(arr, start,mid-1, key);
    }
}
T.C: O(log(n)) S.C: O(n) 
```

##Objects in JS:

- Objects are collections of key-value pairs where the keys are strings (or symbols) and the values can be of any data type (such as numbers, strings, arrays, functions, or even other objects).
-Functions:
```
const person = {
    name: "Alice",
    age: 30,
    greet: function() {
        console.log("Hello, my name is " + this.name);
    }
};

person.name; //This will return value of key name;

1. Finding Key in Object;
person.hasOwnProperty("name"); //Return true if exist else false

2. Add, Delete and Update the key
person.name = "Rushikesh"; //Updating the key's value.And if name key is not present it will create new key called name and set its value.

delete person.name; //This will delete the key.

3. Copying
a. Shallow Copy:
const person2 = person;

b. Deep Copy:
const person2 = Object.assign({}, person);
//it will copy every thing of person into {} and then {} will be assigned to person2

4. freeze vs seal method in Objects
Object.freeze(person); //Prevents adding, deleting, and modifying properties. Makes the object immutable.
Object.seal(person); //Prevents adding and deleting properties, but allows modification of existing properties’ values.

Object.isSealed(person); //checks
Object.isFrozen(person);

5. Keys, Values and Entries methods

Object.keys(person); //Return all keys of person object
Object.values(person); //Return all values of person's keys
Object.entries(person); //Return array of array with key & value pair in each subarray.

6. Looping in Object

for(let key in person){
  ---
  ---
}
```
