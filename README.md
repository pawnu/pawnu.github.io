Following are some toolchains I have played around with to get a feel of how DevSecOps could be implemented in Cloud, Kubernetes, AppSec, and other delivery model.

- [Kubernetes-Native Tekton Security Pipeline](#kubernetes-native-tekton-security-pipeline)
- [Vulnerability Management Driven Pipeline](#vulnerability-management-driven-security-pipeline)
- [Container/Kubernetes Security Pipeline](#containerkubernetes-security-pipeline)
- [Python Jenkins Declarative Pipeline](#python-jenkins-declarative-pipeline)
- [JAVA AWS Cloud-Native Pipeline](#java-aws-cloud-native-pipeline)
- [JavaScript Azure-DevOps Pipeline](#javascript-azure-devops-pipeline)
- [REST API GCP GoCD Pipeline](#rest-api-gcp-gocd-pipeline)
- [Android/iOS App Security Pipeline](#androidios-app-security-pipeline)
- [Attack Tree SlackBot](#attack-tree-slackbot)

## Kubernetes-Native Tekton Security Pipeline

A DevSecOps pipeline living within Kubernetes Cluster as Tekton CI/CD, checking for Application Security, Container Security, Infrastructure as Code security, using opensource and free tools.

- CICD - `Tekton`
- Git Secret Check - `trufflehog`
- SCA - `safety`
- SAST - `bandit`
- DAST - `OWASP Zed Attack Proxy`
- IaC Scanner - `checkov`
- Container Vulnerability Analysis - `starboard trivy`
- Container Image storage - `Docker Hub`
- Database Dynamic Secrets - `Hashicorp Vault Database Engine`, `PostgreSQL`
- Pod Secret Injection - `Hashicorp Vault annotation + agent`
- Kubernetes resource deployment - `kubectl`, `helm`
- Kubernetes CIS benchmark - `starboard kube-bench`
- Kubernetes workload audit - `starboard polaris`
- Kubernetes penetration test - `starboard kube-hunter`
- Kubernetes Engine - `Minikube`
- Kubernetes nodes - `virtualbox driver`

![tektonpipeline](https://user-images.githubusercontent.com/11514346/111226740-7444de80-85d9-11eb-91b8-e6e308799919.PNG)

## Vulnerability Management Driven Security Pipeline
A vulnerability manager (DefectDojo) based pipeline for Python based project which comes with ASVS Standard to provide security test plan and requirements, integration of vulnerability data from 70+ tools, and slack integration for monitoring. 

**Toolchain**

- Planning - `OWASP ASVS`
- CI/CD - `Go CD` 
- secret-check - `trufflehog`
- SCA - `safety`
- SAST - `bandit`
- DAST - `nikto`
- Container Vulnerability Analysis - `trivy`
- Vulnerability Manager - `DefectDojo`
- Monitoring - `Slack`
- Environment - `AWS`

![gocd_pipeline](https://user-images.githubusercontent.com/11514346/84599383-8be41080-ae69-11ea-952c-51f2ad97f4eb.PNG)

## Container/Kubernetes Security Pipeline
DevSecOps pipeline for container based application deployed to GCP kubernetes cluster using GCP k8s and container solutions, and security tests with open source container solutions.

- CICD - `Jenkins`
- Git Secret Check - `trufflehog`
- Container image vulnerability analysis - `trivy`
- Container Image malware analysis - `clamav`
- Container Image storage - `Google Container Registry`
- Kubernetes Engine - `Google Kubernetes Engine`
- Kubernetes nodes - `Google Container-Optimized OS`
- Kubernetes setup - `gcloud`
- Kubernetes resource deployment - `kubectl`, `helm`
- Kubernetes CIS benchmark - `kube-bench`
- Kubernetes penetration test - `kube-hunter`
- Kubernetes runtime protection - `falco`
- Environment - `GCP`

![image](https://user-images.githubusercontent.com/11514346/80305685-35861a00-87b6-11ea-9a38-9930e7e8af6b.png)


## Python Jenkins Declarative Pipeline
DevSecOps pipeline for Python based project using Jenkins, Ansible, AWS, and open-source security tools and checks.

**Toolchain**
- CICD - `Jenkins`
- Orchestration - `Ansible Playbook`
- SCM - `Github`
- Secret check - `trufflehog`
- SCA - `safety`
- SAST - `bandit`
- Container Audit - `lynis`
- DAST - `nikto` for scans, `selenium-chrome` for grabbing session cookie
- Security Audit - `lynis`
- WAF - `modsecurity`, also configured as reverse proxy
- Environment - `AWS`

![pipeline](https://user-images.githubusercontent.com/11514346/71473164-e57a5500-27cd-11ea-97cb-3c25f0266407.JPG)

![psparch](https://user-images.githubusercontent.com/11514346/71579758-effe5c80-2af5-11ea-97ae-dd6c91b02312.PNG)

## JAVA AWS Cloud-Native Pipeline
DevSecOps pipeline for JAVA based project using AWS DevOps tools, AWS security tools, and some open source tools.

**Toolchain**
- CICD - `AWS CodePipeline`, `AWS CodeBuild`, `AWS CodeDeploy`
- IDE - `AWS Cloud9`
- Secret Check - `Talisman` for pre-commit hook, `trufflehog` checks secrets in pipeline
- SCM - `Github`
- Artifact repository - `AWS S3`
- SCA - `dependency-check`
- SAST - `findsecbugs`
- DAST - `OWASP ZAP`
- Compliance Scanning - `AWS Inspector`
- Threat Detection - `AWS GuardDuty`
- Security Advisor - `Security Hub`
- WAF - `AWS WAF`
- Environment - `AWS`

![AWS_Code_Pipeline](https://user-images.githubusercontent.com/11514346/73794262-f68c8d80-479f-11ea-93a4-c2a53bd2932c.png)


## JavaScript Azure-DevOps Pipeline
DevSecOps pipeline for React+Docker based project using Azure DevOps - Release Pipeline, Azure security solutions, and some open source tools.

**Toolchain**
- CICD - `Azure DevOps`, `Azure Release Pipeline`
- Secret Check - `trufflehog`
- SCM - `Github`
- SCA - `anchore` non-os scans
- SAST - `sonarqube community edition 7.9.2`
- DAST - `gauntlt` with `arachni`, `nmap` etc
- Host security - `Azure Security Center` including FIM, `Qualys` vulnerability scans 
- Container security - `anchore` full scan (os, non-os)
- Continious Compliance - `Azure security center` for PCI-DSS, ISO 27001 etc
- WAF - `Azure Application Gateway` with WAF rules
- DDoS protection - `Vnet` DDoS setting
- Azure account protection - `Azure Security Center` recommendation
- SIEM & SOAR - `Azure Sentinel`
- Environment - `Azure Cloud`

![azure_devops2](https://user-images.githubusercontent.com/11514346/73614730-9fe54f00-45f9-11ea-9428-9872ed98baf1.png)


## REST API GCP GoCD Pipeline

DevSecOps pipeline for Python flask REST API project using Go CD, Terraform, GCP, and open-source and cloud native security tools and checks. 

**Toolchain**
- CICD - `Go CD`
- Secret Check - `trufflehog`
- SCM - `Github`
- SCA - `safety`
- SAST - `bandit`
- DAST - `GCP Web Security Scanner`
- Container security - `lynis`
- Compliance - `terraform-compliance`
- Environment - `GCP`

Secret check, SCA, SAST, Container security, compliance checks have all been shifted left and are tested all within code level i.e. source code and Infrastructure as Code (IaC).

![GoCDPipelineView](https://user-images.githubusercontent.com/11514346/77017479-88c4ab80-6972-11ea-87c1-cd89039f0493.PNG)

![GoCDValueStreamMap](https://user-images.githubusercontent.com/11514346/77017476-86fae800-6972-11ea-834e-88b551d98003.PNG)


## Android/iOS App Security Pipeline
A DevSecOps pipeline for Android and iOS based project using Jenkins, android open-source security tools, and a security testing framework MobSF which does code/binary analysis, malware analysis, general and sensitive information check on iOS+Android apps. 

**Toolchain**
- CICD - `Jenkins`
- secret-check - `trufflehog`
- SAST - `findsecbugs`
- Vulnerability Analysis - `androbugs`
- Malware Analysis - `quark-engine`
- Malicious Behaviour Analysis - `androwarn`
- Application Vulnerability Analysis - `qark`
- APK composition analysis - `APKiD`
- Security Test - `MobSF` for iOS and Android
- Environment - `GCP`

For Android, MobSF also checks certificate strength, obfuscation techniques, anti reverse engineering, dangerous permission etc.

![pipeline](https://user-images.githubusercontent.com/11514346/78502893-592be680-775b-11ea-8d4a-f6b4653bbeef.PNG)


![iOSPipeline](https://user-images.githubusercontent.com/11514346/78502793-bd9a7600-775a-11ea-8f22-a5dc49cc3077.PNG)


## Attack Tree SlackBot
A simple bot that sits on AWS EC2 instance with Python Flask API, will create attack-tree-diagram using graphviz library when numbered list of attack is provided as input.

**Toolchain**

- ChatOps - `Slack`
- Diagram service - `Python` for code & logic, `graphviz` library for diagraming
- Artifact Repository - `AWS S3`
- Request API service - `Slack` Actions
- Response API server - `Python Flask`
- Bot client host - `Slack` 
- Bot server host - `AWS`

![slackbot](https://user-images.githubusercontent.com/11514346/73794522-8df1e080-47a0-11ea-8a62-6b646f72e334.PNG)



