
## Run the SQL Server container

```
docker run -d -p 1433:1433 -e sa_password=NDC_l0nd0n -e ACCEPT_EULA=Y --name product-launch-db --ip 172.20.244.163 microsoft/mssql-server-windows-express
```

## Run the NATS container

```
docker run -d -p 4222:4222 --name nats --ip 172.20.244.164 sixeyed/nats:nanoserver
```

##Query the db

```
docker exec docker_product-launch-db_1 powershell -Command "Invoke-SqlCmd -Query 'SELECT * FROM Prospects' -Database ProductLaunch"
```

## Get IP addresses

```
dip docker_product-launch-web_1
dip docker_kibana_1
```