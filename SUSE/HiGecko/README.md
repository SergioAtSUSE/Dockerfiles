# Dockerfile

With this Dockerfile you can create a docker image to run the app https://github.com/SUSE/HiGecko.



# Docker images

The generated images can be found here: https://hub.docker.com/r/slindomansilla/suse_higecko/



# Run a container



## Default execution

```
docker-run -p 3000:3000 --name suse_higecko slindomansilla/suse_higecko
```

By default the container shows the output of the command `rails s -b 0.0.0.0`.

The app should be available at http://localhost:3000

You can stop the execution by pressing _Ctrl+C_



## Test your changes to the app

If you need to test your changes to the app before making a pull request, you can mount your local copy of the git project into the container by running the container with this command.

```
docker-run -p 3000:3000 -v /host/path/to/HiGecko/:/tmp/HiGecko --name suse_higecko slindomansilla/suse_higecko
```
