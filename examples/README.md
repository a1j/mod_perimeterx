#Sample Site

#### Configure: 

1. Replace ```perimeterx.conf``` configuration placeholders with real values from your `PerimeterX` account.
2. Replace `$APP_ID` placeholder inside `index.html` to your PerimeterX application Id.

***All information needed can be found in PerimeterX [console](https://console.perimeterx.com/).***

#### Build:

```bash 
$ docker build -t $NAME .
```

#### Run

```bash
$ docker run --rm -p $PORT:80 $NAME 
```

From within the container you should 

```bash
root@305dd6f490bb:/# apachectl start
```

To follow the logs:

```bash
root@305dd6f490bb:/tmp# tail -f /var/log/apache2/error.log
```

Now you can access `localhost:$PORT` from your local machine and debug.
