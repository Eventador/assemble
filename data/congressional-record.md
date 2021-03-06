# Congressional Record
```
far-right/  
|--congressional-record-archive/
  |--1995to1997.json
  |--1997to2007.json
  |--2007to2016.json
```

List directory contents with AWS CLI
`aws s3 ls s3://far-right/congressional-record-archive/ --profile <credential_profile>` see [`aws configure`](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)

```
2017-02-03 21:30:33    0 Bytes
2017-02-03 21:43:04  608.0 MiB 1995to1997.json
2017-02-03 21:39:39    2.5 GiB 1997to2007.json
2017-02-03 21:33:23    2.1 GiB 2007to2016.json

Total Objects: 4
   Total Size: 5.1 GiB
```

Thanks to @john who donated the congressional [record archive](https://www.congress.gov/congressional-record) 1995-2016.

File contains lines of JSON objects with the below fields:

```
url
title
date
congress
session
issue
volume
start_page
end_page
text
```

We are adding the current record on a daily basis. Live data is dumped twice a day at `s3://far-right/info-source/daily/<DATE>/congress/`
Replace `<DATE>` with the date you want, formatted as YYYYMMDD

Example:
```
aws s3 ls s3://far-right/info-source/daily/20170212/congress/ --human-readable
2017-02-11 19:08:14    1.1 MiB congress_0007.json
2017-02-12 07:08:09    1.1 MiB congress_1207.json
```
