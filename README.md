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
