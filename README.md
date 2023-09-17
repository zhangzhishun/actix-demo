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

[More details](https://0xchai.io/blog/restful-api-with-actix#setup-diesel)

## Documents

- [Learn Rust by building a RESTFul API with Actix](https://0xchai.io/blog/restful-api-with-actix)