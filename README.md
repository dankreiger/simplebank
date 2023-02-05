# README

- [README](#readme)
  - [Prerequisites](#prerequisites)
  - [Tools](#tools)
  - [Targets in the Makefile](#targets-in-the-makefile)
  - [Usage](#usage)
  - [Note on Makefile](#note-on-makefile)
  - [Go type generation](#go-type-generation)
  - [Structure](#structure)

This Makefile provides scripts for running and managing a PostgreSQL database using Docker.

## Prerequisites

- Docker must be installed on your system. Please follow the instructions on the Docker website to install it.

## Tools

In addition to the Makefile, the following tools can be used to manage and visualize your PostgreSQL database:

- [dbdiagram.io](https://dbdiagram.io/): A visual database design tool that allows you to create and modify ER diagrams for your database. It supports multiple databases including PostgreSQL.

- [TablePlus](https://tableplus.com/): A modern, native, and friendly GUI tool for relational databases. It supports PostgreSQL and provides features such as a SQL editor, data viewer, and an intuitive UI for managing your database.

- [go-migrate](https://github.com/golang-migrate/migrate): A database migration tool written in Go. It supports multiple databases including PostgreSQL.

- [sqlc](sqlc.dev): A tool for generating type-safe Go from SQL. It supports PostgreSQL and provides features such as a SQL editor, data viewer, and an intuitive UI for managing your database.

## Targets in the Makefile

This Makefile contains the following targets for running and managing the Simple Bank application:

- `postgres`: Runs a PostgreSQL container named `postgres15-1` with the following options:

  - Port mapping `5432:5432`
  - Environment variable `POSTGRES_USER` set to `root`
  - Environment variable `POSTGRES_PASSWORD` set to `secret`
  - Using the image `postgres:15.1-alpine`

- `createdb`: Creates a database named `simple_bank` using `docker exec`.

- `dropdb`: Drops the database `simple_bank` using `docker exec`.

- `migrateup`: Runs the `migrate` tool to apply database migrations. The connection URL points to the `simple_bank` database on localhost with the specified credentials.

- `migratedown`: Runs the `migrate` tool to undo database migrations. The connection URL points to the `simple_bank` database on localhost with the specified credentials.

- `sqlc`: Runs the `sqlc` tool to generate Go code from SQL.

- `test`: Runs Go tests for the application.

The `.PHONY` target specifies that the above targets are not associated with files, so they will always run when invoked.

## Usage

To run any of the targets in the Makefile, use the following command in the terminal:

```sh
make <target>
```

## Note on Makefile

Please make sure Docker is running before executing the make targets.

## Go type generation

The `sqlc` tool can be used to generate Go types from SQL queries. The `sqlc` tool is installed in the `tools` directory. To generate the Go types, run the following command:

```sh
make sqlc
```

## Structure

![simple_bank](./simple_bank.png)
