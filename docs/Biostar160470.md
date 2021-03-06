# Biostar160470

Getting untranslated nucleotide sequences on tblastn standalone 


## Usage

```
Usage: biostar160470 [options] Files
  Options:
    -p, --bindir
      Blast binaries path
    -d, --db
      Blast db name
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


## See also in Biostars

 * [https://www.biostars.org/p/160470](https://www.biostars.org/p/160470)


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
$ make biostar160470
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

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/biostar/Biostar160470.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/biostar/Biostar160470.java)


<details>
<summary>Git History</summary>

```
Mon Aug 7 09:53:19 2017 +0200 ; fixed unicode problems after https://github.com/lindenb/jvarkit/issues/82 ; https://github.com/lindenb/jvarkit/commit/68254c69b027a9ce81d8b211447f1c0bf02dc626
Wed May 24 17:27:28 2017 +0200 ; lowres bam2raster & fix doc ; https://github.com/lindenb/jvarkit/commit/6edcfd661827927b541e7267195c762e916482a0
Fri May 12 18:07:46 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/ca96bce803826964a65de33455e5231ffa6ea9bd
Fri Apr 14 15:27:32 2017 +0200 ; annotation proc ; https://github.com/lindenb/jvarkit/commit/72b9383a8472e5a91120bab84d15b8acad4db8d4
Fri Apr 8 17:17:56 2016 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/a943c4dfb102e4e4475d733fb32eb3dd22eb2760
Tue Oct 6 17:27:21 2015 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/35fed6f953545afc1b47f1e4b6dc32f5837646c5
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **biostar160470** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


## Example

Makefile:

```make
bin.dir=/commun/data/packages/ncbi/ncbi-blast-2.2.28+/bin

all: blastdb.nin
	cat roxan.fa | ${bin.dir}/tblastn -db blastdb -outfmt 5 | java -jar biostar160470.jar -p ${bin.dir} -d blastdb| xmllint --format - 

blastdb.nin: mysequences.fa
	${bin.dir}/makeblastdb -dbtype nucl -in $< -out blastdb
```

ouput:
```xml
              <Hsp>
                <Hsp_num>5</Hsp_num>
                <Hsp_bit-score>31.9574</Hsp_bit-score>
                <Hsp_score>71</Hsp_score>
                <Hsp_evalue>0.000226217</Hsp_evalue>
                <Hsp_query-from>520</Hsp_query-from>
                <Hsp_query-to>575</Hsp_query-to>
                <Hsp_hit-from>1711</Hsp_hit-from>
                <Hsp_hit-to>1860</Hsp_hit-to>
                <Hsp_query-frame>0</Hsp_query-frame>
                <Hsp_hit-frame>1</Hsp_hit-frame>
                <Hsp_identity>16</Hsp_identity>
                <Hsp_positive>27</Hsp_positive>
                <Hsp_gaps>6</Hsp_gaps>
                <Hsp_align-len>56</Hsp_align-len>
                <Hsp_qseq>MGEFRLCDRLQKGKACPDGDKCRCAHGQEELNEWLDRREVLKQKLAKARKDMLLCP</Hsp_qseq>
                <Hsp_hseq>VGSYYLCKDMINKQDCKYGDNCTFAYHQEEIDVWTEERK------GTLNRDLLFDP</Hsp_hseq>
                <Hsp_midline>+G + LC  +   + C  GD C  A+ QEE++ W + R+          +D+L  P</Hsp_midline>
                <Hsp_hit-DNA>GTGGGCTCCTACTACCTGTGCAAAGACATGATTAACAAGCAGGACTGTAAGTACGGGGATAACTGCACCTTCGCCTACCATCAGGAGGAGATCGACGTGTGGACCGAGGAGCGGAAG------------------CTGCTCTTCGACCCG</Hsp_hit-DNA>
              </Hsp>
              <Hsp>
                <Hsp_num>6</Hsp_num>
                <Hsp_bit-score>22.3274</Hsp_bit-score>
                <Hsp_score>46</Hsp_score>
                <Hsp_evalue>0.215374</Hsp_evalue>
                <Hsp_query-from>22</Hsp_query-from>
                <Hsp_query-to>62</Hsp_query-to>
                <Hsp_hit-from>3316</Hsp_hit-from>
                <Hsp_hit-to>3435</Hsp_hit-to>
                <Hsp_query-frame>0</Hsp_query-frame>
                <Hsp_hit-frame>1</Hsp_hit-frame>
                <Hsp_identity>15</Hsp_identity>
                <Hsp_positive>19</Hsp_positive>
                <Hsp_gaps>1</Hsp_gaps>
                <Hsp_align-len>41</Hsp_align-len>
                <Hsp_qseq>HEAPWTNLTPSWRRPTHRTTVPLAVLRNQPPRQSPACPTLP</Hsp_qseq>
                <Hsp_hseq>HQAAPSPLRPCPSSPHHRPGVRTQAHVLQPP-EAPLKPGLP</Hsp_hseq>
                <Hsp_midline>H+A  + L P    P HR  V       QPP ++P  P LP</Hsp_midline>
                <Hsp_hit-DNA>CATCAGGCAGCCCCCAGCCCCCTGAGGCCCTGTCCATCTTCTCCCCACCACCGCCCCGGTGTGCGTACCCAGGCGCACGTGCTGCAGCCCCCG---GCCCCGCTGAAACCTGGGCTGCCC</Hsp_hit-DNA>
              </Hsp>
```

