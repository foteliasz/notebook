# Build and publish containers

1. Transfer Dockerfile.v1 to build machine.

    ```bash
    scp '.\dummies\Dockerfile.v1' [username]@[host]:/home/[username]
    ```

2. Build dummy container with first version of the application.

    ```bash
    docker build . \
        -t foteliasz/helm-dummy:1.0.0-arm64 \
        -f ./Dockerfile.v1
    ```

3. Publish the first version of application.

    ```bash
    docker push foteliasz/helm-dummy:1.0.0-arm64
    ```

4. Transfer Dockerfile.v2 to build machine.

    ```bash
    scp '.\dummies\Dockerfile.v2' [username]@[host]:/home/[username]
    ```

5. Build dummy container with second version of the application.

    ```bash
    docker build . \
        -t foteliasz/helm-dummy:2.0.0-arm64 \
        -f ./Dockerfile.v2
    ```

6. Publish the second version of application.

    ```bash
    docker push foteliasz/helm-dummy:2.0.0-arm64
    ```
