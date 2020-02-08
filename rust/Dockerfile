FROM rustlang/rust:nightly as build
COPY cowsay /usr/src/myapp/
WORKDIR /usr/src/myapp

RUN cargo build --release

FROM scratch
COPY --from=build /usr/src/myapp/target/release/cowsay /cowsay
CMD [ "/cowsay", "\"Hello World\"" ]
