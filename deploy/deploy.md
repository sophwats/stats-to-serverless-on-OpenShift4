# Deployment Instructions

This document needs to contain all information on how to deploy the lab.

## RHPDS link
This link *must* be given here.

## Instructions to deploy on RHPDS

Edit the following section in `deploy.sh` and set the proper values:


    export RHPDS_USER_COUNT=${RHPDS_USER_COUNT:-1}
    export RHPDS_USER=<RHPDS bastion user>
    export RHPDS_DOMAIN=example.opentlc.com
    export RHPDS_GUID=<RHPDS GUID>
    export RHPDS_PASSWORD=<RHPDS bastion password>

Launch the deployment:

    ./deploy.sh

## Instructions to deploy outside of RHPDS
These should be given as a single command.
