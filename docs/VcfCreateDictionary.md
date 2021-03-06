# VcfCreateDictionary

Create a SAM Sequence Dictionary from a set of VCF files.


## Usage

```
Usage: vcfmakedict [options] Files
  Options:
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -o, --output
      Output file. Optional . Default: stdout
    --version
      print version and exit

```


## Keywords

 * vcf
 * dict
 * fai


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
$ make vcfmakedict
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/misc/VcfCreateDictionary.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/misc/VcfCreateDictionary.java)


<details>
<summary>Git History</summary>

```
Thu Sep 7 15:26:22 2017 +0200 ; adding unit test with testng ; https://github.com/lindenb/jvarkit/commit/980b8937646e706a83b10f6b1ceeb015f37bbcc1
Wed Sep 6 18:09:53 2017 +0200 ; moving to spring xml component ; https://github.com/lindenb/jvarkit/commit/2a697f0a6ac81ad0975fedd43ca2ff916f2920f0
Wed Sep 6 16:28:51 2017 +0200 ; create vcfmakedict, vcfsetdict moved to spring xml component ; https://github.com/lindenb/jvarkit/commit/88e83f863ba6ba49b7ca1e0a609ca61cc92fe14e
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **vcfmakedict** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)



## Example

```
$ java -jar dist/vcfmakedict.jar test.vcf  mutations.vcf

@HD	VN:1.5
@SQ	SN:3	LN:124490595
@SQ	SN:19	LN:57230811
@SQ	SN:rotavirus	LN:1064
```



