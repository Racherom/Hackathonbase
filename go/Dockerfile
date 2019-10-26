FROM golang:alpine as build-stage

RUN apk update && apk add --no-cache git

WORKDIR /app

COPY app .

RUN go get -d -v

RUN go build

EXPOSE 8080

FROM scratch as productive
# Copy our static executable.
COPY --from=build-stage /app/app /app/app
# Run the hello binary.
CMD ["/app/app"]