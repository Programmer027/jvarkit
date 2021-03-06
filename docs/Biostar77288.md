# Biostar77288

Low resolution sequence alignment visualization


## Usage

```
Usage: biostar77288 [options] Files
  Options:
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -o, --out
      Output file. Optional . Default: stdout
    --version
      print version and exit
    -S
      Input is seqLogo
      Default: false
    -W
       Alignment width
      Default: 1000
    -r
      Use Rect
      Default: false

```


## Keywords

 * bam
 * sam
 * visualization
 * svg
 * alignment



## See also in Biostars

 * [https://www.biostars.org/p/77288](https://www.biostars.org/p/77288)


## Compilation

### Requirements / Dependencies

* java compiler SDK 1.8 http://www.oracle.com/technetwork/java/index.html (**NOT the old java 1.7 or 1.6**) . Please check that this java is in the `${PATH}`. Setting JAVA_HOME is not enough : (e.g: https://github.com/lindenb/jvarkit/issues/23 )
* GNU Make >= 3.81
* curl/wget
* git
* xsltproc http://xmlsoft.org/XSLT/xsltproc2.html (tested with "libxml 20706, libxslt 10126 and libexslt 815")


### Download and Compile

```bash
$ git clone "https://github.com/lindenb/jvarkit.git"
$ cd jvarkit
$ make biostar77288
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/biostar/Biostar77288.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/biostar/Biostar77288.java)


<details>
<summary>Git History</summary>

```
Sun May 21 17:11:09 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/aa4f02194fe00a1a842949e448661e227f16fe9f
Thu May 11 16:20:27 2017 +0200 ; move to jcommander ; https://github.com/lindenb/jvarkit/commit/15b6fabdbdd7ce0d1e20ca51e1c1a9db8574a59e
Thu May 4 13:06:07 2017 +0200 ; moving to jcommander ; https://github.com/lindenb/jvarkit/commit/b2f8f945cb8838c0289a7d850ce24603417eccde
Fri Apr 14 15:27:32 2017 +0200 ; annotation proc ; https://github.com/lindenb/jvarkit/commit/72b9383a8472e5a91120bab84d15b8acad4db8d4
Thu May 28 17:32:37 2015 +0200 ;  issue: https://github.com/lindenb/jvarkit/issues/28 ; https://github.com/lindenb/jvarkit/commit/4e10a0934f4a75b88c802583a8e19b1c228438fc
Mon May 12 14:06:30 2014 +0200 ; continue moving to htsjdk ; https://github.com/lindenb/jvarkit/commit/011f098b6402da9e204026ee33f3f89d5e0e0355
Mon May 12 10:28:28 2014 +0200 ; first sed on files ; https://github.com/lindenb/jvarkit/commit/79ae202e237f53b7edb94f4326fee79b2f71b8e8
Tue Jan 28 13:07:40 2014 +0100 ; bed rename chr ; https://github.com/lindenb/jvarkit/commit/3d1fbea5935084195d0b854089efcf571e42e0c6
Fri Oct 11 15:39:02 2013 +0200 ; picard v.100: deletion of VcfIterator :-( ; https://github.com/lindenb/jvarkit/commit/e88fab449b04aed40c2ff7f9d0cf8c8b6ab14a31
Wed Jul 24 14:44:13 2013 +0200 ; starting my code from http://plindenbaum.blogspot.com/2011/01/my-tool-to-annotate-vcf-files.html ; https://github.com/lindenb/jvarkit/commit/cbd77f6fc09edd992990112cbfc959b3b09574d5
Wed Jul 24 11:23:17 2013 +0200 ; biostar77288 ; https://github.com/lindenb/jvarkit/commit/df8f75815104512a868b6d29ff6436b503b92e38
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **biostar77288** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


## Example

```bash
curl -s "http://www.tcoffee.org/Courses/Exercises/saragosa_pb_2010/practicals/practical_2/ex.1.19/file/clustalw.msa" |\
	java -jar dist/biostar77288.jar  > result.svg
```
![ScreenShot](https://raw.github.com/lindenb/jvarkit/master/doc/biostar77288.png)

```bash
$ java -jar dist/sam4weblogo.jar IN=in.bam   REGION="1:630-719" |\
	java -jar dist/biostar77288.jar  SEQLOGO=true > result.svg
```


