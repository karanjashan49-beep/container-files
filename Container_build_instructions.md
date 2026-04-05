# Container Build Instructions

This file explains a simple way to build a container image.

## 1. Create a Containerfile

A `Containerfile` (or `Dockerfile`) defines how the image is built.

Example:

```Dockerfile
FROM alpine:latest

RUN apk add --no-cache curl

CMD ["sh"]
```

## 2. Build the container image

Use one of the following commands from the directory containing the `Containerfile`.

### With Podman

```bash
podman build -t my-image:latest .
```

### With Docker

```bash
docker build -t my-image:latest .
```

## 3. Run the container

### With Podman

```bash
podman run --rm -it my-image:latest
```

### With Docker

```bash
docker run --rm -it my-image:latest
```

## 4. Notes

- `-t my-image:latest` gives your image a name and tag.
- `.` means build using the current directory as the build context.
- You can replace `my-image:latest` with any name you want.
- If you use Podman, the file can be named `Containerfile`.
- If you use Docker, `Dockerfile` is the common name.

## 5. Recommended project structure

```text
project-folder/
├── Containerfile
└── app-files
```

## 6. Example build workflow

```bash
cd project-folder
podman build -t demo-app:latest .
podman run --rm -it demo-app:latest
```

This is the basic process: write the container definition, build the image, then run it.
