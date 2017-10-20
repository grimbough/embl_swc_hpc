## Identifying our computer

```
hostname
```

## Our first SLURM job

```
srun hostname
```

## Exploring our example program

```
cd $HOME/embl_swc_hpc/exercises
./hpc_example.py -t 10 -l 100
```

## Running example program on on the cluster

```
srun ./hpc_example.py -t 10 -l 100
```

## Running in the background

```
srun ./hpc_example.py -t 10 -l 100 &
```

## Redirecting output

```
srun --output=output.txt ./hpc_example.py -t 20 -l 100 &
```

## Creating a larger list

```
srun --output=output.txt ./hpc_example.py -t 30 -l 5000000 &
```

## Displaying details of our cluster queue

```
scontrol show partition
```

## Requesting more resources

```
srun --mem=250 \
--output=output.txt \
./hpc_example.py -t 30 -l 5000000 &
```

## Running interactive jobs
```
srun --pty bash
```

## Interactive job with more memory
```
srun --mem=250 --pty bash
```

## Using `sbatch` instead

```
sbatch batch_jobs.sh
```

## Using job dependencies to build pipelines

```
jid=$(sbatch --parsable batch_job.sh)

sbatch --dependency=afterok:$jid batch_job.sh
```