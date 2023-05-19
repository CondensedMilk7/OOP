---
theme: default
background: https://source.unsplash.com/collection/94734566/1920x1080
highlighter: shiki
lineNumbers: true
transition: slide-left
---

# Object Oriented Programming (OOP)

ობიექტზე ორიენტირებული პროგრამირება

---

# რა არის OOP

OOP არის დიზაინის სისტემა, სადაც:

- თითოეული ობიექტი წარმოადგენს ამ სისტემის რაღაც ასპექტს;
- ობიექტები შეიცავენ ფუნქციებსა და მონაცემებს;
- ობიექტები იძლევიან ინტერფეისებს რათა პროგრამის სხვადასხვა ნაწილებმა ისინი გამოიყენონ;
- მიუხედავად ამისა ობიექტები ინარჩუნებენ კერძო შინაგან მდგომარეობას;
- სისტემის სხვა ნაწილებისთვის აუცილებელი არ არის ამ ობიექტის შინაგან მდგომარეობაზე წვდომა.

---

# კლასი

როცა სისტემას ბვადგენთ OOP-ის მეშვეეობით, ჩვენ ვქმნით ობიექტების აბსტრაქტულ
განსაზღვრებებს. ამას ეწოდება **კლასი**.

პროფესორის კლასი ფსევდო კოდში:

```js
class Professor
    properties
        name
        teaches
    methods
        grade(paper)
        introduceSelf()
```

ეს განსაზღვრავს `Professor` კლასს, რომელსაც აქვს:

- ორი მონაცემი (თვისება): `name` და `teaches`
- ორი მეთოდი: `grade*()` და `introduceSelf()`

---

# კონსტრუქტორი

კლასი თავისთავად არაფერს აკეთებს, ის ერთგვარი _მონახაზია_, რომლითაც შეგვიძლია
ამ კლასის სტრუქტურის მქონე მუშა ობიექტების შექმნა. ამ ობიექტებს ეწოდებათ კლასის
**ინსტანციები**. კლასის ინსტანციას ქმნის განსაკუთრებული ფუნქცია **constructor**.

```js
class Professor
    properties
        name
        teaches
    constructor
        Professor(name, teaches)
    methods
        grade(paper)
        introduceSelf()
```

კონსტრუქტორით ინსტანციის შექმნა:

```js
const pridon = new Professor("Pridon", "Psychology");
const gabriel = new Proffessor("Gabriel", "Philosophy");

pridon.teaches; // Psychology
pridon.introduceSelf(); // 'Hello, my name is Pridon and I am your Psychology professor'
```

---

# მემკვიდრეობა

მემკვიდრეობით შესაძლებელია ერთმა კლასმა მიიღოს მეორე კლასის სტრუქტურა.

სტუდენტის კლასი, რომელსაც საერთო აქვს პროფესორთან:

```js
class Student
    properties
        name
        year
    constructor
        Student(name, year)
    methods
        introduceSelf()
```

---

# მემკვიდრეობის შემუშავება

```js {1-7|1-16|all}
class Person
    properties
        name
    constructor
        Person(name)
    methods
        introduceSelf()

class Professor : extends Person
    properties
        teaches
    constructor
        Professor(name, teaches)
    methods
        grade(paper)
        introduceSelf()

class Student : extends Person
    properties
        year
    constructor
        Student(name, year)
    methods
        introduceSelf()
```

---

# სუპერკლასები და ქვეკლასები

Student და Professor გამოდიან Person-ის ქვეკლასები, რომელიც თავის მხრივ სუპერკლასია.

```js
walsh = new Professor("Pridon", "Psychology");
walsh.introduceSelf(); // 'My name is Professor Pridon and I will be your Psychology professor.'

summers = new Student("Ana", 1);
summers.introduceSelf(); // 'My name is Ana and I'm in the first year.'
```

`introduceSelf()`-ის default იმპლემენტაცია:

```js
pratt = new Person("Giorgi");
pratt.introduceSelf(); // 'My name is Giorgi.'
```

**პოლიმორფიზმი** - როცა მეთოდს გააჩნია იგივე სახელი, მაგრამ განსხვავებული იმპლემენტაცია
სხვა კლასებში. როცა ქვეკლასში მეთოდი ანაცვლებს სუპერკლასის იმპლემენტაციას, მაშინ
ქვეკლასი **override**-ს უკეთებს სუპერკლასს.

---

# ენკაფსულაცია

ობიექტები გვაწვდიან ინტერფეისებს, რათა ისინი მოვიხმაროთ, მაგრამ ამასთანავე
მათ გააჩნიათ შინაგანი კერძო (**private**) მდგომარეობა. ამ მდგომარეობისადმი
წვდომა აქვს მხოლოდ ამ კლასის მეთოდებს და არა სხვა ობიექტებს. ენკაფსულაცია არის
სახალხო და კერძო შინაგანი მდგომარეობების განცალკევება.

ენკაფსულაციის დახმარებით შეიძლება ობიექტის შინაგანი იმპლემენტაციის შეცვლა ერთგან, რათა ცვლილება აისახოს ყველგან, სადაც კლასის იმპლემენტაციაა.

---

პრობლემური გზა:

```js
if (student.year > 1) {
  // allow the student into the class
}
```

ეფექტური გზა

```js
class Student : extends Person
    properties
       year
    constructor
       Student(name, year)
    methods
       introduceSelf()
       canStudyArchery() { return this.year > 1 }
```

```js
if (student.canStudyArchery()) {
  // allow the student into the class
}
```

---
layout: center
---

# შეკითხვები?
