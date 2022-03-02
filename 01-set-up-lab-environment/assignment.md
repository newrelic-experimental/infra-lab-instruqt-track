---
slug: set-up-lab-environment
id: ml6mlby9riet
type: challenge
title: Spin up Geek's Movie Shop
teaser: Set up your lab environment
notes:
- type: text
  contents: As an IT engineer for Geek's Movie Shop, it's your responsibility to ensure
    that all your services are running smoothly. This means you need to observe your
    infrastructure to see how it's behaving and to identify and mitigate issues as
    they come up.
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

Geek's Movie Shop is a web application that consists of several, interconnected microservices. Before you begin to observe and monitor the infrastructure that supports these services, you need to set up your lab environment.

## Set up your environment

Geek's Movie Shop is a distributed application. It's composed of services hosted on multiple servers. Here, we provide you some quick setup commands so that you can spin up your lab environment. First, you configure your New Relic license key on each host, so that your instrumented applications know where to send telemetry data. Then, you use `docker-compose` to spin up pre-instrumented services that use your license key.

First, copy your [license key](https://docs.newrelic.com/docs/apis/intro-apis/new-relic-api-keys/#ingest-license-key). You use this multiple times throughout this challenge.

In the **host 1** tab, configure a new environment variable, called `NEW_RELIC_LICENSE_KEY`.

```bash
export NEW_RELIC_LICENSE_KEY=<YOUR_LICENSE_KEY>
```

> Replace <YOUR_LICENSE_KEY> with your real [license key](https://docs.newrelic.com/docs/apis/intro-apis/new-relic-api-keys/#ingest-license-key).

In the **host 2** tab, do the same.

```bash
export NEW_RELIC_LICENSE_KEY=<YOUR_LICENSE_KEY>
```

Now, you're ready to run your application.

## Spin up your application

In the **host 1** tab, build and run the Geek's Movie Shop services.

```bash
cd /home/packer/infra-lab-material/host-1
docker-compose build -q
docker-compose up -d
```

Expect this command to run for several minutes. While it does, do the same for **host 2**.

```bash
cd /home/packer/infra-lab-material/host-2
docker-compose build -q
docker-compose up -d
```

Once the services are running, the docker output shows that the containers were successfully created.

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

## Spin up your load generator

With your services running, spin up a load generator that sends traffic to your site.

In the **host 3** tab, build and run your load generator.

```bash
cd /home/packer/infra-lab-material/host-3
docker-compose build -q
docker-compose up -d
```

Docker output shows that the loader service is successfully created.

```bash
Creating network "host-3_default" with the default driver
Creating host-3_loader-2_1 ... done
Creating host-3_loader-1_1 ... done
```

Now that your application and load generator are running, you're ready to instrument your infrastructure.