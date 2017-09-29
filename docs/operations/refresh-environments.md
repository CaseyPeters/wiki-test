# Refresh Local Dev Environment with Data from a deployed environment <a name="refresh-local-dev"></a>

_TL;DR:_

Using Node version `4.2.2`...

    node utilities/scripts/export-data.js <environment> -o campspot_production.sql --parks 14 26 && utilities/scripts/import_production.sh

## Export Data from Production

`node utilities/scripts/export-data.js <environment> -o campspot_production.sql --parks 14 26`
Will load data from only parks 14 and 26 and will exclude audits

`node utilities/scripts/export-data.js <environment> -o campspot_production.sql --parks 14 26 --audits`
Will do the same, but include audits

## Import Data Locally

Copy the file that was created by the export to the root folder of the Campspot project and rename it `campspot_production.sql`.

In the campspot project directory, execute the following command to run the import script:
`utilities/scripts/import_production.sh`.

Note: Running this script requires that you have mysql installed on your command line.

Execute the following command in your campspot project directory to update your access control logic:
`npm run acls`
     

# Refresh Staging (or a Dev Server) with Production Data via `copy_data`

There is no network path between staging and production, so this process cannot be run directly from an AWS server. In order to refresh staging run the following command locally: 

    utilities/scripts/copy_data.sh <from-environment> <to-environment>

Note that this doesn't run migrations. To run migrations, ssh into `campspot-staging-integration` (log directly into dev servers since they do not have integration servers. E.g., `ssh campspot-development-5`) and run:

    cd /var/node/campspot && node_modules/.bin/db-migrate -e <environment> up


# Refresh Staging (or a Dev Server) with Production Data via SCP and `import-data`

Staging or a dev server can be refreshed manually by copying a dump of production to the target server, and then running the `import-data` script. 

1.  [Pull a fresh dump of prod.](#refresh-local-dev) It can be handy to `-o` this to a specific name like, `campspot_production_20170214.sql`.
2. Copy the sql file to somewhere on the target server. 

```
scp campspot_production_20170214.sql campspot-development-5:/home/ec2-user
```

3. SSH into the target server, change to the project directory and run:

```
NODE_ENV=development-5 node utilities/scripts/import-data.js --noTunnel -d development-5 -i /home/ec2-user/campspot_production_02132017.sql
```
# Refresh Dev Servers with Staging Data #

1. SSH into the target development server `ssh campspot-development-#`
2. CD to the root directory `cd /var/node/campspot`
3. Copy data from staging to development server `utilities/scripts/copy_data.sh --no-tunnel staging development-#`

# Export Single Table Data from Production to Local

For example, to export the data from the FinancialAccountMapping table in production, to a local file named `financial_account_mapping_20170416T0329.sql` run the following:

```
node utilities/scripts/export-data.js production -o financial_account_mapping_20170416T0329.sql --table FinancialAccountMapping --noCreateInfo
```

To import it locally once the download is complete:

```
utilities/scripts/import_mysql_data.sh financial_account_mapping_20170416T0329.sql
```

Note you may need to truncate, or delete conflicting data in your local database in order to import successfully.

# Troubleshooting #

Syncing data between environments can take 30 minutes +. Sometimes, the connection between your computer and the remote server can break during that time and you may see an error message related to Broken Pipe. To avoid this and ensure that the entire process runs whether or not your connection is broken, you can use screen terminal command. 
1. SSH into the environment you will be syncing data into 
1. In the terminal, type in ```screen  -S <someName>``` This will clear your current terminal screen and create a new session with someName as the session name. 
1. Now you can run your commands per above
1. Once your command has started, detach the screen by running Ctrl + a (release) and then d to detach the screen

** Type ```man screen``` into a terminal to bring up documentation