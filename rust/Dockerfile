FROM rustlang/rust:nightly as build
COPY cowsay /usr/src/myapp/
WORKDIR /usr/src/myapp

RUN cargo build --release

# FROM alpine
# COPY --from=build 
CMD [ "/usr/src/myapp/target/release/cowsay", "\"Hello World\"" ]
