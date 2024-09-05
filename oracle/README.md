# Oracle Database 19c Enterprise Edition on ARM64

This Docker Compose file is for people unable to use the course's Vagrantfile because they have ARM CPUs. To be sure that you need this, run the following command:

```bash
uname -m
```

If the output is `armv64` or `aarch64`, then you are in the right place. If the output is `x86_64`, then walk away from this repository and use the course's Vagrantfile.

## Getting Started

**Prerequisites:** [Docker](https://www.docker.com/get-started) must be installed.

To get started, run the following command:

```bash
docker compose up -d
```

Access logs to see the installation progress:

```bash
docker logs oracledb -f --tail 100
```

Once installation complete, Oracle Enterprise Manager Database Express (EM Express) will be available at [https://localhost:5500/em]. Use the following credentials to log in:

```
Username: sys
Password: my-super-secret-password
```

**Note:** Replace `oracledb` with the name of the container you want to access or view logs for.

### Connecting to the Oracle Database

Once the container is up and running, you can access Oracle Database using any database client. Use the following connection details:

```
Hostname: localhost
Port: 1521
Service Name (SID): ORCLCDB
Username: sys
Password: my-super-secret-password
Role: AS SYSDBA
```

**Note:** Make sure to replace `my-super-secret-password` with the password you set in the `compose.yml` file.

### Custom configurations

You can customize the Oracle Database configuration by editing the `compose.yml` file. The following configurations are available:

- ORACLE_SID: This parameter changes the Oracle system identifier (SID) of the database. This parameter is optional and the default value is set to ORCLCDB.
- ORACLE_PDB: This parameter modifies the name of the pluggable database (PDB). This parameter is optional and the default value is set to ORCLPDB1.
- ORACLE_PWD: This parameter modifies the password for the SYS, SYSTEM and PDBADMIN users. This parameter is optional and the default value is randomly generated.
- INIT_SGA_SIZE: This parameter modifies the memory in MB that should be used for all SGA components. This parameter is optional, and the default value is calculated during database creation if it isn't provided.
- INIT_PGA_SIZE: This parameter modifies the target aggregate memory in MB that should be used for all server processes attached to the instance. This parameter is optional, and the default value is calculated during database creation if it isn't provided.
- ORACLE_EDITION: This parameter modifies the edition of the database when the container is started for the first time. This parameter is optional and the two values are enterprise or standard. The default value is enterprise.
- ORACLE_CHARACTERSET: This parameter modifies the character set of the database. This parameter is optional and the default value is set to AL32UTF8.
- ENABLE_ARCHIVELOG: This parameter enables the ARCHIVELOG mode while creating the database for the first time. Default value of this parameter is false.

### Stopping the containers

To stop the containers, run the following command:

```bash
docker compose down
```
