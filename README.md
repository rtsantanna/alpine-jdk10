# alpine-jdk10

Dockerfile for OpenJDK 10.0.1 on Alpine Linux 3.7. Alpine uses musl libc, so the image installs glibc to run the official OpenJDK build.

> **Deprecated.** Java 10 reached end of life in September 2018. For new projects use a maintained image such as [`eclipse-temurin`](https://hub.docker.com/_/eclipse-temurin), which has Alpine variants.
>
> The prebuilt image `rtsantanna/alpine-jdk10` is no longer published on Docker Hub (removed in September 2026). Build it from this Dockerfile if you still need it.

## What the Dockerfile does

1. Installs glibc 2.25 ([sgerrand/alpine-pkg-glibc](https://github.com/sgerrand/alpine-pkg-glibc)) and copies `libgcc`, `libstdc++` and `zlib` into `/usr/glibc-compat`.
2. Downloads OpenJDK 10.0.1 from java.net, checks its SHA-256 and extracts it to `/opt/jdk-10.0.1`.
3. Sets `JAVA_HOME=/opt/jdk-10.0.1` and adds it to `PATH`.

## Build

```bash
docker build -t alpine-jdk10 .
docker run --rm alpine-jdk10 java -version
```

The build downloads `gcc-libs` and `zlib` from the current Arch Linux packages, so it may no longer build unchanged today.

By Sant'Anna, Ricardo
