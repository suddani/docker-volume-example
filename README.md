# docker-volume-example
Utilizing the volume flag in a dockerfile to provide a default config that can be changed in later runs

Works also without the volume flag which can be checked with app2.


## Test

Check that initial data is there that came with the container
```
docker-compose run --rm app cat /data/config.cfg
```

Modify data

```
docker-compose run --rm app sh -c 'printf "service: \"other\"\nport: 8888" > /data/config.cfg'
```


Check that new data is there
```
docker-compose run --rm app cat /data/config.cfg
```

Between every run the container itself is destroyed because we are using ```--rm```

## Destroy

Remove all containers
```
docker-compose down
```

Remove all containers and volumes
```
docker-compose down -v
```