The practice with Spring Boot + Prometheus

# I. Running application:

## 1. Start your application
You can start either `pro01-simple-metrics` or `pro02-metrics-with-aspectj`
Those applications have code for measuring running time, the request counts...
So we can try to trigger some requests to those application by open URL in browser
``` 
localhost:8080/sample-api
``` 
Refresh it several times so that the requests count will be increased.
Those metrics numbers will be expose to the URL:
```
localhost:9091/actuator/prometheus
``` 

## 2. Start Prometheus GUI
```
cd ./prometheus-gui
bash start.sh
```

So our `prometheus-gui` will collect metrics numbers from our applications (e.g. `pro02-metrics-with-aspectj`) via URL `localhost:9091/actuator/prometheus` 
and store those data in its database. It was configured in `prometheus-gui/premetheus.yml`

After that, you can open the UI on web browser with URL
```
localhost:9090/graph 
```

Then you can explore it, good luck!

# II. Documents
To understand more about Prometheus, please read more at following links:

Starting guideline: https://prometheus.io/docs/prometheus/latest/getting_started/

TODO:
+ Counts per second/minute/hour: https://stackoverflow.com/questions/26038298/what-does-minute-rates-of-both-timer-and-meter-metrics-indicates, https://reflectoring.io/monitoring-error-rate-spring-boot/
+ Running time for the whole flow with async requests: https://www.nurkiewicz.com/2018/01/monitoring-and-measuring-reactive.html (by create (lazily) a new Context object)
+ How many 200-like and 500-like response occurred: https://touk.pl/blog/2018/03/05/spring-boot-2-0-http-request-metrics-with-micrometer/
+ Response time statistics: mean, median, percentiles
+ SLA (view slide [3] to understand the concept): https://spring.io/blog/2018/03/16/micrometer-spring-boot-2-s-new-application-metrics-collector

Additional references:
   1. Some good codes to use Metrics: https://www.nurkiewicz.com/2018/01/monitoring-and-measuring-reactive.html
   2. https://spring.io/blog/2018/03/16/micrometer-spring-boot-2-s-new-application-metrics-collector
   3. Slide with very good and short explanation about Metric Concepts (Histogram, SLA...): https://www.slideshare.net/makingx/spring-boot-actuator-20-micrometer 
My Personal Document (DRAFT): https://drive.google.com/open?id=16DUc5KDOgY9bEwXOLhkVrHtKykAfspkHkxGEz3AFKik
   4. Percentile: https://www.elastic.co/blog/averages-can-dangerous-use-percentile
