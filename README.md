# NWAKU(install)

This is about how to set up waku
#ofiical doc
#


## clone

bash
gitclone https://github.com/waku-org/nwaku-compose
cd nwaku-compose
```

## set up

Docker Compose [reads the .env file](https://docs.docker.com/compose/environment-variables/set-environment-variables/#additional-information-3) from the filesystem. You can use `.env.example` as a template to provide the configuration values. The recommended process for working with `.env` files is to duplicate `.env.example`, rename it as `.env`, and then make the necessary value edits.

```bash
cp .env.example .env
nano .env
```

## register RLN membership[](https://docs.waku.org/guides/nwaku/run-docker-compose#register-for-rln-membership)

The RLN membership is your access key to The Waku Network. Its registration is done on-chain, allowing your `nwaku` node to send messages decentralised and privately, respecting some rate limits. Other peers won't relay messages that exceed the rate limit.

This command registers your membership and saves it in the `keystore/keystore.json` file. You should have Docker running at this step:

```bash
./register_rln.sh
```

check success

https://www.oklink.com/zh-hant/sepolia-test/address

## Run the node[](https://docs.waku.org/guides/nwaku/run-docker-compose#run-the-node)

Launch all the processes: `nwaku` node, database for storing messages, and Grafana for metrics with the following command. Your RLN membership is loaded into `nwaku` under the hood:

```bash
docker-compose up -d
```

View the logs of the node to confirm that it is running correctly:

```bash


docker-compose logs -f nwaku
```

## monitor

Visit http://localhost:3000/d/yns_4vFVk/nwaku-monitoring to view your node metrics in real time.

