# PcrClipReads

Soft clip bam files based on PCR target regions


## Usage

```
Usage: pcrclipreads [options] Files
  Options:
    --bamcompression
      Compression Level.
      Default: 5
  * -B, --bed
      Bed file containing non-overlapping PCR fragments
    -flag, --flag
      Only run on reads having sam flag (flag). -1 = all reads. (as 
      https://github.com/lindenb/jvarkit/issues/43) 
      Default: -1
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -largest, --largest
      see if a read overlaps two bed intervals use the bed region sharing the 
      longest sequence with a read. see 
      https://github.com/lindenb/jvarkit/issues/44 
      Default: false
    -o, --output
      Output file. Optional . Default: stdout
    -pr, --programId
      add a program group PG to the clipped SAM records
      Default: false
    --samoutputformat
      Sam output format.
      Default: TypeImpl{name='SAM', fileExtension='sam', indexExtension='null'}
    --version
      print version and exit

```


## Keywords

 * sam
 * bam
 * pcr
 * bed



## See also in Biostars

 * [https://www.biostars.org/p/147136](https://www.biostars.org/p/147136)
 * [https://www.biostars.org/p/178308](https://www.biostars.org/p/178308)


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
$ make pcrclipreads
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/pcr/PcrClipReads.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/pcr/PcrClipReads.java)


<details>
<summary>Git History</summary>

```
Tue Jul 11 11:11:36 2017 +0200 ; fix https://github.com/lindenb/jvarkit/issues/81#issuecomment-314378286 ; https://github.com/lindenb/jvarkit/commit/0efc15763059f91d61141473affa79fd04de8aba
Fri Jun 30 17:20:28 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/5fe0a8568d706e8cd5898ff66c0ebd8b1f8447a5
Fri Jun 30 10:21:33 2017 +0200 ; fix pcr clipper ; https://github.com/lindenb/jvarkit/commit/50c95549a1a68ee34a9c9d168723172febd90cd2
Thu Jun 29 20:41:53 2017 +0200 ; start fix https://github.com/lindenb/jvarkit/issues/81 ; https://github.com/lindenb/jvarkit/commit/3758963956c9ceec249feeb4a076c98314756c14
Wed May 24 17:27:28 2017 +0200 ; lowres bam2raster & fix doc ; https://github.com/lindenb/jvarkit/commit/6edcfd661827927b541e7267195c762e916482a0
Sun May 21 20:02:10 2017 +0200 ; instanceMain -> instanceMainWithExit ; https://github.com/lindenb/jvarkit/commit/4fa41d198fe7e063c92bdedc333cbcdd2b8240aa
Mon May 15 17:17:02 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/fc77d9c9088e4bc4c0033948eafb0d8e592f13fe
Tue May 9 18:05:15 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/450dcbb4f5792e9ef1bb829d9214fcf2cf3c1121
Mon Dec 12 13:17:00 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/91b443a14fe47871dc35efdf58c38729fec9d5a9
Mon Feb 29 19:16:30 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/2fe469ec4505823fe7fcdc228f3757bac51a107a
Thu Feb 25 14:49:08 2016 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/cf1bf46196fda4e95ded4d3bbfcf71df00164ebc
Wed Feb 24 18:00:11 2016 +0100 ; answer to https://github.com/lindenb/jvarkit/issues/43 ; https://github.com/lindenb/jvarkit/commit/5beeda137042c132e892129c8cd57af8a6d1a129
Tue Jul 7 16:03:42 2015 +0200 ; pcr slice reads ; https://github.com/lindenb/jvarkit/commit/fc442787c5e74077f0c7256750480b05b4b93317
Mon Jun 22 14:55:09 2015 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/44c533625c38c0538767462793a990e7b3bc5b3d
Thu Jun 18 23:06:45 2015 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/4ea3c3aa7e8870f34bd12b8337be9b976d38b9db
Thu Jun 18 22:37:19 2015 +0200 ; https://github.com/lindenb/jvarkit/wiki/PcrClipReads clip BAM reads on PCR fragments #tweet ; https://github.com/lindenb/jvarkit/commit/8d98ead16d3882afef6d09ff538e7dd9e5f558e3
Thu Jun 18 18:33:28 2015 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/dcfd0ddf4d1a6817487762c188d92e149438abcb
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **pcrclipreads** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)




 Soft clip BAM files based on PCR target regions https://www.biostars.org/p/147136/


 *  mapping quality is set to zero if a read on strand - overlap the 5' side of the PCR fragment
 *  mapping quality is set to zero if a read on strand + overlap the 3' side of the PCR fragment
 *  mapping quality is set to zero if no PCR fragment is found


after processing the BAM file should be sorted, processed with samtools calmd and picard fixmate


### Example


```
echo  "seq2\t1100\t1200" > test.bed
java -jar dist/pcrclipreads.jar -B test.bed  samtools-0.1.19/examples/ex1.bam  |\
	samtools  view -q 1 -F 4 -Sbu  -  |\
	samtools  sort -o clipped.bam -  && samtools index clipped.bam

samtools tview -p seq2:1100  clipped.bam  samtools-0.1.19/examples/ex1.fa

```


### output


![img](http://i.imgur.com/bjDEnMW.jpg)



```
    1091      1101      1111      1121      1131      1141      1151      1161      1171      1181      1191
AAACAAAGGAGGTCATCATACAATGATAAAAAGATCAATTCAGCAAGAAGATATAACCATCCTACTAAATACATATGCACCTAACACAAGACTACCCAGATTCATAAAACAAATNNNNN
              ...................................                               ..................................
              ,,,                                                               ..................................
              ,,,,,                                                              .................................
              ,,,,,,,,,,,                                                        .............................N...
              ,,,,,,,,                                                             ...............................
              ,,g,,,,,,,,,,,,,                                                        ............................
              ,,,,,,,,,,,,,,,,,,,,                                                    ............................
              ,,,,,,,,,,,,,,,,,,,                                                       ..........................
              ,,,,,,,,,,,,,,,,,,,,,,                                                    ..........................
              ,,,,,,,,,,,,,,,,,,,,,,,                                                       ......................
              ,,,,,,,,,,,,,,,,,,,,,,,,,,                                                        ..................
              ,,,,,,,,,,,,,,,,,,,,,,,,,,                                                        ..................
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                       .................
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                       ................
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                        ...............
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                         ............
              ,,,,,,,,,,,,a,,,,,,,,,,,,,,,,,,,                                                             .......
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                            ......
              ,,a,,,a,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                              ....
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                             ....
              ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,                                                                .
                                                                                                                 .

```

## Cited in

 * BAMClipper: removing primers from alignments to minimize false-negative mutations in amplicon next-generation sequencing [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5431517/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5431517/)


## History

 * 20170630 : rewritten after [https://github.com/lindenb/jvarkit/issues/81](https://github.com/lindenb/jvarkit/issues/81)




