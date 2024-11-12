# DATA 182 Assignment 3

In this assignment you will implement a neural network to generate news headlines, by training an LSTM-based language model.
You will also train a Transformer to summarize news articles.

## Setup
Make sure your machine is set up with the assignment dependencies.

### [Option 1] Working on Colab (Recommended)
We recommend working on Colab with GPU enabled since this assignment needs a fair amount of compute.

### Instructions for Colab:
Please follow the instructions **carefully** below to work on Colab:

First:
* Clone the repository with `git clone git@github.com:datac182fa24/datac182_hw3_student.git` as usual.
* Upload the created folder to Google Drive.
* Double click on `summarization.ipynb` and open it in Colab
* Make sure you're connected to a GPU runtime!

The following steps should be done every time you open or re-open the notebook:
* First, mount your Google Drive by running the following code in a cell:
```python
from google.colab import drive
drive.mount('/content/drive')
```
* Navigate to the homework directory by running the following code in a cell:
```python
%cd /content/drive/MyDrive/PATH/TO/HW/REPO
```
So, for example if you uploaded the homework to a folder called `datac182_hw3_student` in your Google Drive, you would run:
```python
%cd /content/drive/MyDrive/datac182_hw3_student
```
* Download the dataset (**ONLY RUN ONCE**):
```python
!bash download_data.sh
```

### Submitting your work:
Once you are done working, create a zip file of your work by running the following code in a cell:
```python
!bash collect_submission.sh
```
This will create a file called `assignment3.zip` in the current directory. Download this file to your computer and upload it to Gradescope.

### [Option 2] Install Anaconda and Required Packages (Slow)
The preferred approach for installing all the assignment dependencies is to use
[Anaconda](https://www.anaconda.com/products/individual), which is a Python distribution
that includes many of the most popular Python packages for science, math,
engineering and data analysis. Once you install Anaconda you can run the following
command inside the homework directory to install the required packages for this homework:

```bash
conda env create -f cs182_hw3.yml
```

Once you have all the packages installed, run the following command **every time**
to activate the environment when you work on the homework.
```bash
conda activate cs182_hw3
```

If you have access to GPU then you can uninstall cpu version and install cuda version PyTorch.
```bash
conda uninstall cpuonly pytorch
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```

If you are on macos, run the following command to install `wget` and `md5sha1sum`.
```bash
brew install md5sha1sum wget
```

### [Option 3] Working on a Virtual Machine (Slow)
This assignment is provided pre-setup with a VirtualBox image. Installation Instructions:
1. Follow [the instructions here](https://www.virtualbox.org/manual/ch02.html) to install VirtualBox if it is not already installed.
2. [Download the VirtualBox image here](https://drive.google.com/file/d/1Upo6wDUR0QiQLwyzh4pWwdnoG01VFBnv/view?usp=sharing)
3. Load the VirtualBox image using [the instructions here](https://docs.oracle.com/cd/E26217_01/E26796/html/qs-import-vm.html)
4. Start the VM. The username and password are both cs182. Required packages are pre-installed and the cs182_hw3 environment activated by default.
5. Download the assignment code onto the VM yourself.

**FAQ**

**I get an error "AMD-V is disabled in the BIOS" or "Intel-VT is disabled in the BIOS" or similar**

Solution: See [this link](https://docs.fedoraproject.org/en-US/Fedora/13/html/Virtualization_Guide/sect-Virtualization-Troubleshooting-Enabling_Intel_VT_and_AMD_V_virtualization_hardware_extensions_in_BIOS.html)


**The virtual machine won't boot**

Solutions:

- Try increasing the number of allocated CPUs: Under Settings→System→Processor
- Try [increasing the amount of allocated memory:](https://superuser.com/questions/926339/how-to-change-the-ram-allocated-to-an-os-in-virtualbox)

### Download data (For option 2 and 3):
To download the data, run the following command from the assignment root directory:
```bash
bash download_data.sh
```
If you get the error "bash: ./download_data.sh: Permission denied" run `chmod +x download_data.sh` and try again.

### Start Jupyter Notebook (For option 2 and 3)
After you download data, you should start the IPython notebook server
from the homework 1 directory with the following command:

```bash
jupyter notebook
```

## Submitting your work:
Once you are done working, run the `collect_submission.sh` script; this will produce a file called `assignment3.zip`.

Check that your submission contains:
- "smmarization.ipynb"
- "transformer.py", "transformer_attention.py", "language_model.py"
- Your folder for best models for each notebook, `best_models`
- Your folder for submission logs, `submission_logs`

Upload this file to Gradescope.
The Gradescope will run an autograder on the files you submit. It is very unlikely but still possible that your implementation might fail to pass some test cases due to randomness.
If you think your code is correct, you can simply rerun the autograder to check check whether it is really due to randomness.

## Q1: Transformer Network for Summarization (15 points)
The IPython notebook `Summarization.ipynb` will introduce you to the implementation
of Transformer to summarize news articles. Follow the instructions in the notebook to complete this part.
