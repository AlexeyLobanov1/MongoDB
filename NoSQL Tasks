1.Знайти всіх людей, зп більше 500. за спаданням.
```js
db.People
  .find({"Salary" : { "$gt" : 500 }})
  .sort({"Salary" : -1});
```

2.Людей 300 до 500. вивести іх клас.
db.People.find({
"Salary": {$gte: 300, $lte: 500}
},
{
"Clases_name": 1
});

3.Знайти людей з ЗП 53 и 368.
 db.People.find({ Salary: { $in: [100, 500] } })
 
4.Знайти суму всіх зарплат всіх людей.
db.People.aggregate([
{
$group: {
_id: null,
sum: { $sum: "$Salary" }
}
}
]);

5.Знайти суму зарплат всіх людей класу jun.
db.People.aggregate([
{
$match: {
Clases_name: "jun"
}
},
{
$group: {
_id: null,
sum: { $sum: "$Salary" }
},
}
])

6.Знайти всіх людей в який імя закінчуется на МА.
db.People.find({ Name: { $regex: "ma$" } });

Знайти людей в яких в імені є буква О.
db.People.find({ People_name: { $regex: /o/ } });

Знайти всіх людей jun та sen.
db.People.find({ Clases_name: { $in: ["jun", "sen"] } });

Знайти всіх людей jun та sen старше 1997 року.
db.People.find({
$and: [
{ Clases_name: { $in: ["jun", "sen"] } },
{ Date: { $gt: "1997" } }
]
});

Знайти всіх людей в яких ім'я починається на Н або М з ЗП більше 1400.
db.People.find({
$or: [
{ People_name: { $regex: "^D" } },
{ People_name: { $regex: "^I" } }
],
Salary: { $gt: 1400 }
});

7.Знайти всіх людей midd між 1997 иа 1999 роком включно.
db.People.find({
Clases_name: "midd",
Date: {
$gte: "1997.01.01",
$lte: "1999.12.31"
}
});

8.Знайти середню ЗП по всім.
db.People.aggregate([
{
$group: {
_id: null,
avg: { $avg: "$Salary" }
},
}
]);

9.Знайти всіх людей які належать до класу jun в якому таблиця міні менше 500.
db.People.find({
$and: [
{ Clases_name: "jun" },
{ Salary: { $lte: 500 } }
]});

10.Знайти всіх людей класу, в назві якого є буква "I".
db.People.find({ Clases_name: { $regex: /i/ } })

11.Вивести середні ЗП по кожному класу. 
db.People.aggregate([
{
$group: {
_id: "$Clases_name",
avg: { $avg: "$Salary" }
},
}
]);

12.Вивести суми зарплат по кожному класу.
db.People.aggregate([
{
$group: {
_id: "$Clases_name",
sum: { $sum: "$Salary" }
},
}
]);

13.Знайти всіх людей в яких зп більше 500 або вони старше 25 років.
db.People.find({
$or: [
{ Salary: { $gte: 500 } },
{ Date: { $lt: "1997" } }
]
});

14.Вивести всіх людей але щоб колонка Ім'я була унікальною.
db.People.distinct("People_name");

15.Уявляємо що зп вказана в таблиці в долларах. Вивести ЗП людей в гривні. 
db.People.aggregate([
{
$project: {
People_name: 1,
SalaryUAH: {
$multiply: ["$Salary", 38]}
}
}
])

16.Знайти 5-ть найстаріших замовлень.
1) db.Orders.aggregate([
{ $sort: { Order_date: 1 } },
{ $limit: 5 }
]);

2) db.Orders.find().sort({"Order_date": 1}).limit(5);

17.Знайти замовлення, де люди відносяться до класу jun.
db.Orders.aggregate([
{
$lookup: {
from: "People",
localField: "Peopleid",
foreignField: "_id",
as: "People"
},
},
{
$match: {
"People.Clases_name": "jun"
},
}
]);

18.Вивести кількість замовлень, в яких ім'я людини закінчується на А і вони midd клас.
db.Orders.aggregate([
{
$lookup: {
from: "People",
localField: "Peopleid",
foreignField: "_id",
as: "People"
}
},
{
$match: {
"People.People_name": {$regex: "a$" },
Clases_name: "midd"
}
}
]);
