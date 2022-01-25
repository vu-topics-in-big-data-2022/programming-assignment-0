# Homework-0

Due Date: Thursday January 27 11:59 PM

This is an introductory homework. The idea is to complete the steps as listed below and then two python notebook that show the work done. Please refer to the following instructions in this work:

1. [Obtain AWS academy access](https://github.com/vu-topics-in-big-data-2022/instructions/blob/main/aws/student_aws_academy_learner_lab_guide.pdf). You should have received an email for that. If not, then reach out to instructors immediately.
2. [Read the overview of google colab and colab with github](https://github.com/vu-topics-in-big-data-2022/instructions/blob/main/colab/readme.md).
3. [Read the pdf that shows how to collect the link saying open in colab for the notebook](./CorrectingTheLinksInPythonNotebook.pdf) and open the [Assignment_0.ipynb](./Assignment_0.ipynb) in google colab and correct the link.
4. Run the steps listed in [Assignment_0.ipynb](./Assignment_0.ipynb) and save it back to github.
5. Read https://towardsdatascience.com/connecting-google-colab-to-an-amazon-ec2-instance-b61be9f9cf30
6. Run Assignment_0 notebook on AWS using the instructions from step 5 and save it as Assignment_0-aws.ipynb in your repository.
8. Submit the link of your repository that was created by github classroom in the brightspace as the submission to the assignment. This last step is critical. Without this your work is not considered submitted.


# Additional Instructions

## Instance creation

- Use "Ubuntu Server 20.04 LTS" with type "t2.large", increase disk memory size to 16gb, and open port 8888 for jupyter

![](./screenshots/ubuntu_ami.png)

![](./screenshots/t2_large.png)

![](./screenshots/16gb_storage.png)

![](./screenshots/ports_for_jupyter.png)

## Log into your instance

### Background information about SSH
Secure shell is a cryptographically secure mechanism of connecting over a network to a remote computer. The link https://www.ssh.com/academy/ssh provides a detailed overview of the protocol. The page https://missing.csail.mit.edu/2020/command-line/ provides a good overview of command line. The section in the missing semester page on Remote Machines introduces some ssh recipes. Please pay special attention to these as this will be very important in the class.

Here are a few video links that provide specific information on working with ssh and EC2 instances.

* For Windows user: https://www.youtube.com/watch?v=bi7ow5NGC-U
* For Mac and Linux users: https://www.youtube.com/watch?v=Nv_1u8gCkIQ

### Assignment specifics for SSH
- ssh into your instance
```
ssh -i .ssh/insertYourKey.pem ubuntu@0.00.000.00
```

- If on linux/mac (if you are on windows and use putty, please consult the internet), if you get the following error when attempting to ssh in...
```sh
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '.ssh/insertYourKey.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key ".ssh/insertYourKey.pem": bad permissions
ubuntu@0.00.000.00: Permission denied (publickey).
```

then you should run the command:

```sh
chmod 600 .ssh/insertYourKey.pem
```

and try again


## set up instance

```sh
sudo apt-get update
sudo apt install -y python3-pip python3.8-venv
python3 -m venv big_data_env
source big_data_env/bin/activate
pip install pandas pyarrow tqdm jupyter_http_over_ws
```

- add 16gb of swap space to the instance following the instructions [here](https://www.howtogeek.com/455981/how-to-create-a-swap-file-on-linux/)

- follow instructions [here](https://research.google.com/colaboratory/local-runtimes.html) to connect colab to your notebook instance

- run your code


## References 

You may want to refer to pandas documentation and tutorials. Take a look at the [attached documentation of pandas](Pandas.pdf). Other useful pandas links

* https://www.datacamp.com/community/tutorials/pandas-tutorial-dataframe-python
* https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html
* https://jonathansoma.com/lede/foundations/classes/pandas%20columns%20and%20functions/apply-a-function-to-every-row-in-a-pandas-dataframe/
* https://datatofish.com/sort-pandas-dataframe/
