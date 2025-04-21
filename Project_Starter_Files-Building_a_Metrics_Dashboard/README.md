## Verify the monitoring installation

### All Pods in all Namespaces
![All Pods in all Namespaces](answer-img/deployment-all-pods.png "All Pods in all Namespaces")

### All Services in all Namespaces
![All Services in all Namespaces](answer-img/deployment-all-svc.png "All Services in all Namespaces")

## Setup the Jaeger and Prometheus source

Expose Grafana: 
`kubectl -n monitoring port-forward svc/prometheus-grafana --address 0.0.0.0 3000:80`
`Forwarding from 0.0.0.0:3000 -> 3000`

Add Prometheus as Datasource in Grafana:
`Grafana -> Connections -> Data Sources -> Add new Data Source -> Name: "Prometheus-Datasource" -> Connection - Prometheus Server URL: "http://prometheus-kube-prometheus-prometheus.monitoring.svc.cluster.local:9090" -> Save & test`

### Screenshot of the homepage after Login to Grafana
![Grafana after login](answer-img/Grafana-Login.png)

## Create a Basic Dashboard

![Prometheus-Dashboard in Grafana](answer-img/Grafana-Dashboard-Prometheus.png)

## Describe SLO/SLI

SLO: "At least 99% of uptime per month", SLI: "Uptime was 99.57% in the last month"
SLO: "Maximum Request response time below 200ms per day", SLI: "Maximum request response time was 147ms yesterday"

## Creating SLI metrics.
1. The service will handle at least 1000 requests per hour without performance degradation.
2. The API will be available 99.9% of the time over the last 30 days
3. The /healthz endpoint will return a 20x status at least 99.95% of the time during business hours 
4. 95% of HTTP requests to /api/v1/* will complete within 300ms over the last 24h.
5. Less than 0.1% of requests will return 5xx status codes over the last 1 hour.


## Create a Dashboard to measure our SLIs
*TODO:* Create a dashboard to measure the uptime of the frontend and backend services We will also want to measure to measure 40x and 50x errors. Create a dashboard that show these values over a 24 hour period and take a screenshot.

## Tracing our Flask App
*TODO:*  We will create a Jaeger span to measure the processes on the backend. Once you fill in the span, provide a screenshot of it here. Also provide a (screenshot) sample Python file containing a trace and span code used to perform Jaeger traces on the backend service.

## Jaeger in Dashboards
*TODO:* Now that the trace is running, let's add the metric to our current Grafana dashboard. Once this is completed, provide a screenshot of it here.

## Report Error
*TODO:* Using the template below, write a trouble ticket for the developers, to explain the errors that you are seeing (400, 500, latency) and to let them know the file that is causing the issue also include a screenshot of the tracer span to demonstrate how we can user a tracer to locate errors easily.

TROUBLE TICKET

Name:

Date:

Subject:

Affected Area:

Severity:

Description:


## Creating SLIs and SLOs
*TODO:* We want to create an SLO guaranteeing that our application has a 99.95% uptime per month. Name four SLIs that you would use to measure the success of this SLO.

## Building KPIs for our plan
*TODO*: Now that we have our SLIs and SLOs, create a list of 2-3 KPIs to accurately measure these metrics as well as a description of why those KPIs were chosen. We will make a dashboard for this, but first write them down here.

## Final Dashboard
*TODO*: Create a Dashboard containing graphs that capture all the metrics of your KPIs and adequately representing your SLIs and SLOs. Include a screenshot of the dashboard here, and write a text description of what graphs are represented in the dashboard.  
