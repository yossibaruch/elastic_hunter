# elastic_hunter.py
Quickly do IOC searches on data indexed by Elasticsearch ( I use md5 / filename as an example because I'm lazy -- yes I know these are brittle. ) 

## 1. IOCs you wish to search must be in CSV format -- row data does not need to be related, the column is what matters
```bash
# example:
"md5","file_name"
"C35906060A4B79FCB9564248C472741E","evil_file1.exe"
"41202F5DBD630BA5E29A3B0DAD1FE9C1","evil_file2.exe"
"90F0BC619BEF2A3BEFEACA0B2F0407DB","evil_file3.exe"
...
"2B9CC45773D7E15C2855239B15A7DA35","really_evil.exe"
```

## 2. Your index fields must match the name of the CSV headers
## 3. Usage:

```bash
Usage: elastic_hunter.py [options]

Options:
  -h, --help            show this help message and exit
  -c CSV_FILE, --csv=CSV_FILE containing IOC info (required)
  -i INDEX_NAME, --index=INDEX_NAME you want to search against (required)
  -s SERVER, --server=SERVER running elasticsearch (defaults to localhost)
  -p PORT, --port=PORT elasticsearch is running on (defaults to 9200)
```


## 3. Example:

```bash
$ ./elastic_hunter.py -c ../20_thousand_iocs.csv -i "all_files_metadata"
[+] Got 13 hits where 'file_name' = 'jscript9.exe'
[+] Got 1 hits where 'md5' = '3CC983011177A815A94218EB38E13241'
```
