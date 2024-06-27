Since it's an unofficial upgrade, the path to the web image in `./templates/docker-compose.v3.yml` is changed to the repo that contains the Domain's API logic.

To create a custom Docker image, run the following command locally in the Postal directory:

```sh
docker build . -t REPO_NAME:TAG
```

For example:

```sh
docker build . -t postal:3.3.4-with-domains-api
```

Then push the image to a registry:

```sh
docker image push postal:3.3.4-with-domains-api
```

You can push to Docker Hub or GitHub Registry after logging in. Note that this requires an organization or a paid plan (more details [here](https://docs.github.com/en/get-started/learning-about-github/githubs-plans)). The image size is currently around 1.7GB.

There are two options to run the `postal upgrade` command to update Postal (read more [here](https://docs.postalserver.io/getting-started/upgrading)):

1. Set the git remote URL to the repo with the updated image path and pull the changes:

   ```sh
   git remote set-url origin REPO_URL
   git pull origin
   ```

2. Directly change the path to the web service image in `./templates/docker-compose.v3.yml` on the server and then run `postal upgrade`:

   ```sh
   postal upgrade
   ```