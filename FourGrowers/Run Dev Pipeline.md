[[reference]]
Activate `nix` by going to `harvestingbot/analytics` the running `nix develop`. From there, go to `ingest/infra/dev` then run: `terragrunt apply -var='snowflake_user=rporter'`