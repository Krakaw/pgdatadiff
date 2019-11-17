# PGDataDiff

[![asciicast](https://asciinema.org/a/281974.svg)](https://asciinema.org/a/281974)

## Introduction

This is a small utility that given 2 postgres databases, will tell you what tables have different data. Specificaly is was developed to test replication is working correctly between 2 postgres databases.

Specifically is compares tables data and sequences.

### How does it determine if table data is different?

Firstly it compares the row count in both tables.

If the row count is the same, it gets postgres to create MD5 sums of "chunks" of the table. This way no data is actually read directly by `pgdatadiff`, it also means that `pgdatadiff` is relatively fast but is puts the databases a moderate amount of pressure as it calculates the MD5 sums of large amounts of data.

If you have tables have many columns, perhaps consider using a smaller `--chunk-size`, the default is 10000. Conversely if your tables have a small amount of columns with 100000's of rows, perhaps increase this value.

## Installation

The latest version can be installed using `pip install pgdatadiff`. Python 3.6+ is required.

## Usage

Check `pgdatadiff --help`

## Docker Images

Docker images are available.

`docker run -it davidjmarkey/pgdatadiff:0.1.0 /usr/bin/pgdatadiff`


