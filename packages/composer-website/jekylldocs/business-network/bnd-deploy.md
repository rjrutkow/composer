---
layout: default
title: Task - Deploying and Updating Business Networks
category: tasks
sidebar: sidebars/businessnetworks.md
excerpt: How to deploy or update Business Networks
---

# Deploying and Updating Business Networks


Before a business network definition can be deployed it must be packaged into a _Business Network Archive_ (BNA) file. The `composer archive create` command is used to create a BNA file from a root folder on disk.

Once the BNA file has been created it can be deployed to a runtime using the `composer network deploy` command using a suitable [Connection Profile](../reference/connectionprofile.html)

For example:

        composer network deploy -p connectionProfileName -a <BusinessNetworkDefinition>.bna
           -i <Your EnrollmentID> -s <Your EnrollmentSecret>

To update the definition of an already deployed business network use the `composer network update` CLI command.

## Deploying business networks to {{site.data.conrefs.hlf_full}} Beta

In {{site.data.conrefs.hlf_full}} Beta peers now enforce the concepts of admins and members. Admin user's identities and crypto material must be available to the peer at deployment. To make that identity and its crypto material available, your must import it to your local `keyValStore` directory before deploying the business network. To import the identity, use the [`composer identity import` command](../reference/composer.identity.import.html). When importing an identity, you do not assign it a secret, however the `composer network deploy` command requires a secret. If you are using an imported identity, you can enter any value for the secret.

When connecting to the peer you must specify an identity where the userID contains the text `admin`, for example, `PeerAdmin`, `myadmin`, or `AdminPeer` are all valid userID's. Peers in different organizations may have different admin users. Only an admin user of peer's organization will be able to deploy a business network to their peers.

Due to many breaking API changes between Hyperledger Fabric alpha 1 and Hyperledger Fabric beta, {{site.data.conrefs.composer_full}} only supports the beta level and cannot support older versions of {{site.data.conrefs.hlf_full}} v1.0 (e.g. alpha 1).

### Deploying business networks using Playground locally

When deploying a business network to {{site.data.conrefs.hlf_full}} Beta using the Playground locally, you must follow the process above to connect using the peer admin identity. However, in order to create identities and interact with your business network in the Playground, you must use the certificate authority admin identity.

## References

* [**Composer CLI commands**](../reference/commands.html)
