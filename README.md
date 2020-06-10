# AncDB
The AncGIS database

The repository contains 5 directories:
- **admin**: Contains configuration files for AdminMongo (more information [here](./admin/README.md)),
- **data**: Contains examples of generated data files,
- **generation**: Contains scripts to check and generate data files from raw data,
- **rawdata**: Directory where to put your raw data,
- **shell**: Contains a shell script helping to populate de database with the generated data files.

## Normal processing

The rawdata and the data are not stored into the code repository.
You have to get the rawdata from the various providers.
Put the rawdata into the rawdata directory and launch the generation of the data.

**Important note:** The following commands work only in the context of the [vm4ancgis](https://github.com/sgalopin/vm4ancgis) virtual machine.

### Step 1 - Get the raw data from the providers
- Taxons raw data:
> Go the [contact page](https://apinutriculture.org/contact/) of apinutriculture.org and ask a dump of the database.

- On the host:
 - Add your raw data into the "rawdata" directory,
 - Set the parameters into the "config.json" file

### Step 2 - Check your raw data

You can decide to edit you own database for any reason. In that case, you can check your data with the provided scripts and schemas.

- On the guest:
 - Check the parameters into the "config.json" file,
 - Launch the check (Example with the taxons):    
 ```
cd /var/www/ancdb/generation/taxons
node check-taxons.js
```

### Step 3 - Generation of the data

- On the guest:
 - Check the parameters into the "config.json" file,
 - Launch the generation:    
 ```
cd /var/www/ancdb
npm run start
```

### Step 4 - Filling the database

- On the guest:
 - Check the parameters into the "populate-db.sh" file,
 - Launch the filling:    
 ```
cd /var/www/ancdb/shell
/bin/bash populate-db.sh
```
