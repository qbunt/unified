# Unified

A simplified `docker-compose` setup that includes everything to stand up the Linuxserver packaged [Unifi Network Application](https://docs.linuxserver.io/images/docker-unifi-network-application/). It includes the required mongodb instance and networks into the application container.

This repo offers nothing substantially different than the main linuxserver container other than letting you set two passwords and starting the stack, releasing it because I was annoyed.

This uses:

- mongo v7 (it is pinned, mongo releases do not migrate automatically)
- latest of the [Linuxserver Unifi network application](https://docs.linuxserver.io/images/docker-unifi-network-application/)

> [!IMPORTANT]  
> If you're migrating from the older, deprecated version of the [Unifi controller](https://github.com/linuxserver/docker-unifi-controller) published by Linuxserver, [follow these instructions](https://docs.linuxserver.io/images/docker-unifi-network-application/#migration-from-unifi-controller) to export _both the settings and history_ before you proceed. You'll need to start these containers first and restore from backup.

## Usage

1. Clone this repo

    ```bash
    git clone git@github.com:qbunt/unified.git && cd unified
    ```

1. Generate two random strings to use as database passwords (ideally in linux)

    ```bash
    tr -dc A-Za-z0-9 </dev/urandom | head -c 25; echo
    ```

1. Replace those `REPLACE_ME` strings in the [.env](./.env) with what you just generated

    ```env
    MONGO_ROOT_PASS=yournewsupersecretpassword
    MONGO_PASS=yourothernewsupersecretpassword
    ```

3. Start the containers:

    ```sh
    docker-compose up -d
    ```

## License

[MIT](./license)
