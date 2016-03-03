# Refinery: Planning the path to service

## Milestones

### Minimal

A minimal refinery service on AWS. Users can create accounts,
and can upload data (and metadata).

### Presentable

The service is configured to automatically appear at a
particular domain, and has TLS (HTTPS).

### Restorable

Backups are automatically configured and are bioinformatician
proof.

### Encrypted

All data is encrypted at rest.

### Hardened

Defence-in-depth through internal security partitions and
minimising access to resources.


## Requirements

Each milestone corresponds to meeting a list of requirements.

For *minimal*:

- `account` Users can create accounts and use them
- `upload` Can upload data
- `durable` Data is durable
- `install` Installation into an AWS account is clear and possible

For *presentable*:

- `domain` Can be configured to appear at a particular domain
name
- `tls` user browsing and uploads are protected using HTTPS
(TLS)

For *restorable*:

- `backup` backups of all data are made in a documented and
controlled manner
- `restore` documented and tested procedure exists for restoring
from backups


For *encrypted*

- `encrypted` all data are encrypted at rest (using AWS KMS)

For *hardened*

- `sg` Refinery platform resources can be isolated from other
resources using AWS security groups.
- `firewall` Refinery platform resources are isolated from each
other.


Other Milestones

- `saml` integregates with existing SAML servers
- `cloudman` integrates with cloudman
- `s3` Bulk data is stored on AWS S3, allowing near infinite
space and durability.


## Analysis

Meeting the *upload* requirement requires various bug fixes.

## Current Status

2016-03-03

AWS CloudFormation can be used to start a refinery instance in
an AWS account. This has been done by more than 1 person in more
than 1 AWS account. (meets *install* requirement).

Storage is separated. Both disk files and structured database
files are stored on separate (EBS and RDS) resources so that the
refinery instance can be destory and recreated without affecting
the data (meets *durable* requirement).

Email is working via SES. User accounts can be created (necessary
to meet *accounts* requirement, but see the URL snag below).

There are some snags (not all internal services start correctly,
upload seems to be broken).

Server is deployed with insecure user passwords.

Not all of the AWS resources are correctly tagged.

URL in registration emails is wrong.


## Planned Components

While most of the components below have time estimates, I would
regard these as tentative at best.

Create / use non-default refinery password
    2.5 days

Fix URL in emails
    2.5 days

Tag root volume
    1 day

Backups

AWS VPC

AWS Security groups

front-end / load balancer.

TLS

Encryption-at-rest

S3

Galaxy
