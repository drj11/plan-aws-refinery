# Planning the path to service

A minimal refinery service on AWS. Users can create accounts,
and can upload data (and metadata). Currently aiming for
Wednesday 2016-03-02.

## Requirements

- `account` Users can create accounts and use them
- `upload` Can upload data
- `durable` Data is durable
- `install` Installation into an AWS account is clear and possible

Notably absent: Galaxy, cloud burst / scaling,
  scalable storage (S3).

## Analysis

The ability for users to create accounts requires that email be
working. Without this, it is possible that system administrators
would be able to create accounts by-hand (that option has not
been investigated).

Having durable data means separating the storage from the web
app server instances. This gives the storage and the web app servers
independent lifetimes, so that the web app servers can be
reconfigured, destroyed, and recreated without it affecting
users' data. Storage is a (PostgreSQL) relation database,
and flat files on disk. These will be moved to RDS and (separate)
EBS.

Making it possible to install on AWS is mostly a documentation,
but also a minimisation, task. AWS CloudFormation is used to automate
deployment to an AWS account.

## Current Status

2016-01-21

AWS CloudFormation can be used to start a refinery instance in
an AWS account.

Working on separating the RDS component (relational PostgreSQL
database).

Next: separating the RBS component (disk-based flat files).


## Planned Components

While most of the components below have time estimates, I would
regard these as tentative at best. However, the overall
timescale seems plausible. (about 27 working days).


Overall documentation
    2.5 days,
    1.5 days remaining

Connect to separate RDS
    5 days,
    1.5 days remaining

Connect to separate EBS
    2.5 days

AWS Resource Tags
    2.5 days

Document IAM Roles
    2.5 days

Create / use non-default refinery password
    2.5 days

Create use non-default RDS password
    2.5 days

Email working
    5 days

Document how to get email working
    2.5 days

Backups

AWS VPC

AWS Security groups

front-end / load balancer.
