FROM rustlang/rust:nightly
COPY cowsay /usr/src/myapp/
WORKDIR /usr/src/myapp

RUN cargo build --release
CMD [ "./target/release/cowsay", "\"Hello World\"" ]
