
For instructions setting up InfluxDB with Docker, see the [setup section below](#setting-up-influxdb).

---

## {% linkable_title Setting up InfluxDB %}

These instructions require you to have docker installed.

1. Create a persistent volume for influxdb to store its data:

    `docker volume create influxdb-data`

1. Run the following command to start the InfluxDB container:

    ```
    docker run -d \
    --name="influxdb" \
    --restart always \
    -p 8086:8086 \
    -v influxdb-data:/var/lib/influxdb \
    influxdb
    ```

3. After the container has started, run the influx client:

    `docker exec -it influxdb influx`

4. Create a new database for Home Assistant:
    
    ```
    CREATE DATABASE home_assistant
    exit
    ```

5. Add InfluxDB to Home Assistant by putting the influxdb section into your configuration.yaml
    
    ```
    influxdb:
        host: YOUR_DOCKERHOST_IP
    ```

    By default, all entities and their states will get sent to influxdb. It may be in your best interest to limit which devices are sent. You can do this by whitelisting entities or domains with `include` or blacklisting entities or domains with `exclude`. 
    
    For example, you may want to only have your sensors values sent to influxdb:

    ```
    influxdb:
        host: YOUR_DOCKERHOST_IP
        include:
            domains:
                - sensor
    ```

6. Restart Home Assistant to have it try and connect to InfluxDB. Once it has restarted, if there were any problems with it connecting, there will be an error notification on your Home Assistant page.
