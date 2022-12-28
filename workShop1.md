>***Task 1 :***
>ანა არის 28 წლის , ხოლო მისი ძმა ლევანი 21ის .
>
>გამოიყენეთ ცვლადები , რომელშიც შეინახავთ თითოეულის ასაკს და სახელს.
>განსაზღვრეთ ახალი სტრინგ ტიპის ცვლადი რომელიც შეინახასვს ტექსტს :
>'ანა ლევანზე 7 წლით უფროსია'
>სხვაობა დათვალეთ დინამიურად ცვლადების და არითმეტიკული ოპერატორების გამოყენებით
>დალოგეთ ზემოაღნიშნული ცვლადი . 

```javascript
//პირველი ცვლადი
let sister = {
    familyMember: true,
    age: 28,
    name: 'ანა'
}
//მეორე ცვლადი
let brother = {
    familyMember: true,
    age: 21,
    name: 'ლევანი'
}

//სასურველი შედეგის დინამიურად მისაღებად სახელი "ლავენი" მოითხოვს ცვლილებას "ზე" თანდებულის დართვისას
//nameModifier იქნება დამხმარე ფუნქცია სახელის სასურველ ფორმაში ჩასასმელად
let nameModifier = name => name.split('').slice(0, name.length-1).join('');

//პასუხი
let solution = `${sister.name} ${nameModifier(brother.name)}ზე ${sister.age-brother.age} წლით უფროსია`;
console.log(solution);
```

***Task 2 :*** 
>გვაქვს სტუდენტების სახელების კენტი სიგრძის მასივი ['John','Sam','Ann','Will','Andrew','Joseph','Lorelai','Amelie','Den']
>დალოგეთ სიის ზუსტად შუაში მყოფი სახელი.

```javascript
//იმისთვის რომ ვიპოვოთ შუში მყოფი ელემენტის სახელი, მასივში შემავალაი ელემენტების რაოდენობა უნდა გავყოთ ორზე და გავითვალისწინოთ რომ
//მასივის პოზიციონირება იწყება 0-დან, შესაბამისად მიღებული განაყოფი უნდა დავამრგვალოთ ქვემოთ. * ათვლა რომ 1 დან იწყებოდეს დამრგვალება 
//მოგვიწევდა ზემოთ. 
let arr1 = ['John','Sam','Ann','Will','Andrew','Joseph','Lorelai','Amelie','Den'];

//დამხმარე ფუნქცია შუაში მყოფი ელემენტის ინდექსის მოსაძებნად
let middleIndexFinder = array => Math.floor(array.length/2);

//დამხმარე ცვლადი, ნაპოვნი ინდექსის შესანახად
let middleIndex = middleIndexFinder(arr1);

//პასუხი
console.log(`მოცემული მასივის "ზუსტად" შუაში მდგომი სახელია: ${arr1[middleIndex]}`);
```

***Task 3 :*** 
>Part 1 : შექმენით სტუდენტის ობიექტი , რომელსაც აქვს 5 property : firstName; lastName; age; subjects; roommate;
>firstname,lastname - string type
>age - number
>subject - object (array of strings)
>roommate - object (რომელსაც აქვს თავის მხრივ ორი property : fullname , age )
>
>მნიშვნელობები მიანიჭეთ ტიპების მიხედვით . subject- მასივი უნდა შედგებოდეს არანაკლებ 5 ელემენტისგან
>
>Part 2 : 
>    for ციკლის გამოყენებით დალოგეთ თუ რა საგნებს სწავლობს სტუდენტი , subject arrayს ელემენტები.
>
>    ასევე შექმენით ახალი ცვლადი fullName რომელშიც შეინახავთ სტუდენტის სრულ სახელ და გვარს.
>
>    ეს fullName მნიშვნელობასთან ერთად დაამატეთ სტუდენტის ობიექტს. 
>     
>    დაამატეთ ცვლადი result რომლის მნიშვნელობაც იქნება წინადადება : 
>        ' (სტუდენტის სახელი და გვარი) არის age წლის და მისი რუმმეითი არის : roommate fullname
    
```javascript
//სტუდენტის ობიექტი
let student = {
    firstName: 'ალექსანდრე',
    lastName: "იმნაიშვილი",
    age: 30,
    subjects: ['HTML', 'CSS', 'JavaScript', 'React', 'Project Management'],
    roommate: {
        fullName: 'ლევან იმნაიშვილი',
        age: 27
    }
}

//სტუდენტის სრული სახელი
let fullName = `${student.firstName} ${student.lastName}`;

//ვამატებთ სტუდენტის ობიექტს სრულ სახელს
student.fullName = fullName;

//კონსოლში გამოგვაქვს საგნების სია
for(let i=0; i<student.subjects.length; i++){
    console.log(student.subjects[i]);
}

//კონსოლში საგნების სიის გამოტანის ალტერნატიული მეთოდი
//დამხმარე ფუნქციის გამოყენებით
let subjectsLogger = arg => {
    console.group(`${arg.firstName}ს გავლილი აქვს შემდეგი საგნები:`);
    for(let i=0; i<arg.subjects.length; i++){
        console.log(arg.subjects[i]);
    }
    console.groupEnd();
}
//ვიძახებთ დამხმარე ფუნქციას და ვაწვდით არგუმენტად სტუდენტის ობიექტს
subjectsLogger(student);

//ვამატებთ 'result'ცვლადს დავალებაში მითითებული მნიშვნელბით

let result = `${student.fullName} არის ${student.age} წლის და მისი რუმმეითი არის: ${student.roommate.fullName}`

//ვამოწმებთ შედეგს
console.log(result);
```

***Task 4 :*** 
>გვაქვს  მასივი : ["Banana", "Orange", "Apple", "Mango",2,12]
>გამოიყენეთ while ციკლი და მანამ სანამ მასივის ელემენტის ტიპი არის სტრინგი
>დალოგეთ ეს ელემენტი.

```javascript
let arr2 = ["Banana", "Orange", "Apple", "Mango",2,12];

//მთვლელი მე-4 დავალებისთვის
let i = 0;

//პასუხი
while(typeof(arr2[i]) === 'string'){
    console.log(arr2[i]);
    i++;
}
```

***Task 5 :*** 
>გვაქვს მასივი : [12,23,43,11,9,2,121,90]
>თუ მასივის ელემენტი მეტია 31ზე და თან არის ლუწი მაშინ დალოგეთ : 'Element is greater than provided value and is EVEN'
>თუ მასივის ელემენტი ნაკლებია 31ზე და თან არის კენტი მაშინ დალოგეთ : 'Element is less than provided value and is ODD'

```javascript
let arr3 = [12,23,43,11,9,2,121,90];
let providedValue = 31;

//პასუხი
for(let i=0; i<arr3.length; i++){
    if(arr3[i] > providedValue && arr3[i]%2 === 0){
        console.log(`${arr3[i]} Element is greater than provided value (${providedValue}) and is EVEN`);
    }else if(arr3[i] < providedValue && arr3[i]%2 !== 0){
        console.log(`${arr3[i]} Element is less than provided value (${providedValue}) and is ODD`);
    };
}
```