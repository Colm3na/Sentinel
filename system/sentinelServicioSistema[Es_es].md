# Aquí se describen los pasos para poner sentinel como un servicio de sistema

1. Entramos en:

`cd /etc/systemd/system/`

2. Creamos un archivo llamado `sentinel.service`:

`sudo vim sentinel.service` 

3. En el escribimos _(recuerda cambiar **USER** por tu usuario)_:

```
[Unit]
Description=Sentinel Node
After=network.target

[Service]
Type=simple
User=USER
WorkingDirectory=/home/USER
ExecStart=/home/USER/go/bin/sentinel-hubd start
Restart=on-failure
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
```

>_Paramos el nodo si lo tenemos en funcionamiento antes de seguir_

4. Creamos los enlaces simbólicos:

`sudo systemctl enable sentinel.service`

5. Iniciamos el servicio:

`sudo systemctl start sentinel.service` 

6. Creamos un script para comprobar los logs _(podemos crearlo en el `home` y cambiar el nombre por el que más nos guste)_:

`vim checkSentinel`

7. En el escribimos:

```
#!/bin/bash
#
#
sudo journalctl -f -u sentinel.service
```

8. Damos permisos de ejecución:

`chmod +x checkSentinel` 

9. Para ver los logs lo ejecutamos con:

`./checkSentinel`