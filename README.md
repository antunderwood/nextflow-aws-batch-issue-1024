# nextflow-aws-batch-issue-1024


## Data sets
 - Large: s3://nextflow-datasets/52-samples/fastqs
 - Small: s3://nextflow-datasets/2-samples/fastqs

## Running the workflow
Two requirements

 - Substitute <S3 BUCKET BASE FOLDER> for one of the base S3 folders nextflow-datasets/52-samples or nextflow-datasets/2-samples
 - Substitute <AWS BATCH QUEUE> for an AWQS Batch queue you have permissions for 

```
nextflow run assembly.nf -ansi -profile aws_batch -resume \
-work-dir s3://<S3 BUCKET BASE FOLDER>/workdir \
--input_dir s3://<S3 BUCKET BASE FOLDER>/fastqs \
--output_dir s3://<S3 BUCKET BASE FOLDER>/output \
--fastq_pattern '*_{1,2}.fastq.gz' \
--adapter_file adapters.fas  \
--depth_cutoff 100 \
--qc_conditions qc_conditions.yml \
--aws_batch_queue <AWS BATCH QUEUE>
```