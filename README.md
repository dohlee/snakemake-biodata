# snakemake-biodata

Download reference biodata in an easy and reproducible way.

## Requirements

- snakemake>=5.1.4
- stable internet connection

## Available data
- reference
    - genome
        - hg38
        - GRCh38
    - transcriptome
        - hg38
        - GRCh38
- sample data
    - RRBS
        - single-end

## Remote urls
- reference genome hg38: https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.hg38.genome.fa.gz
- reference genome GRCh38:
https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.GRCh38.genome.fa.gz
- reference transcriptome hg38:
https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.hg38.transcriptome.fa.gz
- reference transcriptome GRCh38:
https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.hg38.transcriptome.fa.gz
- sample data
    - RRBS
        - single-end: https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/sample-data/rrbs/se/RRBS.se.fastq.gz

## Example rules
All data is stored in remote storage. To use remote file with HTTPS protocol, import required module before writing rules as below:
```python
from snakemake.remote.HTTP import RemoteProvider as HTTPRemoteProvider
HTTP = HTTPRemoteProvider()
```
### Reference genome-hg38
Download hg38 genome fasta.
```python
import os

rule download_hg38_genome:
    input:
        HTTP.remote('https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.hg38.genome.fa.gz', keep_local=True)
    output:
        'Homo_sapiens.hg38.genome.fa.gz'
    run:
        basename = os.path.basename(output)
        shell('mv {input} {output}')
```

### Reference genome-GRCh38
Download GRCh38 genome fasta.
```python
import os

rule download_GRCh38_genome:
    input:
        HTTP.remote('https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.GRCh38.genome.fa.gz', keep_local=True)
    output:
        'Homo_sapiens.GRCh38.genome.fa.gz'
    run:
        basename = os.path.basename(output)
        shell('mv {input} {output}')
```

### Reference transcriptome-hg38
Download hg38 transcriptome fasta.
```python
import os

rule download_hg38_transcriptome:
    input:
        HTTP.remote('https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.hg38.transcriptome.fa.gz', keep_local=True)
    output:
        'Homo_sapiens.hg38.transcriptome.fa.gz'
    run:
        basename = os.path.basename(output)
        shell('mv {input} {output}')
```

### Reference transcriptome-GRCh38
Download GRCh38 transcriptome fasta.
```python
import os

rule download_GRCh38_transcriptome:
    input:
        HTTP.remote('https://sgp1.digitaloceanspaces.com/dohlee-bioinfo/reference/Homo_sapiens.GRCh38.transcriptome.fa.gz', keep_local=True)
    output:
        'Homo_sapiens.GRCh38.transcriptome.fa.gz'
    run:
        basename = os.path.basename(output)
        shell('mv {input} {output}')
```
