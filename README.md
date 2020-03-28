## start

sudo systemctl start mongod || sudo systemctl daemon-reload

## check mongodb run

sudo systemctl status mongod

## stop

sudo systemctl stop mongod

## Restart MongoDB

sudo systemctl restart mongod

## create

use "nameDatabase"

## insert

db."name collection".insert({key:value,key:value})

## find data

db."name collection".find()

// display đẹp hơn

db."name collection".find().pretty()

## drop

// delete all data in databse

db.dropDatabase()

## remove document

db."name collection".remove({key:value})

## Export Collection

-d = database

-c = collection

-o = out

testExport = nameFile export

mydb = name database

mongoexport -d mydb -c users -o testExport.json

#### Export csv

mongoexport -d mydb -c users --type=csv -o "home/anh/testExport.csv" \_id,user_name,password

##### \_id,user_name,password => các trường muốn export

- "_ubntu home/anh => file home ( cái này mặc định cấu hình sẽ tạo file mới) _"

## Import Collection

home/anh/testExport.json= link save file

mongoimport -d mybd -c users --file home/anh/testExport.json

#### Import csv

mongoimport -d mybd -c users --file "home/anh/testExport.csv" --headerline

## Export database (full database )

"_/home/anh => link save data => ( bắt buộc )_"

mongodump -d mydb -o "/home/anh"

## Import database (full database )

"_/home/anh/mydb_" => link save

"_restore_" => name (gì cũng đc)

mongorestore -d restore '/home/anh/mydb'

## example

#### insert data

db.users.insert({user_name: "Anh.Ho",
password :"23123",
email :"abc.com",
skill:["nestJs","mogoDb","javascript","jquery","reactJs"],
status: "active"
})
