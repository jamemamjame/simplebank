1. Create postgres instance
```
docker run --name postgres12 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=secret -p 5432:5432 -d postgres:12-alpine
```
2. Create database
```
docker exec -it postgres12 createdb --username=root --owner=root simple_bank
```
2. Install `migrate` command. We're going to create schema and table
2. Create migration file
```
migrate create -ext sql -dir db/migration -seq init_schema
```
2. Write SQL into the generated file
2. This project use `sqlc` to deal with database querying
```
brew install sqlc
```
2. GO mod init
```
go mod init github.com/techschool/simplebank
```
2. Install dependencies
```
go mod tidy
```