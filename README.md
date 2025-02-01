# Rust single thread web app
A very simple rust web app that processes requests one at a time


## Language
```
Rust
```

## Views
### Home
```
GET 127.0.0.1:7878/
```

### Invalid resource
```
GET 127.0.0.1:7878/invalid_resource
```

### Run
```
Cargo run
```

### Simulate one thread
Uncomment the code bellow with `match` and comment on `if/else` block. When the `/sleep` new resource is requested, other requests will have to wait.
#### Uncomment
```rust
    let (status_line, filename) = match &request_line[..] {
        "GET / HTTP/1.1" => ("HTTP/1.1 200 OK", "hello.html"),
        "GET /sleep HTTP/1.1" => {
            thread::sleep(Duration::from_secs(5));
            ("HTTP/1.1 200 OK", "hello.html")
        },
        _ => ("HTTP/1.1 404 NOT FOUND", "404.html")
    };
```
#### comment
```rust
    let (status_line, filename) = if request_line == "GET / HTTP/1.1"{

        // print!("Request {http_request:#?}");
        // let response = "HTTP/1.1 200 OK\r\n\r\n";
        // let status_line = "HTTP/1.1 200 OK";
        // let contents = fs::read_to_string("hello.html").unwrap();
        // let length = contents.len();

        // let response = format!("{status_line}\r\nContent-Length: {length}\r\n\r\n{contents}");

        // stream.write_all(response.as_bytes()).unwrap();
        ("HTTP/1.1 200 OK", "hello.html")
    }
    else {
        // some code
        // let status_line = "HTTP/1.1 404 NOT FOUND";
        // let contents = fs::read_to_string("404.html").unwrap();
        // let length = contents.len();

        // let response = format!("{status_line}\r\nContent-Length: {length}\r\n\r\n{contents}");
        // stream.write_all(response.as_bytes()).unwrap();
        ("HTTP/1.1 404 NOT FOUND", "404.html")
    }
```


