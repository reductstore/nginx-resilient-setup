# nginx-resilient-setup

An example of a resilient ReducStore setup with NGINX.

Read more here: https://www.reduct.store/docs/next/guides/disaster-recovery#active-active-setup


## Running the example

```
docker compose up -d
# Ingress endpoint to write data
reduct-cli alias add ingress -L http://localhost:80/ingress --token secret
# Egress endpoint to query data
reduct-cli alias add egress -L http://localhost:80/egress --token secret


# Write dataset from Demo Server
reduct-cli alias add play -L https://play.reduct.store --token reductstore
# Write data to ingress
reduct-cli cp play/datasets ingress/bucket-1 --limit 1000
# Export data from egress
reduct-cli cp egress/bucket-1 ./export_folder --limit 1000
```
