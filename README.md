# greenlight

```bash
$ go run ./cmd/api
$ go run ./cmd/api >>/tmp/api.log

$ docker compose up -d
$ docker exec -it [container_name_or_id] psql -U [username]

# Add the following to your $HOME/.profile file:
# export GREENLIGHT_DB_DSN='postgres://[username]:[password]@localhost/greenlight'
$ source $HOME/.profile

# Working with sql migrations
$ migrate create -seq -ext=.sql -dir=./migrations create_movies_table
$ migrate create -seq -ext=.sql -dir=./migrations add_movies_check_constraints
$ migrate -path=./migrations -database=$GREENLIGHT_DB_DSN up
# if the last command failed excute the following:
postgres=# ALTER DATABASE greenlight OWNER TO [username];
$ migrate -path=./migrations -database=$EXAMPLE_DSN version
$ migrate -path=./migrations -database=$EXAMPLE_DSN goto 1
$ migrate -path=./migrations -database =$EXAMPLE_DSN down 1
$ migrate -path=./migrations -database=$EXAMPLE_DSN down
$ migrate -path=./migrations -database=$EXAMPLE_DSN force 1
$ migrate -source="s3://<bucket>/<path>" -database=$EXAMPLE_DSN up
$ migrate -source="github://owner/repo/path#ref" -database=$EXAMPLE_DSN up
$ migrate -source="github://user:personal-access-token@owner/repo/path#ref" -database=$EXAMPLE_DSN up

# Sending a bunch of concurrent requests
$ xargs -I % -P8 curl -X PATCH -d '{"runtime": "97 mins"}' "localhost:4000/v1/movies/4" < <(printf '%s\n' {1..8})
# Getting the request time
$ curl -w '\nTime: %{time_total}s \n' localhost:4000/v1/movies/1
# Testing timeouts outside of PostgreSQL
$ go run ./cmd/api -db-max-open-conns=1
$ curl localhost:4000/v1/movies/1 & curl localhost:4000/v1/movies/1 &

# Sending shutdown signals
$ pgrep -l api
$ pkill -SIGTERM api
$ pkill -SIGKILL api
$ curl localhost:4000/v1/healthcheck & pkill -SIGTERM api
```

Let's Go Further

2. Getting Started

- Project Setup and Skeleton Structure
- A Basic HTTP Server
- API Endpoints and RESTful Routing

3. Sending JSON Responses

- Fixed-Format JSON
- JSON Encoding
- Encoding Structs
- Formatting and Enveloping Responses
- Advanced JSON Customization
- Sending Error Messages

4. Parsing JSON Requests

- JSON Decoding
- Managing Bad Requests
- Restricting Inputs
- Custom JSON Decoding
- Validating JSON Input

5. Database Setup and Configuration

- Setting up PostgreSQL
- Connecting to PostgreSQL
- Configuring the Database Connection Pool

6. SQL Migrations

- An Overview of SQL Migrations
- Working with SQL Migrations

7. CRUD Operations

- Setting up the Movie Model
- Creating a New Movie
- Fetching a Movie
- Updating a Movie
- Deleting a Movie

8. Advanced CRUD Operations

- Handling Partial Updates
- Optimistic Concurrency Control
- Managing SQL Query Timeouts

9. Filtering, Sorting, and Pagination

- Parsing Query String Parameters
- Validating Query String Parameters
- Listing Data
- Filtering Lists
- Full-Text Search
- Sorting Lists
- Paginating Lists
- Returning Pagination Metadata

10. Rate Limiting

- Global Rate Limiting
- IP-based Rate Limiting
- Configuring the Rate Limiters

11. Graceful Shutdown

- Sending Shutdown Signals
- Intercepting Shutdown Signals
- Executing the Shutdown
