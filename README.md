# Anonymise CKAN DB

A script to replace user information in the CKAN database with fake data.
The script will:

- Connect to the CKAN database in  a local PostgreSQL.
- Select all entries from the `user` table.
- Replace the each entry's `fullname` with a name generated by the [faker](https://github.com/joke2k/faker) tool.
- Repleace each entry's `name` and `email` with a values generated from the new `fullname`.
- Dump the modified and anomymised db to a file using `pg_dump`.
- Roll back the db to its initial state.

## Usage

```
% python anonymise_db.py --help    
usage: anonymise_db.py [-h] [--db DB] [--user USER] [--host HOST] [--port PORT] [--dumpfile DUMPFILE] --pw PW

Connect to a CKAN DB in Postgres and replace `fullname`, `name` and `email` in the `user` table with random names.

options:
  -h, --help           show this help message and exit
  --db DB              Name of the CKAN database in Postgres. Default: ckan
  --user USER          Username to access the database. Default: ckan
  --host HOST          Postgres database host. Default: localhost.
  --port PORT          Postgres database port. Default: 5432.
  --dumpfile DUMPFILE  Filename of the output dump. Default: anonymised.dump.

required named arguments:
  --pw PW              Password to access the database
```

## Requirements

- The script has been tested with Python 3.12.
- It uses `faker`, `python-slugify` and `psycopg2`.

## Installation



## License

All code in this repository is published under the [MIT License](License).
