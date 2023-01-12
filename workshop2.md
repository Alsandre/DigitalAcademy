> **_// Task 1 :_**
> // შექმენით ფუნქცია რომელსაც აქვს ერთი პარამეტრი .
> // ფუნქციას გადაეცით ობიექტი არგუმეტნად
>
> // let sampleObject = {
> // isItarable : false,
> // sampleArray : [12,63,21,34,98,57]
> // }
> // თუ მიღებული არგუმენტის isItarable მნიშვნელობა არის ჭეშმარიტი მაშინ დალოგეთ თითოეული ელემენტი
> // თუ არ არის ჭეშმარიტი გამოიტანეთ წინადადება "provided array isn't itarable"

```javascript
function iterator(val) {
  if (val.isIterable) {
    for (let item of val.sampleArray) {
      console.log(item);
    }
  } else if (!val.isIterable) {
    console.log("provided array isn't itarable");
  }
}
```

> **_// Task 2_**
> /_
> შექმენით ფუნქცია checkPythagoras რომელიც მიიღებს სამ პარამეტრს x,y,z .
> ფუნქციამ უნდა შეამოწმოს თუ აღნიშნული რიცხვების რომელიმე კომბინაცია მაინც
> აკმაყოფილებს პითაგორას თეორემის პირობას a^2 + b^2 = c^2;
> თუ კი ეს პირობა დაკმაყოფილდა ფუნქციამ უნდა დააბრუნოს true
> წინააღმდეგ შემთხვევაში false
> _/

```javascript
function checkPythagoras(a, b, c) {

  // let abPowered = a ** 2 + b ** 2;
  // let acPowered = a ** 2 + c ** 2;
  // let bcPowered = b ** 2 + c ** 2;

  // SWITCH version

  // switch(true) {
  //   case abPowered === c**2:
  //     return true;
  //   case acPowered === b**2:
  //     return true;
  //   case bcPowered === a**2:
  //     return true;
  //   default:
  //     return false
  // }

  // IF/Else version

  // if((abPowered === c**2) || (acPowered === b**2) || (bcPowered === a**2)){
  //     return true;
  // }else{
  //     return false;
  // }

  // TERNARY version

  // return abPowered === c ** 2
  //   ? true
  //   : acPowered === b ** 2
  //   ? true
  //   : bcPowered === a ** 2
  //   ? true
  //   : false;

  // SHORT readable version

  // return ((abPowered === c**2) || (acPowered === b**2) || (bcPowered === a**2));

  // THE SHORTEST version


  return ((a**2 + b**2) === c**2) || ((a**2 + c**2) === b**2) || ((b**2 + c**2) === a**2);
}
```

> **_// Task 3_**
> /_
> დაწერეთ ფუნქცია minMax რომელიც იღებს 1 მასივის ტიპის პარამეტრს
> და დააბრუნებს მასივის ელემენტებს შორის მაქსიმალურს და მინიმალურს ელემენტს .
> მაგ : [2,14,25,75,11,6] თუ კი ამ მასივს გადავცემთ არგუმენტის სახით ფუნქციამ უნდა
> დააბრუნოს "Min value is 2 and Max value is 75"
> _/

```javascript
function minMax(arr) {
  let min = arr[0];
  let max = arr[0];
  for (let element of arr) {
    if (element > max) {
      max = element;
    }
    if (element < min) {
      min = element;
    }
  }
  let result = `"Min value is ${min} and Max value is ${max}"`;
  return result;
}
```

> **_// Task 4_**
> /_
> დაწერეთ ფუნქცია რომელმაც გადაცემული კუთხის მნიშვნელობით უნდა დააბრუნოს
> თუ რა ტიპის კუთხეა .
> კუთხის სახეები:
> Acute angle: An angle between 0 and 90 degrees.
> Right angle: An 90 degree angle.
> Obtuse angle: An angle between 90 and 180 degrees.
> Straight angle: A 180 degree angle.
> _/
>
> // function checkDeg (deg) {
>
> // }
>
> // checkDeg(92)

```javascript
function checkDeg(deg) {

// // SWITCH version

//   switch (true) {
//     case deg >= 0 && deg <= 90:
//        return `${deg} is Acute angle (An angle between 0 and 90 degrees is considered Acute`;
//       break;
//     case deg === 90:
//        return `${deg} is Right angle (An angle that equals to 90 degree is considered Right`;
//       break;
//     case deg >= 90 && deg <= 180:
//        return `${deg} is Obtuse angle (An angle between 90 and 180 degrees is considered Obtuse`;
//       break;
//     case deg === 180:
//        return `${deg} is Straight angle (An angle that equals to 180 degree is considered Straight`;
//       break;
//     case deg > 180 && deg <= 360:
//        return `${deg} is Reflex angle (An angle between 180 and 360 degrees is considered Reflex`;
//        break;
//     default:
//       return `${deg} is not valid angle, please specify correct value`;
//   }

// //  IF/ELSE version
//     if(deg >= 0 && deg <= 90){
//         return `${deg} is Acute angle (An angle between 0 and 90 degrees is considered Acute`;
//     }else if(deg === 90){
//         return `${deg} is Right angle (An angle that equals to 90 degree is considered Right`;
//     }else if(deg >= 90 && deg <= 180){
//         return `${deg} is Obtuse angle (An angle between 90 and 180 degrees is considered Obtuse`
//     }else if(deg === 180){
//         return `${deg} is Straight angle (An angle that equals to 180 degree is considered Straight`;
//     }else if(deg > 180 && deg <= 360){
//         return `${deg} is Reflex angle (An angle between 180 and 360 degrees is considered Reflex`;
//     }else{
//         return `${deg} is not valid angle, please specify correct value`;
//     }

// TERNARY version
    return  deg >= 0 && deg <= 90 ? 'Acute' 
        : deg === 90 ? 'Right' 
        : deg >= 90 && deg <= 180 ? 'Obtuse' 
        : deg === 180 ? 'Straight' 
        : deg > 180 && deg <= 360 ? 'Reflex' 
        : return `${deg} is not valid angle, please specify correct value`;
}

let a = checkDeg(92);
console.log(a);
```

> **_// Task 5**
> /\*
> დაწერეთ ფუნქცია checkStudentGrade რომელიც მიიღებს ობიექტების მასივს.
> მაგალითად [{name: student1; grade : 91}, {name: student2; grade : 71}, {name: student3; grade : 45} ]
> ფუნქციამ სტუდენტის ქულის მიხედვით უნდა განსაზღვროს საფინალო შედეგი finalResult
> ქვემოთ არსებული ცხრილის მიხედვით და ელემენტის ობიექტში დაამატოს propertyს სახით
> მიღებული მასივი დააბრუნებინეთ ფუნქციას .
>
> 0-50 = F
> 51-60 = E
> 61-70 = D
> 71-80 = C
> 81-100 = A
>
> საორიენტაციოდ შედეგი აღნიშNული მაგალითის მიხედვით უნდა იყოს
> [{name: student1; grade : 91 ; finalResult : 'A'}, {name: student2; grade : 71,finalResult : 'C'}, {name: student3; grade : 45, finalResult : > 'F'} ] \*/

```javascript
let exampleData = [{name: 'student1', grade : 91}, {name: 'student2', grade : undefined}, {name: 'student3', grade : 45} ];

function checkStudentGrade(arr){
    let fLow = 0, fHigh = 50, eLow = 51, eHigh = 60, dLow = 61, dHigh = 70, cLow = 71, cHigh = 80, aLow = 81, aHigh = 100;

let newArr = [];
for(let element of arr){
  newArr.push({...element})
};
// SWITCH version 
    for(let element of newArr){
        let result = 'Failed';
        switch(true) {
            case element.grade > cHigh:
                result = 'A';
                break;
            case element.grade > dHigh:
                result = 'C';
                break;
            case element.grade > eHigh:
                result = 'D';
                break;
            case element.grade > fHigh:
                result = 'E';
                break;
            case element.grade <= fHigh:
                result = 'F';
                break;
            default: console.log(`${element.name} did not attend exam!`)
        }   
        element.finalResult = result 
    }
    return newArr;


}
```