libs3
============

新浪云存储 - libs3

### Requirements

* libcurl
* libcurl-devel
* libxml2                                                              
* libxml2-devel 

> For CentOS, you will need to run `yum install libcurl* libxml2*`.

### Installation / Usage

1. Linux: 使用`make`编译, 在buile下生成: 动态链接库(libs3.so)、静态链接库(libs3.a)、可执行命令行工具(s3)
2. OSX: 使用XCode编译:osx/s3.xcodeproj, 生成: 静态链接库(libs3.a)、可执行命令行工具(s3-cli)
3. Windows: 使用MingW进行编译


### 调用示例 & 命令行工具使用

1. 调用示例: 源码: src/s3.c
2. 命令使用:
```
$ ./s3

Options:

   Command Line:

   -f/--force           : force operation despite warnings
   -h/--vhost-style     : use virtual-host-style URIs (default is path-style)
   -u/--unencrypted     : unencrypted (use HTTP instead of HTTPS)
   -s/--show-properties : show response properties on stdout
   -r/--retries         : retry retryable failures this number of times
                          (default is 5)

   Environment:

   S3_ACCESS_KEY_ID     : S3 access key ID (required)
   S3_SECRET_ACCESS_KEY : S3 secret access key (required)
   S3_HOSTNAME          : specify alternative S3 host (optional)

 Commands (with <required parameters> and [optional parameters]) :

   (NOTE: all command parameters take a value and are specified using the
          pattern parameter=value)

   help                 : Prints this help text

   list                 : Lists owned buckets
     [allDetails]       : Show full details

   test                 : Tests a bucket for existence and accessibility
     <bucket>           : Bucket to test

   create               : Create a new bucket
     <bucket>           : Bucket to create
     [cannedAcl]        : Canned ACL for the bucket (see Canned ACLs)
     [location]         : Location for bucket (for example, EU)

   delete               : Delete a bucket or key
     <bucket>[/<key>]   : Bucket or bucket/key to delete

   list                 : List bucket contents
     <bucket>           : Bucket to list
     [prefix]           : Prefix for results set
     [marker]           : Where in results set to start listing
     [delimiter]        : Delimiter for rolling up results set
     [maxkeys]          : Maximum number of keys to return in results set
     [allDetails]       : Show full details for each key

   put                  : Puts an object
     <bucket>/<key>     : Bucket/key to put object to
     [filename]         : Filename to read source data from (default is stdin)
     [contentLength]    : How many bytes of source data to put (required if
                          source file is stdin)
     [cacheControl]     : Cache-Control HTTP header string to associate with
                          object
     [contentType]      : Content-Type HTTP header string to associate with
                          object
     [md5]              : MD5 for validating source data
     [contentDispositionFilename] : Content-Disposition filename string to
                          associate with object
     [contentEncoding]  : Content-Encoding HTTP header string to associate
                          with object
     [expires]          : Expiration date to associate with object
     [cannedAcl]        : Canned ACL for the object (see Canned ACLs)
     [x-amz-meta-...]]  : Metadata headers to associate with the object

   copy                 : Copies an object; if any options are set, the entire
                          metadata of the object is replaced
     <sourcebucket>/<sourcekey> : Source bucket/key
     <destbucket>/<destkey> : Destination bucket/key
     [cacheControl]     : Cache-Control HTTP header string to associate with
                          object
     [contentType]      : Content-Type HTTP header string to associate with
                          object
     [contentDispositionFilename] : Content-Disposition filename string to
                          associate with object
     [contentEncoding]  : Content-Encoding HTTP header string to associate
                          with object
     [expires]          : Expiration date to associate with object
     [cannedAcl]        : Canned ACL for the object (see Canned ACLs)
     [x-amz-meta-...]]  : Metadata headers to associate with the object

   get                  : Gets an object
     <buckey>/<key>     : Bucket/key of object to get
     [filename]         : Filename to write object data to (required if -s
                          command line parameter was used)
     [ifModifiedSince]  : Only return the object if it has been modified since
                          this date
     [ifNotmodifiedSince] : Only return the object if it has not been modified
                          since this date
     [ifMatch]          : Only return the object if its ETag header matches
                          this string
     [ifNotMatch]       : Only return the object if its ETag header does not
                          match this string
     [startByte]        : First byte of byte range to return
     [byteCount]        : Number of bytes of byte range to return

   head                 : Gets only the headers of an object, implies -s
     <bucket>/<key>     : Bucket/key of object to get headers of

   gqs                  : Generates an authenticated query string
     <bucket>[/<key>]   : Bucket or bucket/key to generate query string for
     [expires]          : Expiration date for query string
     [resource]         : Sub-resource of key for query string, without a
                          leading '?', for example, "torrent"

 Canned ACLs:

  The following canned ACLs are supported:
    private (default), public-read, public-read-write, authenticated-read

```
