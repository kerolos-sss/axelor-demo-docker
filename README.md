# axelor-demo-docker

## Just put the demo in axelor container 

[https://github.com/axelor/axelor-docker](https://github.com/axelor/axelor-docker)

## To run[:]

Make sure to adjust the .env file from the sample.env template
run

```bash
docker-compose up --build
```

Use
[http://localhost:18000](http://localhost:18000)

users

- admin/admin
- demo/demo

If you want to clear the containers and persistance volumes

```bash
docker-compose down -v
```

- -v for removing persistent volumes
