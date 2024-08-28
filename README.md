# greenlight

```bash
$ go run ./cmd/api
$ go run ./cmd/api >>/tmp/api.log

$ docker compose up -d
$ docker exec -it [container_name_or_id] psql -U [username]

# Add the following to your $HOME/.profile file:
# export GREENLIGHT_DB_DSN='postgres://[username]:[password]@localhost/greenlight'
$ source $HOME/.profile
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
