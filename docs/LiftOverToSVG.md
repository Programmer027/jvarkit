# LiftOverToSVG

Convert LiftOver chain files to animated SVG


## Usage

```
Usage: liftover2svg [options] Files
  Options:
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    --version
      print version and exit
    -b
      add this build name
      Default: []
    -t
       seconds per step
      Default: 20.0
    -w
      width
      Default: 1000

```


## Keywords

 * svg
 * liftover
 * ucsc
 * xml


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
$ make liftover2svg
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/liftover/LiftOverToSVG.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/liftover/LiftOverToSVG.java)


<details>
<summary>Git History</summary>

```
Mon May 22 16:12:07 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/778fea07cb650833dcb197b69f1add57f23b21c3
Thu Apr 27 17:22:22 2017 +0200 ; cont jcommander ; https://github.com/lindenb/jvarkit/commit/0a27a246a537d2b48201596067652ea26bfc28d6
Thu Oct 30 15:59:55 2014 +0100 ; liftOver to SVG ; https://github.com/lindenb/jvarkit/commit/1b886abf0082236c5ed63b86f1d6411d04b4b9e1
Wed Oct 22 22:11:18 2014 +0200 ; liftOver to SVG ; https://github.com/lindenb/jvarkit/commit/3ef9302f60d7a7b61c563295c925de6f8f4801cf
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **liftover2svg** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


## Screenshot

https://twitter.com/yokofakun/status/525014376387215360

![svg ](https://pbs.twimg.com/media/B0k5ytFCIAAiBPJ.png)

## Examples

### Examples 1

hg16 to hg38 http://cardioserve.nantes.inserm.fr/~lindenb/liftover2svg/hg16ToHg38.svg

BIG FILE : hg38 to panTro4 http://cardioserve.nantes.inserm.fr/~lindenb/liftover2svg/hg38ToPanTro4.svg



### Example 2

create a **SVG** file for **hg16** to **hg38**.

```makefile
.PHONY:all 
all: test.svg


test.svg: hg16ToHg17.over.chain hg17ToHg18.over.chain hg18ToHg19.over.chain hg19ToHg38.over.chain dist/liftover2svg.jar
	java -jar dist/liftover2svg.jar -b hg16 -b hg17 -b hg18 -b hg19 -b hg38 \
			 hg16ToHg17.over.chain hg17ToHg18.over.chain hg18ToHg19.over.chain hg19ToHg38.over.chain > $@

hg16ToHg17.over.chain : 
	curl -s "http://hgdownload-test.cse.ucsc.edu/goldenPath/hg16/liftOver/$@.gz" | gunzip -c |\
	grep chain > $@

hg17ToHg18.over.chain : 
	curl -s "http://hgdownload-test.cse.ucsc.edu/goldenPath/hg17/liftOver/$@.gz" | gunzip -c |\
	grep chain > $@

hg18ToHg19.over.chain : 
	curl -s "http://hgdownload-test.cse.ucsc.edu/goldenPath/hg18/liftOver/$@.gz" | gunzip -c |\
	grep chain > $@
	
hg38ToPanTro4.over.chain :
	curl -s "http://hgdownload-test.cse.ucsc.edu/goldenPath/hg38/liftOver/$@.gz" | gunzip -c |\
	grep chain > $@

hg19ToHg38.over.chain hg19ToPanTro4.over.chain :
	curl -s "http://hgdownload-test.cse.ucsc.edu/goldenPath/hg19/liftOver/$@.gz" | gunzip -c |\
	grep chain > $@


dist/liftover2svg.jar: ./src/main/java/com/github/lindenb/jvarkit/tools/liftover/LiftOverToSVG.java
	$(MAKE)  liftover2svg

```


