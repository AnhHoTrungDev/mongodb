# \*dùng explain("executionStarts") xem thông tin cụ thể của truy vấn

## what is index

-index hổ trợ tìm kiếm trong mongodb

-Nếu không có index thì mongo sẽ scan toàn bộ các document => rất mất thời gian

-Index giúp giới hạn document phải scan giảm thời gian tìm kiếm truy vấn

- Hổ trợ trên tất cả các field trong collection

- Luôn có field mặt định đc đánh index (\_id)

#### điểm mạnh

-Giảm thời gian query

-Giới hạn số document đc duyệt

-Tăng hiệu xuất

#### điêmt yếu

-Tốn thêm không gian lưu trữ cho index

## Toán Tử

-$lt:... ex : db.test.find({"poin":($lt:5)}) tìm số bài test có điểm < 5

-$gt:... ex : db.test.find({"poin":($gt:5)}) tìm số bài test có điểm > 5

-$all:... ex:db.inventory.find( { tags: { $all: ["red", "blank"] } } )
tìm toàn bộ các document với array tag có giá trị red black

## Embedded Documents

Khi thiết kế dữ liệu kiểu Embedded thì chúng ta không cần tạo ra nhiều collection để lưu trữ, mà sẽ lưu trữ tất cả vào một collection.

link:=> https://viblo.asia/p/query-an-array-of-embedded-documents-in-mongodb-V3m5WBdWlO7

## Single Field Indexes

-MongoDb hỗ trợ người dùng định nghĩa index theo chiều tăng dần hoặc giảm dần trên 1 trường của document

key = field đc gắn index với 1(tăng dần) và -1 (giảm dần)

db.records.createIndex( { key: 1 } )

## Compound Indexes

-có thể đánh index cho nhiều field để giới hạn số document đc duyệt qua

## Query on Embedded

_*find with *_

## Text Index

-dùng để search string

## Unique Index

- đảm bảo nó ko trùng nhau

## TTL Index (time -to - live)

- xóa document sau 1 thời gian luw trữ

ex: db.users.createIndex({
user_name:"text"
..

},{
name:"search*text" => \*\_custome name*_
default:language: "none" => \_\_set ngôn ngữ mặc định_\*
})

## Sparse Index

- Chỉ scan qua các document mà feild được đánh đấu index không null

## Partial Index

- xử dụng toán tử để giới hạn bản ghi phải scan qua => tăng hiệu xuất , giảm time thực thi

link https://docs.mongodb.com/manual/core/index-partial/

## multikey indexes

mongo tạo index cho từng giá trị trong mãng hổ trợ truy vấn các trường là mãng

-hạn chế không lập dc multikey nếu có nhiều trường có kiểu dữ liệu là mãng

ex:db.coll.find(x :{ $elemMatch:{$gt :22,\$lt:55}})

link https://medium.com/@bloomaman/mongodb-multikey-indexes-and-index-intersection-45f6b065408a

ex: data =
{item: 35, prices:[250,35]}
......
{item: 106, prices:[1500,65]}

//tạo index

db.ensureIndex({item:1, prices:1});

//select

db. coll. find({item: {$gt:12, $lt:65}});

## link tài liệu

https://drive.google.com/file/d/1dVN0UnIYD3VpZ6HGfSwZM5NLeEWLdKpM/view
