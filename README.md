# Githooks dockerfile
Builds an image that enable automatic githook installation on every machine when running docker-compose up

## How to use
Builds the image and tag it:
```bash
cd githooks
docker build . -t githooks:latest
```

Now, in the project that needs git hooks to be installed, add a service to your `docker-compose.yml` file
```yaml
services:
  web: ...

  # Here
  githooks:
    image: githooks:latest
    volumes: 
      - ./.git:/tmp/.git
      - ./.githooks:/tmp/.githooks
```

Finally, add a `.githooks` to the root of project, and create whatever hook you need, e.g: `pre-push`
