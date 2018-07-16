## Docker DNS server

Since version 2 Docker runs a small DNS server on it's containers and it allows containers to see each other. For example, your docker can see the other services if you ping the service name. The followings are mounted on the container services:
```
/etc/resolve.conf
/etc/hosts
```
the resolve.conf file containers the new special DNS ip.It is because of this that they can see each other.by using the following command, you can run multuple containers:
```
docker-compose scale <servicename>=4
```

This will create 4 instances of your app. if you run `nsloop <service name>` you can now see all 4 new on your server.

> To use NGINX as a load balancing reverse proxy in front of your docker services. You wll need to find your DNS ip and add it to your resolver. and then set a variable to your service in your NGINX config and pass it to your proxy for an instance change. 

To scale up your container use:
```
docker-compose scale app=5
```

