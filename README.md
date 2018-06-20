# keepasscsv2dir
transform a KeepassX or KeepassXC csv file into a directory of secrets


# Usage

* In Keepass, update a password entry to include `filename=path/to/secret/file` in the `Notes`
  field.
* In Keepass, export as CSV with the "`Export to CSV file`"
* Run `./keepasscsv2dir` to take the secrets and put them into files:

```
$ ./keepasscsv2dir --output-directory ~/testsecrets --keepass-csv-file secrets.csv
> /Users/username/testsecrets
  Importing "development jira"                       development.jira.secret                 
	 Creating secret subdirectory /Users/username/testsecrets
  Importing "development aws access key"             integration.aws.access_key.secret       
  Importing "test aws access key"                    test.aws.access_key.secret              
  Importing "development aws secret key"             development.aws.secret_key.secret       
  Importing "test aws secret key"                    test.aws.secret_key.secret              
  Importing "legacy environment1"                    legacy/environment1                     
	 Creating secret subdirectory /Users/username/testsecrets/legacy
```

```
$ tree -L 2 ~/testsecrets/
/Users/username/testsecrets/
├── development.aws.secret_key.secret
├── development.jira.secret
├── integration.aws.access_key.secret
├── legacy
│   └── environment1
├── test.aws.access_key.secret
└── test.aws.secret_key.secret

1 directory, 6 files
```

