---
slug: set-up-lab-environment
id: ml6mlby9riet
type: challenge
title: Spin up Geek's Movie Shop
teaser: Set up your lab environment by spinning up Geek's Movie Shop on multiple hosts
notes:
- type: text
  contents: As an IT engineer for Geek's Movie Shop, it is your responsibility to
    make sure that all the Geek's Movie Shop services are running smoothly. To ensure
    that, it is crucial for you to be in light with how your infrastructure is behaving
    so you can identify and mitigate issues as needed.
tabs:
- title: host 1
  type: terminal
  hostname: host-1
- title: host 2
  type: terminal
  hostname: host-2
- title: host 3
  type: terminal
  hostname: host-3
difficulty: basic
timelimit: 1800
---

Geek's Movie Shop is a web application that consists of several interconnected microservices:
- user
- login
- cart
- catalogue
- payment
- ratings
- shipping
These services are instrumented with New Relic to monitor their performance and are deployed across a distributed infrastructure. Your goal is to observe the infrastructure to make sure all the related services are running smoothly.

Before you begin using New Relic infrastructure to observe and monitor your infrastructure, you need to spin up these services.

## Set up your environment

You application consists of multiple services, all of which are instrumented with New Relic. These services are spun over multiple hosts and use your liscense key to write telemetry data to New Relic. Before you spin up your application, you need to set your `NEW_RELIC_LICENSE_KEY` environment variable on all the hosts.

Export your `NEW_RELIC_LICENSE_KEY` environment variable on **host 1**.

```bash
export NEW_RELIC_LICENSE_KEY=<YOUR_LICENSE_KEY>
```
Replace <YOUR_LICENSE_KEY> with your real [license key](https://docs.newrelic.com/docs/apis/intro-apis/new-relic-api-keys/#ingest-license-key).

Next, move over to tab **host 2** and export your `NEW_RELIC_LICENSE_KEY` environment variable.

```bash
export NEW_RELIC_LICENSE_KEY=<YOUR_LICENSE_KEY>
```

Now you're ready to run your application.

## Spin up your application

On **host 1**, navigate to the root directory of application, build and run your services.

```bash
cd /home/packer/infra-lab-material/host-1
docker-compose build -q
docker-compose up -d
```

The services take sometime to build. Meanwhile, move to **host 2** tab and run your services.

```bash
cd /home/packer/infra-lab-material/host-2
docker-compose build -q
docker-compose up -d
```

Once your services are running, you see the similar output.

```bash
Creating network "host-1_geek-shop" with the default driver
Pulling redis (redis:4.0.6)...
4.0.6: Pulling from library/redis
c4bb02b17bb4: Already exists
58638acf67c5: Pull complete
f98d108cc38b: Pull complete
83be14fccb07: Pull complete
5d5f41793421: Pull complete
ed89ff0d9eb2: Pull complete
Digest: sha256:0e773022cd6572a5153e5013afced0f7191652d3cdf9b1c6785eb13f6b2974b1
Status: Downloaded newer image for redis:4.0.6
Creating host-1_mysql_1     ... done
Creating host-1_rabbitmq_1  ... done
Creating host-1_redis_1     ... done
Creating host-1_mongodb_1   ... done
Creating host-1_catalogue_1 ... done
Creating host-1_user_1      ... done
Creating host-1_cart_1      ... done
Creating host-1_payment_1   ... done
Creating host-1_shipping_1  ... done
Creating host-1_web_1       ... done
```

Besides these services, you also need to spin up a loader service that send mock traffic to your site.

Move to **host 3** tab, build and run your loader service.

```bash
cd /home/packer/infra-lab-material/host-3
docker-compose build -q
docker-compose up -d
```

With your application and loader service now running, you're ready to start instrument your infrastructure.