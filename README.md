# Dictionaries lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

- Create an instance of a dictionary called `citiesDict` that maps 3 countries to their capital cities.

- Add two more countries to your dictionary.

- Translate at least 3 of the capital names into another language.
```swift

var citiesDict: [String:String] = ["Germany":"Berlin", "Australia":"Canberra", "Canada":"Ottawa"]
//add two more countries
    citiesDict["Malaysia"] = "Kuala Lumpur"
    citiesDict["Turkey"] = "Ankara"
    
    print(citiesDict)

//Translate 3 of the capital names in another language
    citiesDict ["Germany"] = "\u{411}\u{435}\u{440}\u{43B}\u{438}\u{43D}"
    citiesDict ["Canada"] = "\u{41E}\u{442}\u{442}\u{430}\u{432}\u{430}"
    citiesDict ["Malaysia"] = "\u{41A}\u{443}\u{430}\u{43B}\u{430}\u{2D}\u{41B}\u{443}\u{43C}\u{43F}\u{443}\u{440}"

    print(citiesDict)
```

## Question 2

`var someDict:[String:Int] = ["One": 1, "Two": 4, "Three": 9, "Four": 16, "Five": 25]`

- Using `someDict`, add together the values associated with "Three" and "Five" and print the result.
```swift

    var someDict:[String:Int] = ["One": 1, "Two": 4, "Three": 9, "Four": 16, "Five": 25]
    //add value of "Three" and "Five"
        var threeFive:Int = someDict["Three"]! + someDict["Five"]!
        print(threeFive)
```
- Add values to the dictionary for the keys "Six" and "Seven".
```swift
someDict["Six"] = 6
someDict["Seven"] = 7
```

- Make a key called `productUpToSeven` and set its value equal to the product of all the values.
```swift
    var productUpToSeven = 1
        for (key, value) in someDict {
            productUpToSeven = (productUpToSeven * value)
        }
    print(productUpToSeven)
```
- Make a key called `sumUpToSix` and set its value equal to the sum of the keys "One", "Two", "Three", "Four", "Five" and "Six".
```
var sumUpToSix = 0
    for (key, value) in someDict {
        if key != "Seven" {
            sumUpToSix = (sumUpToSix + value)
        }
    }
    print(sumUpToSix)
```
- Remove the new keys made in the previous two steps
```swift

    let removedValue = someDict.removeValue(forKey: "Six")
    someDict["Seven"] = nil
    print(someDict)

```
- Add 2 to every value inside of `someDict`.
```swift
    for (key, value) in someDict {
    someDict[key] = value + 2
    }
    print(someDict)
```


## Question 3

Create a variable that is explicitly typed as a dictionary that maps strings to floating point numbers. Initialize the variable to the data shown in the table below which lists an author name and their comprehensibility score.

| Author Name |	Score |
| :--: | :--: |
| Mark Twain |	8.9 |
| Nathaniel Hawthorne	| 5.1 |
| John Steinbeck	| 2.3 |
| C.S. Lewis | 9.9 |
| Jon Krakauer | 6.1 |

Using the dictionary created in the previous problem, do the following:

- Print out the floating-point score for “John Steinbeck”.
```swift

print("John Steinbeck : \(authorsAndScores["John Steinbeck"]!)")

```
- Add an additional author named “Erik Larson” with an assigned score of 9.2.
```swift
    authorsAndScores["Erik Larson"] = 9.2
    print(authorsAndScores)
```
- Write an if/else statement that compares the score of John Krakaur with Mark Twain. Print out the name of the author with the highest score.
```swift
if authorsAndScores["Jon Krakauer"] ?? 0 >     authorsAndScores["Mark Twain"] ?? 0 {
    print("Jon Krakauer has the highest score")
    } else {
    print("Mark Twain has the highest score")
}
```
- Use a for-loop to iterate through the dictionary you created at the beginning of the problem, and print out the content in the form of key: value, one entry per line.
```swift
    for (key, value) in authorsAndScores {
        print("\(key), \(value)")
    }
```

## Question 4

You are given a dictionary code of type [String:String] which has values for all lowercase letters. The code dictionary represents a way to encode a message. For example if code["a"] = "z" and code["b"] = "x" the encoded version if "ababa" will be "zxzxz". You are also given a message which contains only lowercase letters and spaces. Use the `code` dictionary below to encode the message and print it.

```swift
var code = [
    "a" : "b",
    "b" : "c",
    "c" : "d",
    "d" : "e",
    "e" : "f",
    "f" : "g",
    "g" : "h",
    "h" : "i",
    "i" : "j",
    "j" : "k",
    "k" : "l",
    "l" : "m",
    "m" : "n",
    "n" : "o",
    "o" : "p",
    "p" : "q",
    "q" : "r",
    "r" : "s",
    "s" : "t",
    "t" : "u",
    "u" : "v",
    "v" : "w",
    "w" : "x",
    "x" : "y",
    "y" : "z",
    "z" : "a"
]
```
```swift
var message = "hello world"
var encodedMessage = ""


for char in message {
    if char == " " {
        encodedMessage.append(char)
    }
    
    for (key, value) in code {
        if key.contains(char) {
            encodedMessage.append(value)
        }
    }
}
print(encodedMessage)

```
You are also given an `encodedMessage` which contains only lowercase letters and spaces. Use the `code` dictionary to decode the message and print it.
`var encodedMessage = "uijt nfttbhf jt ibse up sfbe"`
```swift
var encodedMessage = "uijt nfttbhf jt ibse up sfbe"
var message = ""
    for c in encodedMessage {
        for (key, value) in code {
            if String(c) == value {
                message.append(key)
            } else if String(c) == " " {
                message.append(c)
                break
            }
        }
    }
print(message)
```


## Question 5

You are given an array of dictionaries. Each dictionary in the array contains exactly 2 keys `“firstName”` and `“lastName”`. Create an array of strings called `firstNames` that contains only the values for `“firstName”` from each dictionary.

```swift
var people: [[String:String]] = [
    [
        "firstName": "Calvin",
        "lastName": "Newton"
    ],
    [
        "firstName": "Garry",
        "lastName": "Mckenzie"
    ],
    [
        "firstName": "Leah",
        "lastName": "Rivera"
    ],
    [
        "firstName": "Sonja",
        "lastName": "Moreno"
    ],
    [
        "firstName": "Noel",
        "lastName": "Bowen"
    ]
]
var firstNames: [String] = []

for person in people {
    if let firstname = person["firstName"] {
        firstNames.append(firstname)
    }
}
print(firstNames)
```
```
Now, create an array of strings called `fullNames` that contains the values for `“firstName”` and `“lastName”` from the dictionary separated by a space.
```
```swift
var fullName: [String] = []

for person in people {
    if let firstnames = person["firstName"], let lastnames = person["lastName"] {
        let fullnames = "\(firstnames) \(lastnames)"
        fullName.append(fullnames)
    }
}

print(fullName)
```

## Question 6

You are given an array of dictionaries. Each dictionary in the array describes the score of a person. Find the person with the best score and print his full name.

```swift
var peopleWithScores: [[String: String]] = [
    [
        "firstName": "Calvin",
        "lastName": "Newton",
        "score": "13"
    ],
    [
        "firstName": "Garry",
        "lastName": "Mckenzie",
        "score": "23"
    ],
    [
        "firstName": "Leah",
        "lastName": "Rivera",
        "score": "10"
    ],
    [
        "firstName": "Sonja",
        "lastName": "Moreno",
        "score": "3"
    ],
    [
        "firstName": "Noel",
        "lastName": "Bowen",
        "score": "16"
    ]
]

var highestScore = 0
var firstNames = ""
var lastNames = ""

for names in peopleWithScores {
    if let score = names ["score"] {
        if let newScore: Int = Int(score){
            if newScore > highestScore{
                highestScore = newScore
                if let firstName = names["firstName"], let lastName = names["lastName"]{
                firstNames = firstName
                lastNames = lastName
                }
            }
        }
    }
}

print("\(firstNames) \(lastNames) has the highest score of \(highestScore)")

```
Print out the dictionary above in the following format:  **full name - score**
```swift
for names in peopleWithScores {
    if let firstName = names["firstName"], let lastName = names["lastName"], let scores = names ["score"] {
        print("\(firstName) \(lastName) - score \(scores)")
    }
}
```
## Question 7

`var numbers = [1, 2, 3, 2, 3, 5, 2, 1, 3, 4, 2, 2, 2]`

You are given an array of integers. The frequency of a number is the number of times it appears in the array. Find out the frequency of each one.

Print the numbers in ascending order followed by their frequency.
```swift
var numbers = [1, 2, 3, 2, 3, 5, 2, 1, 3, 4, 2, 2, 2]
var frequency: [Int:Int] = [:]
var newNumbers: [Int] = []

for number in numbers {
    if let oldFreq = frequency[number] {
    frequency[number] = oldFreq + 1
    } else {
        newNumbers.append(number)
        frequency[number] = 1
    }
}

newNumbers.sort(by: <)
for number in newNumbers {
print("\(number) \(frequency[number]!)")
}
```

## Question 8

Print the most common letter in the string below:

```swift

var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."

var frequency = [Character: Int]()
var mostCommonLetter: Character = " "
var count:Int = 0

for c in myString where c != " "{
    if frequency.keys.contains(c) {
        frequency[c] = frequency[c]! + 1
    } else {
    frequency[c] = 1
    }

    if let temp = frequency[c] as? Int {
        if temp > count{
        mostCommonLetter = c
        count = temp
        }
    }
}

print("The most common letter used in the paragraph is \(mostCommonLetter)")
```


## Question 9

Write code that creates a dictionary where the keys are Ints between 0 and 20 inclusive, and each key's value is its cube.
```swift
var cubeDict : [Int:Int] = [:]
    for i in 0...20{
        cubeDict[i] = i * i * i
    }
print(cubeDict)
```

## Question 10

Write code that iterates through `testStates` and prints out whether or not that key is in `statePop`.

```swift
let statePop = ["Alabama": 4.8, "Alaska": 0.7, "Arizona": 6.7, "Arkansas": 3.0]
let testStates = ["California","Arizona", "Alabama", "New Mexico"]

for states in testStates {
    if statePop.keys.contains(states) {
        print("\(states) is in the statePop")
    } else {
        print("\(states) is NOT in the statePop")
    }
}

```


## Question 11

You are given the dictionary `deposits`, which maps a persons name to an array of deposits that have been made to their account.

a) Write code to to print the name and total amount deposited of the person who recieved the most money.

b) Create an array called `stolenCents`, iterate over deposits for each person and steal their cents! ... like Office Space or Superman 3. Calculate the decimal part of each value, add it to the `stolenCents` array and round down the value in the dict.

c) How much money did you steal?

```swift
var deposits: [String: [Double]] = [
 "Williams" : [300.65, 270.45, 24.70, 52.00, 99.99],
 "Cooper" : [200.56, 55.00, 600.78, 305.15, 410.76, 35.00],
 "Davies" : [400.98, 56.98, 300.00],
 "Clark" : [555.23, 45.67, 99.95, 80.76, 56.99, 46.50, 265.70],
 "Johnson" : [12.56, 300.00, 640.50, 255.60, 26.88]
]
```


## Question 12

Print the second most common letter in the string below:

`var myString = "We're flooding people with information. We need to feed it through a processor. A human must turn information into intelligence or knowledge. We've tended to forget that no computer will ever ask a new question."`


## Question 13

Given the below 4 arrays of Ints,

a) create a new array, sorted in ascending order, that contains all the values without duplicates.

b) create another new array that contains unique values that appear in all 4 arrays.

```swift
let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]

let newArr = [arr1, arr2, arr3, arr4]

var noDuplicates: [Int] = []

for arr in newArr {
    for int in arr {
        if !noDuplicates.contains(int) {
        noDuplicates.append(int)
        }
    }
}

print(noDuplicates.sorted())
```
b) create another new array that contains unique values that appear in all 4 arrays.

```swift

let arr1 = [2, 4, 5, 6, 8, 10, 12]
let arr2 = [1, 2, 3, 4, 5, 6]
let arr3 = [5, 6, 7, 8, 9, 10, 11, 12]
let arr4 = [1, 3, 4, 5, 6, 7, 9]

let newArr = [arr1, arr2, arr3, arr4]
var uniqueValues: [Int] = []

    for int in arr1 where arr2.contains(int) && arr3.contains(int) && arr4.contains(int) {
        uniqueValues.append(int)
    }

    print(uniqueValues)
```

## Question 14

Given the following exert from the Declaration of Independence, find the most frequent word that is longer than 5 characters.

 - use `components(separatedBy:)` to break up the string into an array.

 - use `CharacterSet.punctuationCharacters` in union with any other characters you don't want in your array, like spaces and new lines.

 ```swift
let declarationOfIndependence = """
When in the Course of human events, it becomes necessary for one people to dissolve the
political bands which have connected them with another, and to assume among the powers of the
earth, the separate and equal station to which the Laws of Nature and of Nature's God entitle
them, a decent respect to the opinions of mankind requires that they should declare the causes
which impel them to the separation.

We hold these truths to be self-evident, that all men are created equal, that they are endowed by
their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit
of Happiness. That to secure these rights, Governments are instituted among Men, deriving
their just powers from the consent of the governed, That whenever any Form of Government
becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to
institute new Government, laying its foundation on such principles and organizing its powers in
such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence,
indeed, will dictate that Governments long established should not be changed for light and
transient causes; and accordingly all experience hath shewn, that mankind are more disposed to
suffer, while evils are sufferable, than to right themselves by abolishing the forms to which they
are accustomed. But when a long train of abuses and usurpations, pursuing invariably the same
Object evinces a design to reduce them under absolute Despotism, it is their right, it is their duty,
to throw off such Government, and to provide new Guards for their future security. Such has
been the patient sufferance of these Colonies; and such is now the necessity which constrains
them to alter their former Systems of Government. The history of the present King of Great
Britain is a history of repeated injuries and usurpations, all having in direct object the
establishment of an absolute Tyranny over these States. To prove this, let Facts be submitted to a
candid world.
"""
```
