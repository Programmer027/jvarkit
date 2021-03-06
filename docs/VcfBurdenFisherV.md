# VcfBurdenFisherV

Fisher Case / Controls per Variant (Vertical)


## Usage

```
Usage: vcfburdenfisherv [options] Files
  Options:
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -if, --ignorefilter
      accept variants having a FILTER column. Default is ignore variants with 
      a FILTER column
      Default: false
    -o, --output
      Output file. Optional . Default: stdout
    --version
      print version and exit

```


## Keywords

 * vcf
 * burden
 * fisher


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
$ make vcfburdenfisherv
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/burden/VcfBurdenFisherV.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/burden/VcfBurdenFisherV.java)


<details>
<summary>Git History</summary>

```
Wed Sep 20 15:52:53 2017 +0200 ; moving to amalgamation ; https://github.com/lindenb/jvarkit/commit/fca74f53afa062f238c8a899ee0ee6e7cd15136c
Fri Aug 4 16:40:02 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/57f08e720a97f952bab81961431d83accdefeae3
Wed Jul 26 18:09:38 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/576fdd17812f9a47491945cb8bb74990ffb084c9
Mon May 15 20:23:58 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/bb4421e107f53c95efdcad8fb54f022f9642312c
Fri Jun 3 16:35:43 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/8990c064a122e300faddcab38bd476a9f8b9758e
Wed May 25 10:49:01 2016 +0200 ; vcf burden R ; https://github.com/lindenb/jvarkit/commit/9e18b322b437bd9269c36406e35cdafce2ba71e5
Tue May 24 16:49:08 2016 +0200 ; error in fisherburdenv ; https://github.com/lindenb/jvarkit/commit/ad8d8c2252786a71d063854fddcf5c3e276a052e
Thu Apr 28 19:07:11 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/95bad48c19727c26c607a12a9b2e1e165e826aaa
Tue Apr 26 17:21:33 2016 +0200 ; vcfbuffer ; https://github.com/lindenb/jvarkit/commit/3300512769fd3bb2ee4430c9474367b06f2edc7c
Thu Apr 21 10:39:25 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/7adf87adc987efbe89def5c530f5a84be0c841d4
Mon Apr 18 17:34:40 2016 +0200 ; cnot burden ; https://github.com/lindenb/jvarkit/commit/e0403a175b479d9e8bec1ced1e3f35715f404ad8
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **vcfburdenfisherv** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


Variant in that VCF should have one and only one ALT allele. Use https://github.com/lindenb/jvarkit/wiki/VcfMultiToOneAllele if needed.

### Output


#### INFO column

 *  BurdenF1Fisher : Fisher test


#### FILTER column

 *  BurdenF1Fisher :Fisher test doesn't meet  user's requirements


### see also


 *  VcfBurdenFilter3



