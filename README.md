# DADA2 QIIME 2 plugin

This package contains the DADA2 QIIME 2 plugin. It is currently in pre-release status. This documentation is intended for demonstration/testing purposes only. If you're interested in learning to use QIIME 2, you should start at http://2.qiime.org.

## Using DADA2 through QIIME 2

You can install the DADA2 plugin as follows using Miniconda.

```bash
conda create -n q2-dada2 -c r r python=3.5
source activate q2-dada2
conda install -c bioconda bioconductor-dada2
pip install https://github.com/qiime2/qiime2/archive/master.zip https://github.com/qiime2/q2cli/archive/master.zip https://github.com/qiime2/q2-types/archive/master.zip https://github.com/qiime2/q2-feature-table/archive/master.zip https://github.com/gregcaporaso/q2-dada2/archive/master.zip
```

You can first use DADA2 to explore the quality of a tutorial dataset as follows.

```bash
curl -sO https://dl.dropboxusercontent.com/u/2868868/data/qiime2/artifacts/fmt-tutorial-per-sample-fastq.qza
qiime dada2 plot-qualities --i-demultiplexed-fastq-dir fmt-tutorial-per-sample-fastq.qza --o-visualization quality-plots --p-n 10
qiime tools view quality-plots.qzv
```

You can then use DADA2 to denoise, dereplicate, and remove chimeras from the same dataset as follows.

```bash
qiime dada2 denoise --i-demultiplexed-fastq-dir /Users/caporaso/gdrive/published-documents/qiime2/2016-fmt-tutorial/fmt-tutorial-per-sample-fastq.qza --o-table fmt-tutorial-table.qza
qiime feature-table summarize --i-table fmt-tutorial-table.qza --o-visualization fmt-tutorial-table-summ
qiime tools view fmt-tutorial-table-summ.qzv
```
