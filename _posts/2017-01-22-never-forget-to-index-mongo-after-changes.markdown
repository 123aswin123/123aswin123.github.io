---
layout: post
title: "Never forget to reIndex your MongoDB after a MongoImport"
date:   2017-01-22 22:15:00
---

We at [Deducely](http://deducely.com) provide APIs to track technologies that are used by companies across the globe. Recently we wanted to rename some MongoDB keys (as in Key value pair JSON keys) that were being served by our API. To do that we tried used the [$rename](http://docs.mongodb.com/manual/reference/operator/update/rename) command. Since our DBs are enormous with millions of documents with hundreds of key value pairs, the `$rename` command took forever to run and crashed in between.

To workaround this problem, a friend suggested us to `mongoexport` all the documents and use `sed` to rename the keys. Lastly we had to `mongoimport` the documents with the corrected keys.

Viola, this method worked like a charm. I connected the DB with our API code and tested by retrieving a few frequently checked domains like 'youtube.com', 'hotmail.com', 'amazon.com' etc... and our API worked like a charm.

Then I hit some less popular domains, but got no response from the API. Scrutinizing the logs revealed that the mongo connection had timed out. [Recent attacks on live MongoDB instances](https://nakedsecurity.sophos.com/2017/01/11/thousands-of-mongodb-databases-compromised-and-held-to-ransom/) have been prevalent and I was paranoid that our DBs might have also been attacked, but the security steps that we had taken had thwarted all the attack attempts and our database was safe.

Still the problem prevailed, I was unable to update records as the code threw a timeout error. In frustration I tried every MongoDB trick I was aware of. I tried restarting the VMs, stopping and starting the process, resyncing the mongoDB replica set, repairing the DB with the `mongod --repair` command. None of these resulted in fruition.

I tried connecting to the DB via robomongo and running a few queries, the shell became unresponsive and the app crashed! Finally I SSHed into the VM where the DB was running and brought up a mongo shell.

Inside the mongo shell , when google.com was queried a successful result came at once. When google2123123213.com (an invalid domain not in the DB) was queried it ran forever and after 15 minutes null was returned. This helped in identifying the issue plaguing the system.

The queries took forever to run and resulted in a timeout because we did not create the required DB index after the `mongoimport`.

As a rule of thumb, try to use `mongodump` and `mongorestore` wherever possible as this would ensure that everything is dumped and restored perfectly. If you are left with no other choice than doing a `mongoimport` **NERVER EVER EVER FORGET TO INDEX THE REQUIRED FIELDS**. This would save us loads of time.

The best feeling that a developer can get is the satisfaction of finally finding the bug and squashing it permanently after endless hours of frustrating wild goose chases!
