# VcfRenameSamples

Rename the Samples in a VCF


## Usage

```
Usage: vcfrenamesamples [options] Files
  Options:
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -o, --output
      Output file. Optional . Default: stdout
    --outputbcf
      Output bcf (for streams)
      Default: false
    --vcfcreateindex
      VCF, create tribble or tabix Index when writing a VCF/BCF to a file.
      Default: false
    --vcfmd5
      VCF, create MD5 checksum when writing a VCF/BCF to a file.
      Default: false
    --version
      print version and exit
    -E
      error like src sample missing in VCF
      Default: false
  * -f
      Tab delimited file containing old-name\tnew-name

```


## Keywords

 * vcf
 * sample


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
$ make vcfrenamesamples
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/misc/VcfRenameSamples.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/misc/VcfRenameSamples.java)


<details>
<summary>Git History</summary>

```
Wed Jul 26 18:09:38 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/576fdd17812f9a47491945cb8bb74990ffb084c9
Tue Jun 6 18:06:17 2017 +0200 ; postponed vcf ; https://github.com/lindenb/jvarkit/commit/bcd52318caf3cd76ce8662485ffaacaabde97caf
Wed May 17 14:09:36 2017 +0200 ; fix typo bioalcidae ; https://github.com/lindenb/jvarkit/commit/9db2344e7ce840df02c5a7b4e2a91d6f1a5f2e8d
Thu May 11 16:20:27 2017 +0200 ; move to jcommander ; https://github.com/lindenb/jvarkit/commit/15b6fabdbdd7ce0d1e20ca51e1c1a9db8574a59e
Tue Apr 25 17:33:00 2017 +0200 ; fix make ; https://github.com/lindenb/jvarkit/commit/621fdfbe039f474e187e8f5c67ff17b368b77289
Fri Jun 5 12:42:21 2015 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/cc909f9f4ceea181bb65e4203e3fdbde176c6f2f
Tue Mar 17 16:59:10 2015 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/b74a74277f72f240dab3360a49fdb8357f7bfbbd
Mon May 12 14:06:30 2014 +0200 ; continue moving to htsjdk ; https://github.com/lindenb/jvarkit/commit/011f098b6402da9e204026ee33f3f89d5e0e0355
Mon May 12 10:28:28 2014 +0200 ; first sed on files ; https://github.com/lindenb/jvarkit/commit/79ae202e237f53b7edb94f4326fee79b2f71b8e8
Sun Feb 2 18:55:03 2014 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/abd24b56ec986dada1e5162be5bbd0dac0c2d57c
Thu Dec 12 23:40:23 2013 +0100 ; rename samples vcf ; https://github.com/lindenb/jvarkit/commit/dde9d975366700060e6436ed83c7399f00ebd0cd
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **vcfrenamesamples** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


```bash
$ curl -s "https://raw.github.com/arq5x/gemini/master/test/test1.snpeff.vcf" |\
grep -A 2 CHROM  | cut -f 1-5,10-

#CHROM	POS	ID	REF	ALT	1094PC0005	1094PC0009	1094PC0012	1094PC0013
chr1	30860	.	G	C	0/0:7,0:7:15.04:0,15,177	0/0:2,0:2:3.01:0,3,39	0/0:6,0:6:12.02:0,12,143	0/0:4,0:4:9.03:0,9,119
chr1	69270	.	A	G	./.	./.	1/1:0,3:3:9.03:106,9,0	1/1:0,6:6:18.05:203,18,0

curl -s "https://raw.github.com/arq5x/gemini/master/test/test1.snpeff.vcf" |\
java -jar dist/vcfrenamesamples.jar -f <(echo -e "1094PC0005\tALPHA\n1094PC0012\tBETA\nSAMPLE\tGAMMA\n1094PC0009\tEPSILON") -E  |\
grep -A 2 "#CHROM" | cut -f 1-5,10-

#CHROM	POS	ID	REF	ALT	ALPHA	EPSILON	BETA	1094PC0013
chr1	30860	.	G	C	0/0:7,0:7:15:0,15,177	0/0:2,0:2:3:0,3,39	0/0:6,0:6:12:0,12,143	0/0:4,0:4:9:0,9,119
chr1	69270	.	A	G	./.	./.	1/1:0,3:3:9:106,9,0	1/1:0,6:6:18:203,18,0
```


