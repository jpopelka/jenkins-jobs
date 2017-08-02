# How to update Jenkins jobs with jenkins-job-builder

Make changes to `jobs/template-fabric8-analytics.yml`. See documentation [here](https://docs.openstack.org/infra/jenkins-job-builder/definition.html) and [here](https://docs.openstack.org/infra/jenkins-job-builder/definition.html#modules).

## Install jenkins-job-builder

```bash
pip install -U jenkins-job-builder==2.0.0.0b2
```
Note you version 2.0.0.0b2 or newer.

## Get your Jenkins API token

Go to `<your-jenkins>/user/<username>/configure`

Find the "API Token" section and get your token.


## Configure jenkins-job-builder with your credentials

Edit `etc/jenkins_jobs.ini` and put your username (`user=`) and API token (`password=`) there.

## Run the tool

Test your changes first:
```bash
jenkins-jobs --conf etc/jenkins_jobs.ini test jobs/template-fabric8-analytics.yml
```

No exceptions and XML on stdout means everything's likely OK :)

Apply your changes:
```bash
jenkins-jobs --conf etc/jenkins_jobs.ini update jobs/template-fabric8-analytics.yml
```

