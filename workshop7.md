> # Task 1
>დაწერეთ ფუნქცია რომელიც შეამოწმებს გადაცემული ტექსტი არის თუ არა პალინდრომი . 
>პალინდრომი არის სიტყვა რომელიც შებრუნებულ მდგომარეობაშიც იგივეა . მაგ. madam - მარცხნიდანაც და მარჯვნიდანაც ერთი და იგივეა(შებრუნებულიც და ჩვეულებრივადაც) .
>!!!!დაწერეთ ამ ამოცანის მინიმუმ სამი სხვადასხვა ამოხსნის გზა 
```javascript
// let palindrom = str => str === str.split('').reverse().join(''); 

// let palindrom = str => str.split('').reduce((acc, val, ind, arr) =>  val !== arr[arr.length-1-ind] ? false : acc,true)

// function palindrom(str) {
//     let tempArr = [];
//     for(let i=str.length-1; i > -1; i--){
//         tempArr.push(str[i]);
//     };
//     let str2 = tempArr.join('');
//     return str2 === str;
// }

function palindrom(str) {
    let tempArr = [];
    for(let i=0; i < str.length; i++){
        tempArr.unshift(str[i]);
    };
    let str2 = tempArr.join('');
    return str2 === str;
}
```
---
># Task 2
>დაწერეთ ფუნქცია რომელიც დაგვიბრუნებს პირველ არაგამეორებადი ქარაქტერი/სიმბოლოს. 
>მაგალითად გვაქვს string 'bcskbrk' -> c - პირველი არაგამეორებადი ქარაქტერი არის 'c'  
>'cbcbdde' -> 'e'  
>'worsdorw' -> 's'   
>'worsdorws'-> 'd'
```javascript
function firstUnique (str) {
    let tempArr = [...str];
    let result = 'No uniquie member';
    for(let i=0; i<tempArr.length; i++){
        if(tempArr.slice(i+1, tempArr.length).indexOf(tempArr[i]) === -1){
            result=tempArr[i];
            break;
        }
    }
    return result;
}
```
># Task 3 : 
>დაწერეთ ფუნქცია რომელიც გადაცემულ ტექსტის camelCase ში კონვერტაციას გააკეთებს
>camelize("sad midis Matarebeli") -> "sadMidisMatarebeli"
```javascript
// let camelize = str => str.replace(/(\s\w)/g, (searchResult) => searchResult.trim().toUpperCase())

function camelize(str) {
  let tempArr = str.split(" ");
  let resArr = [];
  for (let i = 0; i < tempArr.length; i++) {
    if ((i === 0)) {
      resArr.push(tempArr[i]);
    } else {
      let tempArr2 = tempArr[i].split("");
      tempArr2[0] = tempArr2[0].toUpperCase();
      resArr.push(tempArr2.join(''));
    }
  }
  return resArr.join('');
}
```
---
># Task 4
>დაწერეთ ფუნქცია რომელსაც გადაეცემა მასივი და ეს ფუნქცია დაგვიბრუნებს
>ამ მასივში ყველაზე ხშირად გამოერებად ელემენტს და გამეორების რაოდენობას
>მაგალითად  
>arr1=[3, 'a', 'a', 'a', 2, 3, 'a', 3, 'a', 2, 4, 9, 3];  
>პროგრამამ უნდა დაგვიბრუნოს 'a - 5'  
>უმჯობესია გამოიყენოთ reduce მეთოდი
```javascript
function occurrenceCounter(arr){
    let res = arr.reduce((acc, el) => {
        if(acc.hasOwnProperty(el)){
            acc[el]++
            return acc;
        }else{
            acc[el] = 1;
            return acc;
        }
    }, {});
    let result = {celeb: '', rating: 0}
    for(let key in res){
        if(res[key] > result.rating){
            result.celeb = key;
            result.rating = res[key];
        }
    }
    return `${result.celeb} - ${result.rating}`;
}
```
># Task 5 : 
>ფუნქციამ უნდა დააბრუნოს მასივი ისე როგორც კომენტარშია ნაჩვენები . 
>გამოიყენეთ map
>``` javascript
> function readyToPutInTheDOM(arr) {
> }
> console.log(
>   readyToPutInTheDOM([
>     {
>       name: "Angelina Jolie",
>       age: 80,
>     },
>     {
>       name: "Eric Jones",
>       age: 2,
>     },
>     {
>       name: "Paris Hilton",
>       age: 5,
>     },
>     {
>       name: "Kayne West",
>       age: 16,
>     },
>     {
>       name: "Bob Ziroll",
>       age: 100,
>     },
>   ])
> );
>
> ["<h1>Angelina Jolie</h1><h2>80</h2>",
> "<h1>Eric Jones</h1><h2>2</h2>",
> "<h1>Paris Hilton</h1><h2>5</h2>",
> "<h1>Kayne West</h1><h2>16</h2>",
> "<h1>Bob Ziroll</h1><h2>100</h2>"]
>```
```javascript
function readyToPutInTheDOM(arr) {
    return arr.map(el => `<h1>${el.name}</h1><h2${el.age}</h2>`);
}
```
># Task 6
>დაწერეთ ფუნქცია რომელიც დაითვლის ნულების მიმდევრობის რაოდენობას .  მიმდევრობა ვალიდურია თუ კი არის არანაკლებ 4 სიგრძისა 
>
>[0, 0, 0, 0, 0, 1]  -->  1
>##### ერთი ჯგუფი 0 ლების მიმდევრობის რომელიც 4ზე მეტია
>
>[0, 0, 0, 0, 1, 0, 0, 0, 0]  -->  2
>##### ორი სხვადასხვა 4 სიგრძის მიმდევრობა
>
>[0, 0, 0, 1, 0]  -->  0 
>##### ერთი მიმდევრობა არის 3 სიგრძის მეორე 1 სიგრძის ანუ არც ერთი არ არის ვალიდური და ფუნქციამ უნდა დაგვიბრუნოს 0 
>
>[0, 0, 0, 1, 0, 0]  -->  0
>##### იგივე
>
>[1, 2, 3, 4, 5]  -->  0
>##### საერთოდ არ გვაქვს მიმდევრობა
>
>[]  -->  0
>##### ცარიელია
```javascript
// General solution for sequences

// function sequenceCounter(arr) {
//     let resObj =  arr.reduce((acc, val, ind, arr) => {
//         if(val === arr[ind-1]){
//             acc.seqCounter++;
//             return acc;
//         }else if(acc.seqCounter > 3){
//             acc.counter++;
//             acc.seqCounter = 1;
//             return acc;
//         }else{
//             acc.seqCounter = 1;
//             return acc
//         }
//     }, {counter: 0, seqCounter: 1});
//     return resObj.seqCounter > 3 ?  ++resObj.counter : resObj.counter;
// }

// For sequences of zero
function sequenceCounter(arr) {
    let counter =  0;
    let result = 0
    for(let element of arr){
        if(element === 0){
            counter++;
        }else{
            if(counter > 3){
                result++;
            }
            counter = 0;
        }
    }
    return counter > 3 ? ++result : result;
}
```
---

># Task 7
>დაწერეთ ფუნქცია ციფრების ჯამი , sumOfDigits(n) რომელიც იღებს ერთ პარამეტრს 
>და აბრუნებს გადაცემული მნიშვნელობის შემადგენელი ციფრების ჯამს .   
>sumOfDigits(1312) = 1+3+1+2 = 7;
>
>აღნიშნული დავალება შეასრულეთ ორნაირად , როგორც ჩვეულებრივი ასევე რეკურსიული
>ფუნქციის გამოყენებით . 
>
>```javascript
>hint : 15670 
>1567 % 10 -> 7
>156 % 10 -> 6
>15 % 10 -> 5
>
>n < 10 -> n 
>function sumOfDigits (n) {
>    if(n < 10) {
>        return n
>    } else {
>        sumOfDigits (n - n%10)
>    }
>}
>```
```javascript
// let sumOfDigits = (n) => n < 10 ? n : n%10 + sumOfDigits(Math.floor(n/10));

// function sumOfDigits(n) {
//   if (n < 10) {
//     return n;
//   } else {
//     return (
//       (n - (n % 10 ** (n.toString().length - 1))) /
//         10 ** (n.toString().length - 1) +
//       sumOfDigits(n % 10 ** (n.toString().length - 1))
//     );
//   }
// }

function sumOfDigits(n) {
    let resArr = [];
    while(n>0){
        resArr.push(n%10);
        n=Math.floor(n/10);
    }
    return resArr.reduce((acc, el) => acc+el, 0)
}
```
># Task 8
>დაწერეთ TO-DO List , input ველით  
```javascript
let container = document.createElement('div');
container.style.width = '300px';
// container.style.height = '50px';
container.style.backgroundColor = '#ccc';
container.style.margin = 'auto';
container.style.padding = '1rem 2rem';
container.style.display = 'flex';
container.style.justifyContent = 'center';
container.style.alignItems = 'center';
container.style.borderRadius = "25px";

let toDoInput = document.createElement('div');
toDoInput.style.width = '90%';
// toDoInput.style.height = '1.5rem';
toDoInput.style.padding = '0.2rem';
toDoInput.style.borderRadius = '12px';
toDoInput.style.backgroundColor = "#ddd";
toDoInput.style.display = "flex";
toDoInput.style.flexDirection = "column";
toDoInput.style.justifyContent = "center";
toDoInput.style.alignItems = "center";



let label = document.createElement('lebel');
label.setAttribute('for', 'input');
label.setAttribute('value', 'Type your task here');
label.style.fontWeight = 'bold';
let labelText = document.createTextNode('Type your task here:');
label.appendChild(labelText);

let input = document.createElement('input');
input.setAttribute('id', 'input');
input.setAttribute('placeHolder', 'Taks...');
input.style.width = '90%';
input.style.padding = '0.2rem 0';

let addButton = document.createElement('button');
addButton.style.width = '90%';
addButton.style.padding = '0.1rem 1rem';
addButton.textContent = 'ADD TASK';

toDoInput.appendChild(label);
toDoInput.appendChild(input);
toDoInput.appendChild(addButton);
container.appendChild(toDoInput);

addButton.addEventListener('click', () => {
  let input = document.getElementById('input');
  let inputValue = input.value;
  let newTask = updateList(inputValue);
  window.document.body.appendChild(newTask);
})
window.document.body.appendChild(container);

function updateList (input) {
  let newEntryContainer = document.createElement('div');
  newEntryContainer.style.backgroundColor = '#ccc';
  newEntryContainer.style.width = '300px';
  newEntryContainer.style.margin = 'auto';
  newEntryContainer.style.marginTop = '1.5rem';
  newEntryContainer.style.padding = '1rem 2rem';
  newEntryContainer.style.display = 'flex';
  newEntryContainer.style.justifyContent = 'center';
  newEntryContainer.style.alignItems = 'center';
  newEntryContainer.style.borderRadius = "25px";
  
  let newEntry = document.createElement('p');
  newEntry.textContent = input;
  newEntryContainer.appendChild(newEntry)
  
  newEntryContainer.addEventListener('click', () => newEntryContainer.style.display = 'none')
  
  return newEntryContainer;
}
```