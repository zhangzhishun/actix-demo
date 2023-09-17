# Actix Web Demo(PostgreSQL)

## Dependencies

- Rust
- Cargo
- Actix Web
- Diesel
- PostgreSQL

## API

- GET /tweets - List all tweets.
    ```bash
    curl http://localhost:8080/tweets
    ```
- POST /tweets - Create a new tweet.
    ```bash
    curl -d '{"message": "I tweet from curl"}' -H "Content-type: application/json" -X POST http://localhost:8080/tweets
    ```
- GET /tweets/:id - Get tweet detail by ID.
    ```bash
    curl http://localhost:8080/tweets/1
    ```
- DELETE /tweets/:id - Delete a tweet with a given id.
    ```bash
    curl -d '{"message": "I tweet from curl (updated)"}' -H "Content-type: application/json" -X PUT http://localhost:8080/tweets/1
    ```
- PUT /tweets/:id - Edit a tweet.
    ```bash
    curl -X DELETE http://localhost:8080/tweets/2
    ```

## Usage

### Set Config

```bash
mv .env.example .env
```

### Install diesel_cli

```bash
cargo install diesel_cli --no-default-features --features postgres
```

### Create migration SQL

```bash
diesel migration generate {TABLE_NAME}
```
You will see the output of two entry files inside `migrations/**` folder.

then edit `up.sql`(replace with your table struct):

```sql
CREATE TABLE tweets
(
    id         SERIAL       NOT NULL PRIMARY KEY,
    message    VARCHAR(140) NOT NULL,
    created_at TIMESTAMP    NOT NULL
)
```
and then run:

```bash
diesel migration run
```

It generated a new file into `src/schema.rs` and then update `down.sql` with the following code(replace with your table name):

```sql
DROP TABLE tweets;
```

We can now roll back our migration correctly by redoing:

```bash
diesel generate redo
```

[More details](https://0xchai.io/blog/restful-api-with-actix#setup-diesel)

## Reference

- [Learn Rust by building a RESTFul API with Actix](https://0xchai.io/blog/restful-api-with-actix)