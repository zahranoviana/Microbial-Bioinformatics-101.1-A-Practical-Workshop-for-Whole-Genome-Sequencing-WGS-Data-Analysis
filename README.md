# Microbial Bioinformatics 101: A Practical Workshop for Whole Genome Sequencing (WGS) Data Analysis

Microbial bioinformatics merges advanced computing with microbiology, decoding genetic and functional traits of microorganisms. This workshop equips BRIN staff to leverage sequencing and analysis tools for deeper insights into microbial interactions and applications in research.  

Session 1: June 27th 2024  

Instructor: Zahra Noviana, Rida Tiffarent, Herjuno Ari Nugroho, Riki Ruhimat, Fajar Nasrulloh, Rini Riffiani, Panji Cahya Mawarda (Tim Ad-hoc Genom Mikroba - PRMT BRIN)  

Participant: Staff of Research Center for Applied Microbiology BRIN

## Outline
### Part 1 - Navigating the Command Line
1. Installation of Window Subsystem for Linux (Window user only) 
2. Installation of Ubuntu 
3. Installation of Miniconda3 
4. Getting Familiar with the Command Line

### Part 2 - Quality check of sequences
1. Installation of nanoplot and fastqc
2. Quality check for long-read sequences (Oxford Nanopore Technologies)
3. Quality check for short-read sequences (Illumina)

### Part 3 - Assembly and annotation
1. Assembly and annotation for long-read sequences (Oxford Nanopore Technologies)
2. Data visualization
__________________________
## Let's get things started

### Let's delve into part 1
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
   vim called notes.txt
   ```   
   quit using q or Esc        
   
   
__________________________

## Here we go Part 2

### 1. Installation of nanoplot and fastqc via conda 
   
   
   #### a. Create conda environment called qc_check
   ```
   ## This is to creat env called qc_check
   conda create --name qc_check
   ```   

   #### b. Activate qc_check environment
   ```
   ## This is to activate the qc_Check
   conda activate qc_check
   ```
  
   #### c. Install nanoplot via conda
   Install nanoplot
   ```
   ## This is to install nanoplot
   conda install bioconda::nanoplot
   ```

   Check if nanoplot is succesfully installed
   ```
   ## This is to check the installation
   which NanoPlot
   ```

   #### d. Check quality of long-read sequences using 
   Get the data \
   Sources: \
   https://github.com/hpc-mahameru/Bioinformatics-User-Meeting/tree/main \
   https://training.galaxyproject.org/training-material/topics/assembly/tutorials/unicycler-assembly/tutorial.html

   ```
   ## This is to create and enter a folder
   mkdir ONT
   cd ONT/   
   ```

   ```
   ## This is to get the data
   wget https://zenodo.org/record/940733/files/minion_2d.fq
   
   ```

   Run NanoPlot
   ```
   ## This is to run NanoPlot
   NanoPlot --fastq minion_2d.fq -o NanoPlot
   ```
   *check the result
   
   Go back to the main folder
   ```
   ## This is to go back to previous folder
   cd ..
   ```
   
   #### e. Install fastqc via conda
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

   #### d. Check quality of short-read sequences using fastqc
   Get the data \
   Sources: \
   https://github.com/hpc-mahameru/Bioinformatics-User-Meeting/tree/main \
   https://training.galaxyproject.org/training-material/topics/assembly/tutorials/unicycler-assembly/tutorial.html

   ```
   ## This is to create and enter a folder
   mkdir illumina
   cd illumina/   
   ```

   ```
   ## This is to get the data
   wget https://zenodo.org/record/940733/files/illumina_f.fq 
   wget https://zenodo.org/record/940733/files/illumina_r.fq 
   ```

   Run fastqc
   ```
   ## This is to run fastqc
   fastqc illumina_f.fq illumina_r.fq -o fastqc
   ```
   *check the result
   

   Go back to the main folder
   ```
   ## This is to go back to previous folder
   cd ..
   ```

   Deactivate the environment
   ```
   ## This is to deactivate qc_check
   conda deactivate qc_check
   ```

__________________________

## Entering the 3rd Part

### 1. Assembly and annotation for long-read sequences (Oxford Nanopore Technologies) using Unicycler
   
   #### a. Create conda environment called assembly
   ```
   ## This is to creat env called assembly
   conda create --name assembly
   ```   

   #### b. Activate assembly environment
   ```
   ## This is to activate the assembly
   conda activate assembly
   ```

   #### c. Install the tools for assembly, annotation, and qc
   ```
   ## This is to activate the assembly
   conda install -c bioconda unicycler=0.4.7 prokka=1.14.6 quast=5.0.2
   ```

   #### d. Run the assembly
   ```
   ## Go to ONT folder
   cd ONT/   
   ```
   
   ```
   ## This is to run assembly using unicycler
   unicycler -l minion_2d.fq -o assembly
   ```

   #### e. Check the assembly result using quast
   ```
   ## This is to run quast
   quast assembly/ -o quast
   ```
   *check the result
   

   #### f. Do annotation using prokka
   ```
   ## This is to run prokka
   prokka assembly/xxxxxx.fa -o prokka
   ```
   *check the result
   


### 2. Data visualization
Go to https://proksee.ca/ and upload assembly and anotation files for genome visualization



__________________________________________________________
### Finish line


