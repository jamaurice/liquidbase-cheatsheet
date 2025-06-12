# Liquibase Commands Cheatsheet

This cheatsheet provides a quick reference for common Liquibase commands, their descriptions, and usage examples. Liquibase is a database schema migration tool that supports various database types.

## Table of Contents
- [Core Commands](#core-commands)
- [Database Management Commands](#database-management-commands)
- [Change Log Management Commands](#change-log-management-commands)
- [Miscellaneous Commands](#miscellaneous-commands)
- [Configuration](#configuration)
- [Notes](#notes)

## Core Commands

| Command | Description | Example |
|---------|-------------|---------|
| `update` | Applies pending changes to the database | `liquibase update --changelog-file=changelog.xml` |
| `rollback` | Reverts changes up to a specified tag or count | `liquibase rollback --tag=1.0` |
| `rollback-count` | Rolls back a specified number of changesets | `liquibase rollback-count --count=2` |
| `rollback-to-date` | Rolls back changes to a specific date/time | `liquibase rollback-to-date --date=2023-01-01` |
| `update-count` | Applies a specified number of changesets | `liquibase update-count --count=5` |
| `update-to-tag` | Applies changes up to a specific tag | `liquibase update-to-tag --tag=1.1` |

## Database Management Commands

| Command | Description | Example |
|---------|-------------|---------|
| `diff` | Compares two databases and reports differences | `liquibase diff --reference-url=jdbc:postgresql://localhost/refdb --url=jdbc:postgresql://localhost/targetdb` |
| `diff-changelog` | Generates a changelog based on database differences | `liquibase diff-changelog --reference-url=jdbc:postgresql://localhost/refdb` |
| `snapshot` | Captures the current database schema | `liquibase snapshot --output-file=snapshot.json` |
| `generate-changelog` | Creates a changelog from an existing database | `liquibase generate-changelog --changelog-file=generated.xml` |
| `drop-all` | Drops all database objects (use with caution) | `liquibase drop-all` |

## Change Log Management Commands

| Command | Description | Example |
|---------|-------------|---------|
| `status` | Reports pending changesets | `liquibase status --verbose` |
| `history` | Lists applied changesets | `liquibase history` |
| `validate` | Checks changelog for errors | `liquibase validate --changelog-file=changelog.xml` |
| `clear-checksums` | Clears all checksums to re-run changesets | `liquibase clear-checksums` |
| `calculate-checksum` | Calculates checksum for a specific changeset | `liquibase calculate-checksum --changeset-id=123` |

## Miscellaneous Commands

| Command | Description | Example |
|---------|-------------|---------|
| `tag` | Tags the current database state | `liquibase tag --tag=release-1.0` |
| `db-doc` | Generates database documentation | `liquibase db-doc --output-directory=docs` |
| `future-rollback-sql` | Generates SQL for rolling back future changes | `liquibase future-rollback-sql --output-file=rollback.sql` |
| `update-sql` | Generates SQL for pending changes without applying | `liquibase update-sql --output-file=update.sql` |

## Configuration

- **Common Parameters**:
  - `--changelog-file`: Specifies the changelog file (e.g., `changelog.xml`, `changelog.yaml`).
  - `--url`: Database connection URL (e.g., `jdbc:postgresql://localhost:5432/mydb`).
  - `--username`: Database username.
  - `--password`: Database password.
  - `--driver`: JDBC driver class (e.g., `org.postgresql.Driver`).

- **Configuration File**:
  Liquibase properties can be stored in `liquibase.properties`:
  ```properties
  changelog.file=changelog.xml
  url=jdbc:postgresql://localhost:5432/mydb
  username=admin
  password=secret
  driver=org.postgresql.Driver
