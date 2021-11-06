# Array

Array in solidity can be used to store multiple values of the same type.
Array can have a compile-time fixed size or a dynamic size.
We will write code to do different operations on array like adding, removing, getting length, getting value at index, getting whole array, etc.

## Initilaize an array

There are several ways to initialize an array.

Let's write first one.
Here we are just decalring an array named arr and not initializing it with values.

```
    uint[] public arr;
```

Let's write an array and initilize it with values.

```
    uint[] public arr2 = [1, 2, 3];
```

Now, we will write an array with fixed size.
In this case, it will be initilized with zeros by default.

```
    uint[10] public myFixedSizeArr;
```

## Getting an element from an array

Let's write a function to get an element from an array.
Here we are just indexing the array using the index passed through the parameter.

```
    function get(uint i) public view returns (uint) {
        return arr[i];
    }
```

## Append an element to an array

Now we will write a function to append an element to an array.
This will increase the array length by 1.

```
    function push(uint i) public {
        arr.push(i);
    }
```

We are using the `push` function to append an element to an array.
It appends the element at the end of the array.

## Pop an element from an array

Let's write a function to remove an element from an array.
This will decrease the array length by 1.

```
    function pop() public {
        arr.pop();
    }
```

We are using the `pop` function to remove an element from an array.
It removes the last element from the array.

## Remove an element from an array

Now we will write a function to remove an element from an array without changing the array length.

```
    function remove(uint index) public {
        delete arr[index];
    }
```

Here we are using the `delete` function to remove an element from an array.
It does not change the array length.
It resets the value at index to it's default value, in this case 0.

## Get the length of an array

Now we will write a function to get the length of an array.

```
    function getLength() public view returns (uint) {
        return arr.length;
    }
```

`arr.length` gives the length of the array.

## Retrieving the entire array

Solidity provides a way to retrieve the entire array.
But it is not recommended to use it for arrays that can grow indefinitely in length.

```
    function getArr() public view returns (uint[] memory) {
        return arr;
    }
```

## Removing an element without a gap in the array

Deleting an element from an array creates a gap in the array.
One trick to keep the array compact is to move the last element into the place to delete.

```
    function removeCompact(uint index) public {
        // Move the last element into the place to delete
        arr[index] = arr[arr.length - 1];
        // Remove the last element
        arr.pop();
    }
```
