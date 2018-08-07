# sqltco
This repository captures a procedure to measure SQL Azure TCO using Azure PowerShell to capture:
Azure Log Analytics
Azure Usage Aggregates
and Azure Rate Card

Using this data one can determine the TCO of Azure SQL while conducting stress testing.

When comparing Azure SQL costs to SQL Server there is a dendancy to compare licensing costs to DTU (or vCores) but that is a misleading comparinson.  Instead one should consider the Azure SQL TCO:
DTU includes SQL Server licensing costs and:
a. Hardware license
b. Virtualisation software license
c. OS licesnse
d. Storage
d. Backup
e. High availablity
and optionally Azure SQL would also include:
f. Extracting data out of Azure
g. Reporting database copy
h. Snapshot database copy
i. Remote reporting database copy
j. Remote disaster recovery database
k. Long term database backup storage

When one creates an Azure SQL one gets the features a-e out of the box.  All these are part of a DTU.
One can configure the optional features and those would incure an additional costs but it might not always be reflected in the DTUs allocated to a specific SQL Server and one would need to use additional APIs in Azure in order to ascertain these: Usage Aggregate and Rate Card APIs.  These costs could also span more than one region.

When one is migrating from SQL Server one can run the DTU tool to gather traces from the server that can be used to determine the amount of DTUs needed in the cloud.  Based on the usage one can determine which Azure SQL edition (standard or premium is needed) and based on the DTUs the cost can be determined.

When one is migrating from a none SQL Server platform one does not have a way to estimate DTUs.  One could make an educated guess from some platforms considering the cores and storage of the originating platform as a guide to make a good estimates for cores and storage needed in Azure and then proceed to use the vCores model to get a sizing estimate.  Normally one would then conduct a performance test on the Azure platform to ensure estimates are validated and then typically would choose to have headroom to assume growth.  

Producing a TCO estimate for a large estate of servers is not easy.  It could reveal highly lucrative offer than could be realized when migrating to the Azure SQL.
