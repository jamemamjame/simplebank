1. Create postgres instance
```
docker run --name postgres12 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=secret -p 5432:5432 -d postgres:12-alpine

OR

make postgres
```
2. Create database
```
docker exec -it postgres12 createdb --username=root --owner=root simple_bank

OR

make createdb
```
2. Install `migrate` command ([click](https://github.com/golang-migrate/migrate/tree/master/cmd/migrate)). We're going to create schema and table
2. Create migration file under `db/migration` directory
```
migrate create -ext sql -dir db/migration -seq init_schema
```
2. Create schema to specifc database
```
make migrateup
```

2. Write SQL into the generated file
2. This project use `sqlc` to deal with database querying
```
brew install sqlc
```
2. Create sqlc setting file, then copy simple config from https://github.com/kyleconroy/sqlc/tree/v1.4.0 to paste
```
sqlc init
```
2. Initiate `go.mod`` file
```
go mod init github.com/techschool/simplebank
```
2. Install dependencies
```
go mod tidy
```
2. Generate mock database for testing
```
make mock
```

Remark
- In Golang, we write test file in the same folder with the code
- Unittest function must start with "Test" prefix (uppercase "T")