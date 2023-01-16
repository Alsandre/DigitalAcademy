> **_//Task 1_**
> /_
> გვაქვს factory ობიექტი , რომელსაც აქვს რამდენიმე key-value წყვილი ,
> ასევე მეთოდი calculateWorkload - აბრუნებს მხოლოდ თანამშრომლის შესრულებული სამუშაოების მასივს (მაგალითის მიხედვით [40,25,28,30,31])
> და formatArray - რომელსაც გადაეცემა თანამშრომლის სახელი და აბრუნებს ობიექტს თანამშრომლის სახელი და ხელშეკრულების ამოწურვამდე
> დარჩენილი დროის მნშვნელობებით. ხელშეკრულების პერიოდი ყველა თანამშრომლისთვის არის 5 წელი.
> მაგალითად ('John' ის შემთხვევაში დაგვიბრუნდება {name : "John", timeLeft : 4}) timeleft = 5 - timespent;
> გვაქვს
> დალოგეთ calculateWorkload და formatArray შედეგები;
> !!!აუცილებლად გამოიყენეთ bind მეთოდი
> _/
> let factory = {
> facName : 'Volkswagen Wolfsburg Plant',
> calculateWorkload : function (){
> },
> formatArray : function (name) {
>
> }
>
> }
>
> let factoryEmployees = {
> employees : [{name : "John", timeSpent : 1 } , {name : "Sam", timeSpent : 3 },{name : "Maria", timeSpent : 2 },{name : "Dan", timeSpent : 4 },{name : "Lorelai", timeSpent : 5 }],
> employeeNum : this.employees.length,
> }
>
> let workloadData = {
> employeeWeeklyWorkload : [{name : "John", workload : 40 } , {name : "Sam", timeSpent : 25 },{name : "Maria", timeSpent : 28 },{name : "Dan", timeSpent : 30 },{name : "Lorelai", timeSpent : 31 }]
> }

```javascript
let factory = {
    facName: "Volkswagen Wolfsburg Plant",
    calculateWorkload: function () {
      return this.employeeWeeklyWorkload.map(el => el.workload);
    },
    formatArray: function (name) {
        return {name, timeLeft: 5-this.employees.filter(el => el.name === name)[0].timeSpent}
    },
  };
  let factoryEmployees = {
      employees : [{name : "John", timeSpent : 1 } , {name : "Sam", timeSpent : 3 },{name : "Maria", timeSpent : 2 },{name : "Dan", timeSpent : 4 },{name : "Lorelai", timeSpent : 5 }],
    //   employeeNum : this.employees.length,
  }
  
  let workloadData = {
      employeeWeeklyWorkload : [{name : "John", workload : 40 } , {name : "Sam", timeSpent : 25 },{name : "Maria", timeSpent : 28 },{name : "Dan", timeSpent : 30 },{name : "Lorelai", timeSpent : 31 }]
  }
  const workLoadCalculator = factory.calculateWorkload.bind(workloadData);
  const employeeLeftContractYears = factory.formatArray.bind(factoryEmployees);

  console.log(employeeLeftContractYears("John"))
  console.log(workLoadCalculator());
```

> **_//Task 2_**
>
> /\*
> დაწერეთ ფუნქცია sumOfNumbers , რომელიც დააბრუნებს გადაცემული არგუმენტების ჯამს
> აღნიშნული ფუნქცია გაუშვით applyს საშუალებით, შესაბამისად არგუმენტებიც applyს მეშვეობით უნდა გადაცეთ.
>
> hint : თუ კი ფუნქციაში არ გვაქვს this ქივორდის საჭიროება და შესაბამისად ობიექტი რომელსაც
> thisმა უნდა მიუთითოს შეგიძლიათ apply call-ს პირველი არგუმენტად გადასცეთ null
>
> \*/

```javascript
let sumOfNumbers = (a, b) => a+b;
sumOfNumbers.apply(null, [3, 4]);
```

> **_//Task 3_**
> /\*
> დაწერეთ რეკურსიული ფუნქცია checkIfEven(n) . აბრუნებს გადაცემული მნიშვნელობა
> არის თუ არა ლუწი . აუცილებლად გამოიყენეთ რეკურსია
>
> \*/

```javascript
let checkIfEven = a => {
    if(a < 3) {
        return a === 2;
    }
    return checkIfEven(a-2);
}

console.log(checkIfEven(30));
```

> **_//Task 4_**
> //გვაქვს ორი მასივი
> // color = ["Blue ", "Green", "Red", "Orange", "Violet", "Indigo", "Yellow "];
> // o = ["th","st","nd","rd"]
> //დაწერეთ ფუნქცია რომელიც გადაცემული მასივის ელემენტების მიხედვით დააბრუნებს შემდეგ ტექსტს :
> // "1st choice is Blue ."
> // "2nd choice is Green."
> // "3rd choice is Red."
> // უნდა გამოვიყენოთ რიგითი რიცხვები წინადადების შესადგენად 1 - first - 1st , 2 - second - 2nd ...

```javascript
let color = ["Blue ", "Green", "Red", "Orange", "Violet", "Indigo", "Yellow "];
let o = ["th","st","nd","rd"];
function ordinalFunction (arr) {
    let newArr = arr.map((el, i) => {
        if(i === 0) return `${i+1}${o[1]} choice is ${el}`;
        else if(i === 1) return `${i+1}${o[2]} choice is ${el}`;
        else if(i === 2) return `${i+1}${o[3]} choice is ${el}`;
        else return `${i+1}${o[0]} choice is ${el}`;
        
    });
    let result = '';
    for(let el of newArr){
        result += `${el}\n`;
    }
    return result;
}
console.log(ordinalFunction(color));
```

> **_//Task 5_**
> /\*_
> დაწერეთ ფუნქცია რომელიც მასივიდან წაშლის falsy values მქონდე ელემენტებს 'null', '0', '""', 'false', 'undefined' and 'NaN' .
> arr = [NaN, 0, 15, false, -22, '',undefined, 47, null]
> ფუნქციამ უნდა დააბრუნოს [15,-22,57] > _/

```javascript

let falsyCheck = arr => arr.filter(el => el);

```

> **_//Task 6_**
> /\*_
> დაწერეთ ფუნქცია რომელიც ორ მასივს აერთიანებს და დუბლირებულ მნიშვნელობებს შლის
> function mergeArr(arr1,arr2)
> arr1 = [1,2,3]
> arr2 = [2,1,30]
> დაბრუნებული მნიშვენლობა უნდა იყოს [1,2,3,30] > _/

```javascript
function mergeArr(arr1,arr2) {
    let resArr = arr1.length >= arr2.length ? [...arr1] : [...arr2];
    if(arr1.length >= arr2.length){
        for(let el of arr2){
            if(!arr1.includes(el)){
                resArr.push(el);
            }
        }
    }
    if(arr1.length < arr2.length){
        for(let el of arr1){
            if(!arr2.includes(el)){
                resArr.push(el);
            }
        }
    }

};
```

> **_//Task 7_**
> /\*\*
> გვავქს ორი ინდივიდუალური ელემენტების/სიგრძის მასივი , დაწერეთ ფუნქცია რომელიც დააბრუნებს ახალ მასივის
> რომლის თითოეული ელემენტი იქნება შესაბამის ინდექსებზე მდგომი ელემენტების ჯამი
> მაგ :
> [1,10,12,13] [4,5] -> [5,15,12,13]
> [1+4,10+5,12,13]
>
> \*/

```javascript
let additionMerger = (arr1, arr2) => {
    if(arr1.length >= arr2.length){
        return arr1.map((el, i) => arr2[i] ? el+arr2[i] : el)
    }
    if(arr1.length < arr2.length){
        return arr2.map((el, i) => arr1[i] ? el+arr1[i] : el)
    }
}
console.log(additionMerger([1,10,12,13], [4,5]));
```
