**How to Setup Bitbucket Pipeline For Master Branch Automation**

**Go to Repository —-> Repository Settings —---> Runner —-----> Add Runner  —> Configure —>  Choose System as linux shell —-- > Add Runner Name  —--> Add Labels (if you wish)**

**Run Given commands with ubuntu/rlogical user**

In Last Command Use & for running runner in Backend, Once it will show online Create Pipeline

Steps:

# download the runner zip

curl https://product-downloads.atlassian.com/software/bitbucket/pipelines/atlassian-bitbucket-pipelines-runner-2.6.0.tar.gz --output atlassian-bitbucket-pipelines-runner.tar.gz

# extract the file

mkdir atlassian-bitbucket-pipelines-runner && tar -xzvf atlassian-bitbucket-pipelines-runner.tar.gz -C atlassian-bitbucket-pipelines-runner

# launch the runner

cd atlassian-bitbucket-pipelines-runner/bin

./start.sh  --runtime linux-shell --workingDirectory ../temp &

**#Now Create File called bitbucket-pipelines.yml**

pipelines:
 branches:
   master:
   - step:
       name: Build and Test
       deployment: test
       runs-on:
         - self.hosted
         - linux.shell
         - devserver
       script:
         - pwd
         - whoami
         - sh /var/www/html/node_optom_backend/deploy.sh


**#Try & #Test**







