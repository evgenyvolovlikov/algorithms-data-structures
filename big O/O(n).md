### Big(O) cheatsheet -> https://www.bigocheatsheet.com/

## O(1)
```
const boxes = [0, 1, 2, 3, 4, 5]
function logFirstTwoBoxes(boxes) {
  console.log(boxes[0]) - O(1)
  console.log(boxes[0]) - O(1)
}

logFirstTwoBoxes(boxes) - O(2)
```
## O(n)
```
ES5
const boxes = [0, 1, 2, 3, 4, 5]
function compressAllBoxes(){
  boxes.forEach(item => {
    console.log(item)
  })
}

ES6 
const compressAllBoxes = boxes => {
  boxes.forEach(item => console.log(item))
} 

compressAllBoxes(boxes) -> O(n)
```
## O(n)
```
const fish = ['dory', 'bruce', 'marlin', 'nemo'];
const nemo = ['nemo'];
const everyone = ['dory', 'bruce', 'marlin', 'nemo', 'gill', 'bloat', 'nigel', 'squirt', 'darla', 'hank'];
const large = new Array(100).fill('nemo')

const findNemo = (arr) => {
  const t1 = performance.now()
  for(let i = 0; i < arr.length; i++){
    if(arr[i] == 'nemo') {
      console.log('Nemo Found!')
    }
  }
  const t2 = performance.now()

  console.log(`Call to find Nemo took: ${t2 - t1}`)
}

findNemo(nemo) -> O(n)
```
## O(n) 
```
function funChallenge(input) {
  let a = 10; -> O(1)
  a = 50 + 3; -> O(1)

  for (let i = 0; i < input.length; i++) {
    anotherFunction(); -> O(n)
    let stranger = true; -> O(n)
    a++; -> O(n)
  }
  return a; -> O(1)
}

funChallenge([1, 2, 3, 4, 5]) -> O(3 + 4n) -> O(n)
```
## O(n)
```
function anotherFunChallenge(input) {
  let a = 5; -> O(1)
  let b = 10; -> O(1)
  let c = 50; -> O(1)
  for (let i = 0; i < input; i++) {
    let x = i + 1; -> O(n)
    let y = i + 2; -> O(n)
    let z = i + 3; -> O(n)

  }
  for (let j = 0; j < input; j++) {
    let p = j * 2; -> O(n)
    let q = j * 2; -> O(n)
  }
  let whoAmI = "I don't know"; -> O(1)
}

anotherFunChallenge([1, 2, 3]) -> O(4 + 5n) -> O(n)
```
```
function printFirstItemThenFirstHalfThenSayHi100Times(items) {
  console.log(items[0]); -> O(1)
  let middleIndex = Math.floor(items.length / 2); -> ?
  let index = 0; O(1)
    
  while (index < middleIndex) {
    console.log(items[index]); -> O(n)
    index++; -> O(n)
  }

  for (var i = 0; i < 100; i++) {
    console.log('hi'); -> O(n)
  }
}

printFirstItemThenFirstHalfThenSayHi100Times() -> O(n)
```
## O(n)
```
const boxes = [0, 1, 2, 3, 4, 5]

function compressBoxesTwice(boxes){
  boxes.forEach(item => {
    console.log(item) -> O(n)
  })
    boxes.forEach(item => {
    console.log(item) -> O(n)
  })
}
compressBoxesTwice(boxes) -> O(2n) -> Drop the constants -> O(n)

function compressBoxesTwice(boxes, boxes2){
  boxes.forEach(item => {
    console.log(item) -> O(n)
  })
    boxes2.forEach(item => {
    console.log(item) -> O(n)
  })
}
compressBoxesTwice(boxes) -> O(n^2) -> Drop the constants -> O(n) ?
```
## O(n^2)
```
const boxes = ['a', 'b', 'c', 'd', 'e'];
function logAllPairsOfArray(array) {
  for (let i = 0; i < array.length; i++) {
    for (let j = 0; j < array.length; j++) {
      console.log(array[i], array[j])
    }
  }
}

logAllPairsOfArray(boxes) -> O(n * n) -> O(n^2) (Quadratic Time)
```
## O(n^2)
```
function printAllNumbersThenAllPairSums(numbers) {

  console.log('these are the numbers:');
  numbers.forEach(function(number) {
    console.log(number);
  });

  console.log('and these are their sums:');
  numbers.forEach(function(firstNumber) {
    numbers.forEach(function(secondNumber) {
      console.log(firstNumber + secondNumber);
    });
  });
}

printAllNumbersThenAllPairSums([1,2,3,4,5]) -> O(n^2)
```

## O(1)
```
function boooo(n) {
  for (let i = 0; i < n; i++) {
    console.log('booooo');
  }
}
```
## O(n)
```
function arrayOfHiNTimes(n) {
  let hiArray = [];
  for (let i = 0; i < n; i++) {
    hiArray[i] = 'hi';
  }
  return hiArray;
}

arrayOfHiNTimes(6) -> O(n)
```