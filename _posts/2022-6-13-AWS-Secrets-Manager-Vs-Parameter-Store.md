---
layout: post
title: AWS Secrets Manager Vs. Parameter Store
published: true
---
While studying for the AWS Sys-Ops exam, I became pretty confused about the difference between Secrets Manager and Systems Manager Parameter Store. They both seem to do the same thing: store secrets for your AWS account. I needed to delve deeper into the differences in order to understand the best use case scenario questions on the exam. After a more detailed examination, I found quite a few differences between the two and formlated some general rules for which to use them. Follow me if you would like to better understand these AWS services.

### In general:
Systems Manager (Parameter Store)
- Securely store secrets and parameters
- Wider use cases
- Appliction configuration variables
- License keys
- Custom settings

Secrets Manager works similarly with added functions:
- Provides cross-account access
- Automatic password rotation
- Password generator
- Database credentials
- API keys
- Allows multiple versions to be saved (Systems Manager allows for 1 previous version)
**Secrets Manager is encrypted by default, it is built for storing sensitive passwords securely**

#### What are the differences?
### Cost:
Secrets Manager costs MORE, \$.40 per secret per month with API interactions costing \$.05 per 10,000 API calls.

Parameter Store is free unless there is high throughput, and then it costs .05 per advanced parameter per month and API interactions cost .05 per 10,000 API calls.

### Secrets Rotation:
Secrets Manager offers key rotation itegrated with services such as RDS, Redshift, and DocumentDB.

Parameter Store requires you write your own function if you wish to update secrets managed by parameter store, and then invoke it using CloudWatch or EventBridge.

### Cross-account Access:
Secrets Manager secrets are available from multiple AWS accounts. Thus they may be centrally managed for an org that has multiple accounts.

Parameter Store: this feature is not supported.

### Secrets Size:
Secrets Manager secrets can be larger, up to 10KB in size.

Parameter Store: 4KB for standard parameter items and 8KB for advanced.

### Multi-Region Access:
Secrets Manager secrets can be spread accross regions to provide wide availablity and redundency.

Parameter Store does not provide this accessibility without again, writing you own custom function in Lambda, for example.

### Which one should I use?
In summary,
If you want/need to save money, use Parameter Store.
If you need to have compliance with password rotation, Secrets Manager makes that easy to do.

Bottom line, it is safer to store sensitive items  in either service, than to hard-code them into your app, or load them into a config file. Because of cost, it is prudent to store things like db credentials, API keys, and OAuth tokens in Secrets Manager and less important items, like application settings or environmental config data in Parameter Store.


