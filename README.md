# Microbial Bioinformatics 101: A Practical Workshop for Whole Genome Sequencing (WGS) Data Analysis

Microbial bioinformatics merges advanced computing with microbiology, decoding genetic and functional traits of microorganisms. This workshop equips BRIN staff to leverage sequencing and analysis tools for deeper insights into microbial interactions and applications in research.  

Session 1: July 9th 2024  

Instructor: Zahra Noviana, Rida Tiffarent, Herjuno Ari Nugroho, Riki Ruhimat, Fajar Nasrulloh, Rini Riffiani, Panji Cahya Mawarda (Tim Ad-hoc Genom Mikroba - PRMT BRIN)  

Participant: Staff of Research Center for Applied Microbiology BRIN

## Outline
### Part I - Navigating the Command Line
1. Installation of Window Subsystem for Linux (Window user only) 
2. Installation of Ubuntu 
3. Installation of Miniconda3 
4. Getting Familiar with the Command Line

### Part II - Quality check of sequences
1. Installation of nanoplot via conda and quality check for long read sequences
2. Installation of fastqc via conda and quality check for short read sequences
3. Quality check for short-read sequences (Illumina)

### Part III - Assembly, annotation and data visualization
1. Assembly of illumina reads using unicycler
2. Checking the assembly result using quast
3. Annotation using prokka
4. Visualization 
__________________________
## Let's get things started

### Let's delve into part I
### 1. Installation of Window Subsystem for Linux (WSL) for Window User 
   Requirement: Windows 10 or 11 
   
   #### a. Open PowerShell as an Administrator 
   #### b. Install Window Subsystem for Linux (WSL)

   ```
   ## This is to install wsl
   wsl --install
   ```

   ![image](https://github.com/zahranoviana/Microbial-Bioinformatics-101.1-A-Practical-Workshop-for-Whole-Genome-Sequencing-WGS-Data-Analysis/assets/97138684/3fa13b2f-1c4f-4122-8b08-65c235558a1e)


   #### c. Check if wsl is succesfully installed
   ```
   ## This is to verify if the wsl is installed
   wsl --help
   ```
   or
   ```
   ## This is to verify the installed wsl version
   wsl --list --verbose
   ```
      
### 2. Installation of WSL command line interface (Ubuntu)
   
   See what's available
   ```
   ## This is to verify the available wsl interfaces
   wsl --list --online
   ```
   
   Install Ubuntu-20.04
   ```
   ## This is to install Ubuntu-20.04
   wsl --install -d Ubuntu-20.04
   ```
   *Give suitable username & password

### 3. Installation of Miniconda3
   
   Open Ubuntu
   
   Download Miniconda installer
   ```
   ## This is to download Miniconda installer
   wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /opt/miniconda-installer.sh
   ```
   
   Execute installation
   ```
   ## This is to install Miniconda
   bash /opt/miniconda-installer.sh
   ```
   
   Test if it is installed correctly
   ```
   ## This is to test the installation
   conda list
   ```

### 4. Getting familiar with the command line

   Check your working directory
   ```
   ## This is to get the path to your working directory
   pwd
   ```

   Create a new folder called bioinformatics_101
   ```
   ## This is to make a new folder called bioinformatics_101
   mkdir bioinformatics_101
   ```

   Check if bioinformatics_101 folder is succesfully created
   ```
   ## This is to list information about files and folders
   ls
   ```

   Change working directories to bioinformatics_101
   ```
   ## This is to enter folder bioinformatics_101
   cd bioinformatics_101/
   ```

   Try to create a file
   ```
   ## This is to create a file called notes.txt
   touch notes.txt
   ```      

   Edit the file
   ```
   ## This is to edit the file called notes.txt
   vim notes.txt
   ```

   - press "a" and type to edit
   - Esc if you're done with editing the file
   - type ":w" and enter to save
   - type ":q" and enter to exit 
   
__________________________

## Here we go, Part II

### 1. Installation of nanoplot via conda and quality check for long read sequences
   
   
   #### a. Create conda environment called qc_check ~30 sec
   ```
   ## This is to create env called qc_check
   conda create --name qc_check
   ```   

   #### b. Activate qc_check environment
   ```
   ## This is to activate the qc_check
   conda activate qc_check
   ```
  
   #### c. Install nanoplot via conda ~60-85 min
   Install nanoplot
   ```
   ## This is to install nanoplot
   # conda install bioconda::nanoplot
   ```

   Check if nanoplot is succesfully installed
   ```
   ## This is to check the installation
   # which NanoPlot
   ```

   #### d. Check quality of long-read sequences using NanoPlot
   Get the data \
   Sources: \
   ##https://github.com/hpc-mahameru/Bioinformatics-User-Meeting/tree/main \
   ##https://training.galaxyproject.org/training-material/topics/assembly/tutorials/unicycler-assembly/tutorial.html

   ```
   ## This is to create and enter a folder
   ## mkdir ONT
   # cd ONT/   
   ```

   ```
   ## This is to get the data
   # wget https://zenodo.org/record/940733/files/minion_2d.fq
   ```

   Run NanoPlot
   ```
   ## This is to run NanoPlot
   # NanoPlot --fastq minion_2d.fq -o NanoPlot
   ```
  
   Go back to the main folder
   ```
   ## This is to go back to previous folder
   # cd ..
   ```

   
### 2. Installation of fastqc via conda and quality check for short read sequences

   #### a. Install fastqc via conda ~ 2 min
   Install fastqc
   ```
   ## This is to install fastqc
   conda install -c bioconda fastqc
   ```

   Check if fastqc is succesfully installed
   ```
   ## This is to check the installation
   which fastqc
   ```

   #### b. Check the quality of short-read sequences using fastqc
   Get the data \
   Sources: \
   ##https://github.com/hpc-mahameru/Bioinformatics-User-Meeting/tree/main \
   ##https://training.galaxyproject.org/training-material/topics/assembly/tutorials/unicycler-assembly/tutorial.html

   ```
   ## This is to create and enter a folder
   mkdir illumina
   cd illumina/   
   ```

   ```
   ## This is to get the data ~10 min
   wget https://zenodo.org/record/940733/files/illumina_f.fq 
   wget https://zenodo.org/record/940733/files/illumina_r.fq 
   ```

   Run fastqc
   ```
   ## First create directory fastqc
   mkdir fastqc
   ```

   ```
   ## This is to run fastqc ~ 30 s
   fastqc illumina_f.fq illumina_r.fq -o fastqc
   ```

   #### c. Check the result
   First open powershell
   ```
   ## Copy folder fastqc to Downloads
   cp -r \\wsl$\Ubuntu\home\*username*\bioinformatics_101\illumina\fastqc \Users\*username*\Downloads
   ```
   
   Go back to bioinformatics_101 directory
   ```
   ## This is to go back to previous folder
   cd ~/bioinformatics_101/
   ```

   Deactivate the environment
   ```
   ## This is to deactivate qc_check
   conda deactivate
   ```

__________________________

## Entering Part III

### 1. Assembly of illumina reads using Unicycler
   
   #### a. Create conda environment called analysis
   ```
   ## This is to create env called analysis
   conda create --name analysis
   ```   

   #### b. Activate the "analysis" environment
   ```
   ## This is to activate the environment
   conda activate analysis
   ```

   #### c. Install mamba for faster installation
   ```
   ## This is to install mamba
   conda install mamba
   ```

   #### d. Install unicyler for the assembly ~2 min
   ```
   ## This is to install unicycler
   mamba install -c bioconda unicycler=0.5.0
   ```

   #### e. Run the assembly   
   ```
   ## Go to illumina folder
   cd illumina/   
   ```

   ```
   ## Check what parameters that can be included
   unicycler --help
   ```

   ```
   ## This is to run assembly using unicycler ~ 1 hour
   unicycler -l illumina_f.fq -2 illumina_r.fq -o assembly
   ```

   #### Since the assembly takes too long, download the result
   ```
   ## Create and change directory
   mkdir assembly2
   cd assembly2/
   ```

   Install gdown to download files from gdrive
   ```
   ## This is to install gdown
   pip install gdown
   ```
   
   ```
   ## Download assembly file with gdown
   gdown --no-check-certificate --folder https://drive.google.com/drive/u/1/folders/12mJhPOoPcDMSdQPjzAH5Pp_HTgvJRPTN
   ```

   #### f. Check the result
   First open powershell
   ```
   ## Copy folder fastqc to Downloads
   cp -r \\wsl$\Ubuntu\home\*username*\bioinformatics_101\illumina\assembly2\assembly_unicycler\ \Users\*username*\Downloads
   ```

   Go back to previous folder
   ```
   ## Go back
   cd ..   
   ```

   Deactivate the environment
   ```
   ## Deactivate current environment
   conda deactivate   
   ```

### 2. Checking the assembly result using quast

   #### a. Quast Installation
   We need to installed quast locally ~ 1 min
   ```
   ## This is to install quast locally 
    wget https://github.com/ablab/quast/releases/download/quast_5.2.0/quast-5.2.0.tar.gz
    tar -xzf quast-5.2.0.tar.gz
    cd quast-5.2.0
   ```

   #### b. Run quast
   ```
   ## This is to run quast
   ./quast.py ~/bioinformatics_101/illumina/assembly2/assembly_unicycler/assembly.fasta -o quast_output1/
   ```

   #### c. Check the result
   First open powershell
   ```
   ## Copy folder fastqc to Downloads
   cp -r \\wsl$\Ubuntu\home\*username*\bioinformatics_101\quast-5.2.0\quast_output1\ \Users\*username*\Downloads
   ``` 

   
### 3. Annotation using prokka  


   #### a. Activate environment
   First go to our working folder
   ```
   ## Go to destination folder
   cd ~/bioinformatics_101/illumina/   
   ```

   Activate environment
   ```
   ## Activate back the analysis environment
   conda activate analysis
   ```

   #### b. Prokka installation
   Install prokka
   ```
   ## This is to install prokka
   conda install -c bioconda prokka
   ```

   Check the installation
   ```
   ## This is to check prokka installation
   which prokka
   ```

   #### c. Run prokka
   ```
   ## This is to run prokka
   prokka assembly2/assembly_unicycler/assembly.fasta -o prokka
   ```

   #### d. Check the result 
   First open powershell
   ```
   ## Copy folder fastqc to Downloads
   cp -r \\wsl$\Ubuntu\home\*username*\bioinformatics_101\illumina\prokka\ \Users\*username*\Downloads
   ```

   
### 4. Visualization

#### a. Employing IGV 

   a. Install IGV from https://igv.org/doc/desktop/#DownloadPage/ \
   b. Genomes --> Load Genome from file --> assembly.fasta \
   c. File --> Load from file --> PROKKA_xxxxxxx.gff 

#### b. Web-based proksee.ca
Go to https://proksee.ca/ and upload assembly and anotation files for genome visualization



__________________________________________________________
### Finish line


