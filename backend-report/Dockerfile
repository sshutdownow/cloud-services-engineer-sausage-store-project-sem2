# Start from the latest golang base image
FROM golang:latest as builder

# Set the Current Working Directory inside the container
WORKDIR /app

# Copy go mod and sum files
COPY go.mod go.sum ./

# Download all dependencies. Dependencies will be cached if the go.mod and go.sum files are not changed
RUN go mod download

# Copy the source from the current directory to the Working Directory inside the container
COPY . .

# Build the Go app
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .


######## Start a new stage from scratch #######
FROM alpine:latest  

WORKDIR /app

# Copy the Pre-built binary file from the previous stage
COPY --chmod=0555 --from=builder /app/main .

# Expose port 8080 to the outside world
EXPOSE 8080

# https://docs.docker.com/reference/dockerfile/#user
USER 1001:1001

# Command to run the executable
CMD ["/app/main"]
