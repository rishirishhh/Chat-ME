postgresinit:
	docker run --name go-chat -p 5433:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=password -d postgres:latest

postgres:
	docker exec -it go-chat psql

createdb:
	docker exec -it go-chat createdb --username=root --owner=root go-chat-db

dropdb:
	docker exec -it go-chat dropdb go-chat-db

migrateup:
	migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat-db?sslmode=disable" -verbose up

migratedown:
	migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat-db?sslmode=disable" -verbose down

.PHONY: postgresinit postgres createdb dropdb migrateup migratedown