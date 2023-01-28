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
// function sequenceCounter(arr) {
//     arr.map((acc, val, ind, arr) => {
//         if(ind === 0){
//             acc.seqCounter = 1;
//             return acc;
//         }
//         if(val === arr[ind-1]){
//             acc.seqCounter++
//             return acc;
//         }else if(acc.seqCounter > 3){
//             acc.counter++;
//             acc.seqCounter = 0;
//             return acc;
//         }else{
//             acc.seqCounter = 0;
//             return acc
//         }
//     }, {counter: 0, seqCounter: 0})
// }
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
>        
>    }
>}
>```
```javascript


```
># Task 8
>დაწერეთ TO-DO List , input ველით  
```javascript


```