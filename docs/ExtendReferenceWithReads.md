# ExtendReferenceWithReads

Extending ends of sequences with the help of reads


## Usage

```
Usage: extendrefwithreads [options] Files
  Options:
    -f, --callingfraction
      (0.0<float<=1.0) new base must have fraction greater than this number
      Default: 0.8
    -filter, --filter
      A filter expression. Reads matching the expression will be filtered-out. 
      Empty String means 'filter out nothing/Accept all'. See https://github.com/lindenb/jvarkit/blob/master/src/main/resources/javacc/com/github/lindenb/jvarkit/util/bio/samfilter/SamFilterParser.jj 
      for a complete syntax.
      Default: mapqlt(1) || MapQUnavailable() || Duplicate() || FailsVendorQuality() || NotPrimaryAlignment() || SupplementaryAlignment()
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -N, --mincontig
      onsider only gaps in reference with size&gt;=N
      Default: 100
    -d, --mindepth
      min depth
      Default: 1
    -o, --out
      Output file. Optional . Default: stdout
  * -R, --reference
      Indexed fasta Reference file. This file must be indexed with samtools 
      faidx and with picard CreateSequenceDictionary
    --version
      print version and exit

```


## Keywords

 * read
 * fastq
 * reference
 * sam
 * bam



## See also in Biostars

 * [https://www.biostars.org/p/148089](https://www.biostars.org/p/148089)


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
$ make extendrefwithreads
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/extendref/ExtendReferenceWithReads.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/extendref/ExtendReferenceWithReads.java)


<details>
<summary>Git History</summary>

```
Wed May 24 17:27:28 2017 +0200 ; lowres bam2raster & fix doc ; https://github.com/lindenb/jvarkit/commit/6edcfd661827927b541e7267195c762e916482a0
Mon May 15 17:17:02 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/fc77d9c9088e4bc4c0033948eafb0d8e592f13fe
Fri May 12 18:07:46 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/ca96bce803826964a65de33455e5231ffa6ea9bd
Thu Apr 6 18:34:56 2017 +0200 ; moving to jcommander ; https://github.com/lindenb/jvarkit/commit/883b4ba4b693661663694256f16b137e371147fa
Thu Apr 14 12:36:51 2016 +0200 ; bam2sql ; https://github.com/lindenb/jvarkit/commit/bfc712a2e3cafe30a15d0161011918446eb9a5c3
Thu Jun 25 18:26:38 2015 +0200 ; fixed infinite loop ; https://github.com/lindenb/jvarkit/commit/ef977b708db3e9f65b434e69d2e0f807fd65b769
Thu Jun 25 16:18:29 2015 +0200 ; extends REF sequence with clipped reads #tweet ; https://github.com/lindenb/jvarkit/commit/e3e4b7c31e357848b2e156affaaead86a8b5cefe
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **extendrefwithreads** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

 
 ## Example

```
$  java   -jar dist/extendrefwithreads.jar \
     -R human_g1k_v37.fasta -f 0.3 \
     f1.bam f2.bam f3.bam 2> /dev/null |\
  cat -n | grep -E '(>|[atgc])' 

     1	>1
   167	NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNncgattaccctaacgctcac
   168	cctaaccctcnccctntnccnncnncccnncttcttccgaTAACCCTAACCCTAACCCTA
  3791	NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNatt
  3792	tatgcNctttntgctgtGATTCATGGCTGAAATCGTGTTTGACCAGCTATGTGTGTCTCT
  8691	NNNNNNNNNNNNNNNNNNNNNNNNctagGATCCTTGAAGCGCCCCCAAGGGCATCTTCTC
 64089	TGGTGAGGGAAATTAGAACCACGACAATTTGGGAACTTAGCTTCTGCCctgctccNNNNN
 66589	NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNgagtAGCTGAGACTAC
 
 ```


