# README file (Helm take-home-test discussion):
In the bitbucket pipelines yaml file, following are addressed:
    - Using python-3.8 as the base image to start the docker container
    - Since this is a independent application, only one step is added in all stages.
    - Choose "caches" for all pip installation inorder to skip the reinstallation of the required packages for every pipeline run. This will save the packages in cache and hence reduces build time as well as in terms of being economical for bitbucket cloud usage.
    - For every pull-requests, the installation of required packages will be run and after successful installation, all the unit tests are executed to sanity check.
    - For 'master' branch, after the merge is successful, following steps are executed from script:
        > Installing all the package prerequisites for parlai
        > Run sample unit tests like 'TransformerRanker' to test all the packages are installed. Since all the unit-tests are executed at the pull-request level, we do not need to re-run again.
        > Setting up the ParlAI 'develop' evnvironment.
        > Validating the installation and testing to display 10 random examples from the SQuAD task.
    
Challenge:
    - Since this is the first time I am working with bitbucket pipeline, it was initally time consuming to understand the pipeline process.
    - I did not knew earlier that pipeline feature works only in BitBucket Cloud. I created an account, added the repo, create pipeline from template.
    
Dilemma:
    - Is it possible to run one step at default, connect to default container and execute parallel scripts?

