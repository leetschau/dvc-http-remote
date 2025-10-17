# Rint Data Sharing Platform

## Setup Server

1. Create data folder
    ```sh
    mkdir data
    sudo chown -R 101:101 ./data
    ```

1. Create User file
    ```sh
    sudo pacman -S apache
    htpasswd -c htpasswd alice  # alice123
    htpasswd htpasswd bob  # bob123
    htpasswd htpasswd cindy  # cindy123
    ```

1. Start server: `docker compose up`.

To check server function, run the following command on client host:
```sh
echo -e "abc\nxyz" > test.txt
curl -v -u cindy:cindy123 -T test.txt http://localhost:8080/test.txt
```

Then on server:
```sh
cat data/test.txt
abc  # you should see the uploaded file
xyz
```
