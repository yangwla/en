# Binlog File Download
You can download the Binlog files of JCS for  MySQL/Percona/MariaDB instance service from the addresses of the intranet and internet provided by JD Cloud.

## Precautions
* The addresses of the intranet and internet have a valid period. If the expiration date is exceeded, the addresses will be invalid. Users can click the download button to generate the download pop-up box to get the new downloading address.

## Binlog Download 
1. Login [RDS Console](https://rds-console.jdcloud.com/database).
2. Select the instance where the Binlog file download is required, click the name of the target instance, and enter the instance detailed page.
3. Select the tag of ***Backup Management***, click the tag of ***Binlog*** to enter the list page, select the Binlog files to be downloaded, and click ***Download*** in the column of ***Operation***.
4. Parameters of Binlog Download Pop-up Box
    * Intranet Address: The domain name shall be provided to access the intranet, such as the access instance, can accessed from a VM on the same VPC or subnet as the database instance, for the downloading of Binlog files.
    * Internet Address: The domain name of public network shall be provided and users can download Binlog files through the internet. The download speed is limited by the network bandwidth of the public network. Therefore, if the public network bandwidth is too small and the backup file is too large, the download time will be comparatively long.
    * Click ***Local Download*** to download Binlog files directly from the browser.
    * Click ***Cancel*** to cancel the download of Binlog files.

    ![backup](../../../../../image/RDS/1109_8.jpg)

## Binlog Decompression
> JD Cloud has compressed Binlog files, so you need to decompress the files after downloading them to the local and then parse Binlog files with standard tools

1. Download the backup decompression tool [Click Download](http://jddb-common-public.oss.cn-north-1.jcloudcs.com/general_mysql_backup_extract_tool.zip) and decompress with the tool name of mysql_backup_extract.py, the use example is shown as below

```
 # View Help Manual
 ./mysql_backup_extract.py -h
 
 # Binlog File to Decompress Instances
 ./mysql_backup_extract.py  -f [name of binlog file to be decompressed] 
```
