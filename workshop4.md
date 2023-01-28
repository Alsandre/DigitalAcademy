> **_Task 1_**
> 
> გვაქვს factory ობიექტი , რომელსაც აქვს რამდენიმე key-value წყვილი ,
> ასევე მეთოდი calculateWorkload - აბრუნებს მხოლოდ თანამშრომლის შესრულებული სამუშაოების მასივს (მაგალითის მიხედვით [40,25,28,30,31])
> და formatArray - რომელსაც გადაეცემა თანამშრომლის სახელი და აბრუნებს ობიექტს თანამშრომლის სახელი და ხელშეკრულების ამოწურვამდე
> დარჩენილი დროის მნშვნელობებით. ხელშეკრულების პერიოდი ყველა თანამშრომლისთვის არის 5 წელი.
> მაგალითად ('John' ის შემთხვევაში დაგვიბრუნდება {name : "John", timeLeft : 4}) timeleft = 5 - timespent;
> გვაქვს
> დალოგეთ calculateWorkload და formatArray შედეგები;
> !!!აუცილებლად გამოიყენეთ bind მეთოდი
> 
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

> **_Task 2_**
>
> 
> დაწერეთ ფუნქცია sumOfNumbers , რომელიც დააბრუნებს გადაცემული არგუმენტების ჯამს
> აღნიშნული ფუნქცია გაუშვით applyს საშუალებით, შესაბამისად არგუმენტებიც applyს მეშვეობით უნდა გადაცეთ.
>
> _hint : თუ კი ფუნქციაში არ გვაქვს this ქივორდის საჭიროება და შესაბამისად ობიექტი რომელსაც_
> _this მა უნდა მიუთითოს შეგიძლიათ apply call-ს პირველი არგუმენტად გადასცეთ null_
>
> 

```javascript
let sumOfNumbers = (...args) => args.reduce((acc, val) => acc+val, 0);
sumOfNumbers.apply(null, [3, 4]);
```

> **_Task 3_**
> 
> დაწერეთ რეკურსიული ფუნქცია checkIfEven(n) . აბრუნებს გადაცემული მნიშვნელობა
> არის თუ არა ლუწი . აუცილებლად გამოიყენეთ რეკურსია
>
> 

```javascript
let checkIfEven = a => {
    if(a < 3) {
        return a === 2;
    }
    return checkIfEven(a-2);
}

console.log(checkIfEven(30));
```

> **_Task 4_**
> //გვაქვს ორი მასივი
> // color = ["Blue ", "Green", "Red", "Orange", "Violet", "Indigo", "Yellow "];
> // o = ["th","st","nd","rd"]
> //დაწერეთ ფუნქცია რომელიც გადაცემული მასივის ელემენტების მიხედვით დააბრუნებს შემდეგ ტექსტს :
> // "1st choice is Blue ."
> // "2nd choice is Green."
> // "3rd choice is Red."
> // უნდა გამოვიყენოთ რიგითი რიცხვები წინადადების შესადგენად 1 - first - 1st , 2 - second - 2nd ...

```javascript
let colors = ["Blue ", "Green", "Red", "Orange", "Violet", "Indigo", "Yellow "];
let colorArr = new Array(122).fill().map(() => colors[Math.floor(Math.random()*colors.length)]);
function ordinalFunction (arr) {
    let newArr = arr.map((el, i) => {
        if(i+1 === 11) return `${i+1}th choice is ${el}`;
        else if((i+1) === 12) return `${i+1}nd choice is ${el}`;
        else if((i+1)%10 === 1) return `${i+1}st choice is ${el}`;
        else if((i+1)%10 === 2) return `${i+1}nd choice is ${el}`;
        else if((i+1)%10 ===3 ) return `${i+1}rd choice is ${el}`;
        else return `${i+1}th choice is ${el}`;
    });
    let result = '';
    for(let el of newArr){
        result += `${el}.\n`;
    }
    return result;
}
console.log(ordinalFunction(colorArr));
```

> **_//Task 5_**
> 
> დაწერეთ ფუნქცია რომელიც მასივიდან წაშლის falsy values მქონდე ელემენტებს 'null', '0', '""', 'false', 'undefined' and 'NaN' .
> arr = [NaN, 0, 15, false, -22, '',undefined, 47, null]
> ფუნქციამ უნდა დააბრუნოს [15,-22,57] 

```javascript
// // Utilizing Arry.prototype.filter()
// let falsyCheck = arr => arr.filter(el => el);

// Vanila js
function falsyCheck (arr) {
    let resultArray = [];
    for(let el of arr) {
        // '!' exclamation mark (aka "bang") logical 'not' operator turns 'true' to 'false' and vice versa
        // '!!' double exclamation mark is used in JS to turn value into boolean resulting in 'true' for truthy values and 'false' for falsy values
        if(!!el){
            resultArray.push(el);
        }
    }
    return resultArray;
};

```

> **_Task 6_**
> 
> დაწერეთ ფუნქცია რომელიც ორ მასივს აერთიანებს და დუბლირებულ მნიშვნელობებს შლის
> function mergeArr(arr1,arr2)
> arr1 = [1,2,3]
> arr2 = [2,1,30]
> დაბრუნებული მნიშვენლობა უნდა იყოს [1,2,3,30]

```javascript
// // Set version
// function mergeArr(arr1,arr2) {
//     let tempArr = arr1.concat(arr2);
//     //since javascript set is collection of unique values, it will automaticaly filter out merged array
//     let tempSet = new Set(tempArr);
//     return [...tempSet];
// }

// Vanilla js version (O_o)
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

> **_Task 7_**
> 
> გვავქს ორი ინდივიდუალური ელემენტების/სიგრძის მასივი , დაწერეთ ფუნქცია რომელიც დააბრუნებს ახალ მასივის
> რომლის თითოეული ელემენტი იქნება შესაბამის ინდექსებზე მდგომი ელემენტების ჯამი
> მაგ :
> [1,10,12,13] [4,5] -> [5,15,12,13]
> [1+4,10+5,12,13]
>
> 

```javascript
// // Utilizing Arry.prototype.map()
// let additionMerger = (arr1, arr2) => {
//     if(arr1.length >= arr2.length){
//         return arr1.map((el, i) => arr2[i] ? el+arr2[i] : el)
//     }
//     if(arr1.length < arr2.length){
//         return arr2.map((el, i) => arr1[i] ? el+arr1[i] : el)
//     }
// }

// Vanilla js version
let additionMerger = (arr1, arr2) => {
  let resultArray = [];
  let length = arr1.length >= arr2.length ? arr1.length : arr2.length;
  for (let i = 0; i < length; i++) {
    if (arr1[i] && arr2[i]) {
      resultArray.push(arr1[i] + arr2[i]);
    } else if (arr1[i]) {
      resultArray.push(arr1[i]);
    } else if (arr2[i]) {
      resultArray.push(arr2[i]);
    }
  }
  return resultArray;
};

console.log(additionMerger([1,10,12,13], [4,5]));
```
