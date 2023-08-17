# Object Methods

JavaScript'te bir "nesne" (object), birden çok değeri veya özelliği gruplayan ve bu özelliklere erişimi kolaylaştıran bir veri yapısıdır. Nesneler, adlandırılmış özellik-değer çiftlerini içerir ve fonksiyonlar gibi metotları da barındırabilir. Bu, nesne yönelimli programlamanın temelini oluşturur ve verileri daha düzenli ve yapılandırılmış bir şekilde tutmanıza olanak tanır.

### Object içerisinde fonksiyon oluşturma

```jsx
const person = {
    name: 'John',
    greet: function() { console.log('hello'); }
};
```

### Object dışarıdan değer atama

```jsx
let student = { };

student.name = 'John';

student.greet = function() {
    console.log('hello');
}

student.greet(); // hello
```

### delete

Nesnenin içerisindeki bir değeri silmemizi sağlar.

```jsx
const user = {
	username: 'AzureDiamond',
	password: 'hunter2'
};

delete user.username
console.log(user); // {"password": "hunter2"}
```

### this anahtar kelimesi

Bir nesnenin bir özelliğine aynı nesnenin bir yöntemi içinden erişmek için this anahtar sözcüğünü kullanabiliriz.

```jsx
const person = {
    name: 'John',
    age: 30,

    // accessing name property by using this.name
    greet: function() { console.log('The name is' + ' ' + this.name); }
};

person.greet();
```

Ayrıca fonksiyonun içerisinde tanımlanan değerlere this kullanmadan erişirken, obje içerisindeki değerleri kastetmek için this anahtar kelimesini kullanırız.

```jsx
const person = {
    name: 'John',
    surname: "Deep",
    greet: function() {
        let surname = 'Doe';
        console.log('The name is' + ' ' + this.name + ' ' + surname); },
	 greet2: function() {
        let surname = 'Doe';
        console.log('The name is' + ' ' + this.name + ' ' + this.surname); }
};

person.greet(); // "The name is John Doe"
person.greet2(); // "The name is John Deep"
```

### Object.keys

Bir nesnenin anahtarlarını içeren bir dizi oluşturur.

```jsx
const employees = {
	boss: 'Michael',
	secretary: 'Pam',
	sales: 'Jim',
	accountant: 'Oscar'
};

console.log(Object.keys(employees)); // ["boss", "secretary", "sales", "accountant"]
```

### Object.values

Bir nesnenin değerlerini içeren bir dizi oluşturur.

```jsx
const session = {
    id: 1,
    time: `26-July-2018`,
    device: 'mobile',
    browser: 'Chrome'
};

console.log(Object.values(session)); // [1, "26-July-2018", "mobile", "Chrome"]
```

### **[O](https://www.digitalocean.com/community/tutorials/how-to-use-object-methods-in-javascript#object-entries)bject.enteries()**

Bir nesnenin iç içe anahtar ve değer çiftlerini oluşturan bir dizi döndürür.

```jsx
const operatingSystem = {
    name: 'Ubuntu',
    version: 18.04,
    license: 'Open Source'
};

console.log(Object.entries(operatingSystem));
// Çıktı :
[
    ["name", "Ubuntu"]
    ["version", 18.04]
    ["license", "Open Source"]
]
```

```jsx
const operatingSystem = {
    name: 'Ubuntu',
    version: 18.04,
    license: 'Open Source'
};

for(let [key, value] of Object.entries(operatingSystem)){
  console.log(key + " = " + value)
}
// Çıktı :
"name = Ubuntu"
"version = 18.04"
"license = Open Source"
```

### Object.assign()

Birden fazla nesnenin değerlerini birleştirmek için kullanılır

```jsx
const name = {
    firstName: 'Philip',
    lastName: 'Fry'
};

const details = {
    job: 'Delivery Boy',
    employer: 'Planet Express'
};

console.log(Object.assign(name, details));
// Çıktı :
{firstName: "Philip", lastName: "Fry", job: "Delivery Boy", employer: "Planet Express"}
```

spread ile de birleştirme yapılabilir.

```jsx
const name = {
    firstName: 'Philip',
    lastName: 'Fry'
};

const details = {
    job: 'Delivery Boy',
    employer: 'Planet Express'
};

const character = {...name, ...details}
```

### Object.freeze()

Belirlenen nesnedeki değerlerin değiştirilmesi, silinmesi ve eklenmesini engeller.

```jsx
const user = {
	username: 'AzureDiamond',
	password: 'hunter2'
};

const newUser = Object.freeze(user);

newUser.password = '*******';
newUser.active = true;

console.log(newUser); // {username: "AzureDiamond", password: "hunter2"}
```

### Object.seal()

Belirlenen nesnedeki değerlerin değiştirilmesine izin verir fakat  değer eklenmesini ve silinmesini engeller.

```jsx
const user = {
	username: 'AzureDiamond',
	password: 'hunter2'
};

const newUser = Object.seal(user);

newUser.password = '*******';
newUser.active = true; //eklenmez
delete newUser.username; //silinmez

console.log(newUser); // {username: "AzureDiamond", password: "*******"}
```

### **shorthand**

Nesne yöntemlerinizi anahtar sözücü atamadan daha pratik bir şekilde tanımlayabiliriz.

```jsx
// greet 'e bir fonksiyon atadık ve artık greet olarak bu fonksiyonu çağırbiliriz.
let person = {
    firstName: 'John',
    lastName: 'Doe',
    greet: function () {
        console.log('Hello, World!');
    }
};

person.greet(); // "Hello, World!";

// bir anahtar sözcüğü tanımlamadan direk fonksiyonu oluşturduğumuzda nesnenin
// içerisine otomatik olarak fonksiyon adı ile anahtar sözcüğü oluşturulur.
let person = {
    firstName: 'John',
    lastName: 'Doe',
    greet() {
        console.log('Hello, World!');
    }
};

person.greet(); "Hello, World!";
```