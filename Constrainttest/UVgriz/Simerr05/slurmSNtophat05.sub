#!/bin/bash
#SBATCH --job-name=nmmaSNtophat.job
#SBATCH --output=nmmaSNtophat%A_%a.out
#SBATCH --error=nmmaSNtophat%A_%a.err
#SBATCH -p shared
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=32
#SBATCH --mem=96G
#SBATCH --time=12:00:00
#SBATCH --mail-type=ALL
#SBATCH --mail-user=thomas.hussenot@ijclab.in2p3.fr
#SBATCH -A umn131
#SBATCH --export=ALL
module purge
module load sdsc cpu/0.15.4 gcc/9.2.0 openmpi/4.1.1
module load anaconda3/2020.11
source /cm/shared/apps/spack/cpu/opt/spack/linux-centos8-zen2/gcc-10.2.0/anaconda3-2020.11-weucuj4yrdybcuqro5v3mvuq3po7rhjt/etc/profile.d/conda.sh
conda activate multinest1
export LD_LIBRARY_PATH=/home/thussenot/MultiNest/lib/:$LD_LIBRARY_PATH
mpiexec -n 32 lightcurve-analysis --model nugent-hyper,TrPi2018 --outdir outdirSNtophat32cores --label GRB230812B --prior ./nugent_TrPi2018GRB230812B05.prior --jet-type -1 --tmin 0.01 --tmax 32 --dt 0.01 --nlive 2048 --Ebv-max 0 --trigger-time 60168.79041667 --data ../../../simUVgriz.txt --plot --xlim 0,32 --ylim 30,18 --bestfit
