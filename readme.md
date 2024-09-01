# Unified

A simplified `docker-compose` setup that includes everything to stand up the Linuxserver packaged [Unifi Network Application](https://docs.linuxserver.io/images/docker-unifi-network-application/). It includes the required mongodb instance and networks into the application container.

This repo offers nothing substantially different than the main linuxserver container other than letting you set two passwords and starting the stack, releasing it because I was annoyed.

## Usage

1. Generate two random strings to use as database passwords (ideally in linux)

    ```bash
    tr -dc A-Za-z0-9 </dev/urandom | head -c 25; echo
    ```

1. Replace those `REPLACE_ME` in the [.env](./.env) with what you just generated

    ```env
    MONGO_ROOT_PASS=yournewsupersecretpassword
    MONGO_PASS=yourothernewsupersecretpassword
    ```

1. Start the containers:

    ```sh
    docker-compose up -d
    ```
