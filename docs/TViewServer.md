# TViewServer

Web Server displaying SAM/BAM file. A web interface for jvarkit:tview


## Usage

```
Usage: tviewserver [options] Files
  Options:
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -m, --max
      Max interval Length
      Default: 2000
    -nojs, --no-javascript
      Disable Javascript (which is not filesystem-safe).
      Default: false
    -P, --port, -port
      Server listening port
      Default: 8080
    -R, --reference
      Indexed fasta Reference file. This file must be indexed with samtools 
      faidx and with picard CreateSequenceDictionary
    --version
      print version and exit

```


## Keywords

 * sam
 * bam
 * table
 * visualization
 * server
 * web


## Compilation

### Requirements / Dependencies

* java compiler SDK 1.8 http://www.oracle.com/technetwork/java/index.html (**NOT the old java 1.7 or 1.6**) and avoid OpenJdk, use the java from Oracle. Please check that this java is in the `${PATH}`. Setting JAVA_HOME is not enough : (e.g: https://github.com/lindenb/jvarkit/issues/23 )
* GNU Make >= 3.81
* curl/wget
* git
* xsltproc http://xmlsoft.org/XSLT/xsltproc2.html (tested with "libxml 20706, libxslt 10126 and libexslt 815")


### Download and Compile

```bash
$ git clone "https://github.com/lindenb/jvarkit.git"
$ cd jvarkit
$ make tviewserver
```

The *.jar libraries are not included in the main jar file, so you shouldn't move them (https://github.com/lindenb/jvarkit/issues/15#issuecomment-140099011 ).
The required libraries will be downloaded and installed in the `dist` directory.

### edit 'local.mk' (optional)

The a file **local.mk** can be created edited to override/add some definitions.

For example it can be used to set the HTTP proxy:

```
http.proxy.host=your.host.com
http.proxy.port=124567
```
## Source code 

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/tview/TViewServer.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/tview/TViewServer.java)


<details>
<summary>Git History</summary>

```
Tue Oct 31 17:21:38 2017 +0100 ; tviewserver / vcfserver : added screenshots ; https://github.com/lindenb/jvarkit/commit/2a991b2e352fb30b8e0a94144fcda8d52c2f653a
Tue Oct 31 17:03:31 2017 +0100 ; tviewserver based on jvarkit:tview ; https://github.com/lindenb/jvarkit/commit/7799aa3b2dae490541a0ae017fd86b6819dd4aba
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **tviewserver** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


## Input

Input is a set of indexed BAM files  or a file containing the path to the BAMs.

## Screenshot

https://twitter.com/yokofakun/status/925395272225746944

![twitter](https://pbs.twimg.com/media/DNepyjOW4AA-_rz.jpg "Screenshot")


## Example 

```
$ java -jar dist/tviewserver.jar -R src/test/resources/toy.fa src/test/resources/toy.bam
2017-10-31 16:31:15.281:INFO::main: Logging initialized @1262ms
[INFO][TViewServer]Starting com.github.lindenb.jvarkit.tools.tview.TViewServer on http://localhost:8080
2017-10-31 16:31:15.523:INFO:oejs.Server:main: jetty-9.3.7.v20160115
2017-10-31 16:31:15.690:INFO:oejs.ServerConnector:main: Started ServerConnector@14a2189{HTTP/1.1,[http/1.1]}{0.0.0.0:8080}
2017-10-31 16:31:15.691:INFO:oejs.Server:main: Started @1675ms

```



