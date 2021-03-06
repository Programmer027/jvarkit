# VcfBurdenSplitter

Split VCF Using a Burden Splitter (by gene, transcript, etc..)


## Usage

```
Usage: vcfburdensplitter [options] Files
  Options:
    -all_enst, --all_enst
      enable grouping by ALL_ENST: gene starting with ENST
      Default: false
    -all_filtered, --all_filtered
      If defined, the group where ALL the variants are FILTERED will be saved 
      here. 
    -all_genes, --all_genes
      enable grouping by all transcript for a gene using transcript name (e.g 
      PRKCB1) 
      Default: false
    -all_nm, --all_nm
      enable grouping by ALL_NM : gene not empty and transcript starting with 
      NM_ 
      Default: false
    -all_refseq, --all_refseq
      enable grouping by ALL_REFSEQ: gene not empty and transcript NOT 
      starting with ENST
      Default: false
    -all_transcripts, --all_transcripts
      enable grouping by all transcript for a gene using gene name (e.g 
      Nm_12345) 
      Default: false
    -gh, --galaxyhtml
      When used with galaxy, the files will be expanded in that path.
      Default: <empty string>
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -if, --ignorefilter
      accept variants having a FILTER column. Default is ignore variants with 
      a FILTER column
      Default: false
    -ls, --listsplitters
      List available splitters and exit
    --maxRecordsInRam
      When writing  files that need to be sorted, this will specify the number 
      of records stored in RAM before spilling to disk. Increasing this number 
      reduces the number of file  handles needed to sort a file, and increases 
      the amount of RAM needed
      Default: 50000
    -o, --output
      Output file. Optional . Default: stdout
    -sp, --splitterName
      Splitter Name
      Default: vepso
    --tmpDir
      tmp working directory. Default: java.io.tmpDir
      Default: []
    -vepEnsg, --vepEnsg
      enable VEP 'ENSG'
      Default: false
    -vepEnsp, --vepEnsp
      enable VEP 'ENSP'
      Default: false
    -vepEnst, --vepEnst
      enable VEP 'FEATURE' starting with 'ENST'
      Default: false
    -vepFeature, --vepFeature
      enable VEP 'FEATURE' (transcript)
      Default: false
    -vepHgnc, --vepHgnc
      enable VEP 'HGNC'
      Default: false
    -vepRefSeq, --vepRefSeq
      enable VEP 'SYMBOL'= XM_ or NM_
      Default: false
    -vepSymbol, --vepSymbol
      enable VEP 'SYMBOL'
      Default: false
    --version
      print version and exit

```

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
$ make vcfburdensplitter
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/burden/VcfBurdenSplitter.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/burden/VcfBurdenSplitter.java)


<details>
<summary>Git History</summary>

```
Mon Aug 7 09:53:19 2017 +0200 ; fixed unicode problems after https://github.com/lindenb/jvarkit/issues/82 ; https://github.com/lindenb/jvarkit/commit/68254c69b027a9ce81d8b211447f1c0bf02dc626
Mon May 15 20:31:18 2017 +0200 ; fix make ; https://github.com/lindenb/jvarkit/commit/a735fd34f45bf7fa74803a0c641779857d2fa90e
Mon May 15 20:23:58 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/bb4421e107f53c95efdcad8fb54f022f9642312c
Fri Mar 24 17:36:27 2017 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/de23cf2c66b72c440f80185e931a14e8068f3b97
Tue Mar 14 18:57:04 2017 +0100 ; fixing sliding window ; https://github.com/lindenb/jvarkit/commit/b8865e650540613ff624271c11c6028ad47d680a
Wed Feb 22 19:07:03 2017 +0100 ; refactor prediction parsers ; https://github.com/lindenb/jvarkit/commit/dc7f7797c60d63cd09d3b7712fb81033cd7022cb
Fri Feb 17 11:11:24 2017 +0100 ; new slider for matilde ; https://github.com/lindenb/jvarkit/commit/32c79bdb1b5e1cf4928cbceedd6ce83f8aebd809
Fri Feb 10 15:21:09 2017 +0100 ; jfx with snippets, burdensplitter: new zones ; https://github.com/lindenb/jvarkit/commit/1670f10c5f73638a22ce9c3d49a63e0f6a92b721
Wed Jan 18 18:26:00 2017 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/4f808db2ad9a8afff2f2e4bfc59cf4f11c29e0f9
Tue Jan 17 16:55:07 2017 +0100 ; burden-splitter-debug, gatk docs ; https://github.com/lindenb/jvarkit/commit/3981682ee1753392c6dde2723ef4650331d99514
Thu Jan 12 12:58:19 2017 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/ddee18b5b803a124e670718187850a91c16e95db
Fri Nov 25 12:30:34 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/31949a5be3c9948eb6d6fa72a96e8cbcbc66796d
Thu Oct 6 14:37:57 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/5dfd9a7683725b342b21b687d70745a996529081
Tue Sep 27 15:25:14 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/4c626a9e2db6af9e3f690b53ed138ff38d4b21c3
Tue May 3 17:34:10 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/7d668372271a7ecc28da6051c0ef251f70bbece9
Fri Apr 29 17:26:25 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/231856146f1035e21b4adfbc4e87a01b60d0d39e
Thu Apr 21 10:39:25 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/7adf87adc987efbe89def5c530f5a84be0c841d4
Mon Apr 18 17:34:40 2016 +0200 ; cnot burden ; https://github.com/lindenb/jvarkit/commit/e0403a175b479d9e8bec1ced1e3f35715f404ad8
Fri Apr 15 17:09:59 2016 +0200 ; inject pedigree ; https://github.com/lindenb/jvarkit/commit/f9a18a1ce155a78b2e430d8d7860d0cab8f33722
Mon Apr 11 16:50:27 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/d84fc3f2d5da92ed230e79702df31c190bb0fb02
Tue Apr 5 12:56:37 2016 +0200 ; burdensplit ; https://github.com/lindenb/jvarkit/commit/4deff63fe7ad00b4776334cf309e46d8261bfea4
Tue Mar 29 16:37:21 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/940176b00414c37ff93bea899f82f68e6f4b7db3
Tue Mar 22 17:19:22 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/97e0e23bddd49049c71d56d495d090c0af636670
Thu Mar 17 14:29:22 2016 +0100 ; galaxy, doc, upgrade ; https://github.com/lindenb/jvarkit/commit/e4d4702a133da90094286daa0f4c15e9d4007452
Thu Mar 10 18:50:45 2016 +0100 ; spligene ; https://github.com/lindenb/jvarkit/commit/e205164bdfdeac661f425056e761bb26badae28b
Wed Mar 2 21:44:13 2016 +0100 ; Genotype filter ; https://github.com/lindenb/jvarkit/commit/3bbf30657f10c85e367a09b2fa4c78120bbc1454
Mon Feb 29 11:37:53 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/4ad2ea821e8528299fa33e9b5a64bf7f9fbb8f2d
Sun Feb 28 19:35:38 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/0509e41d72f24f887c38ab658fd6b894f677f967
Sun Feb 28 14:54:44 2016 +0100 ; burden week-end ; https://github.com/lindenb/jvarkit/commit/2f49ec436743934639d0adf51b55a577db7ee3d2
Fri Feb 26 17:41:28 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/d3402007c15a4474f375081d5f811d85d52d82be
Fri Feb 26 16:57:37 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/6fda6b1c5b65e08f2f54216eb47b114183c2c05d
Fri Feb 26 16:37:13 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/3ceade840f7306a7d48c25f8bb10eddebfa0e90a
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **vcfburdensplitter** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


### Description

This tools reads a VCF  (it should be sorted on chrom/POS and annotated with Ensembl Variation Predictor) and split data into genomic area of interest (gene, transcripts...).
For each area, a small VCF is produced and a Fished test is computed.
The final output is a set of concatenated VCF files. You could insert in a database using VcfDerby01



