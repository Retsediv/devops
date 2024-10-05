FROM alpine:3.14 AS builder

RUN apk add --no-cache build-base

WORKDIR /app

COPY <<EOF ./main.c
#include <stdio.h>

int main() {
    printf("Hello, world!\n");
    return 0;
}
EOF

RUN gcc -o hello main.c


# Runtime env
FROM alpine:3.14

WORKDIR /app
COPY --from=builder /app/hello .

# CMD ["./hello"]
# CMD ["echo", "Hello, world!"]
ENTRYPOINT ["./hello"]
