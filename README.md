# ITI-final-project
Deploy a Python web application in a GKE private cluster using by CI/CD Pipeline in GCP
 
 
 ### Build Infrastructure using Terrafrom 
 - terraform init 
 - terraform apply
 
 ### Connect to private vm
 - `gcloud compute ssh --zone "us-central1-a" "private-vm"  --tunnel-through-iap --project "abdelrahmanadel-project2"`
 - install docker 
 - install gcloud
 - install kubectl
 - connect to gcloud using `gcloud auth login`
 - install gke-gcloud-auth-plugin ` gcloud install gke-gcloud-auth-plugin`
 - Configure Docker with GCR (google container registery) `gcloud auth configure-docker`
 - Dockerize the jenkins image `docker build . -t gcr.io/abdelrahmanadel-project2/new-jenkins:v1.0`
 - push image to gcr `docker push gcr.io/abdelrahmanadel-project2/new-jenkins:v1.0`
 
 
 ### Connect to private GKE-cluster through private vm 
 - `gcloud container clusters get-credentials private-cluster --zone us-central1-c --project abdelrahmanadel-project2`
 - apply deployment files in (jenkins-k8s-deployment folder) `kubectl apply -f <definition-file.yml> --namespace jenkins`
 
 ## get inside jenkins pod 
 - `kubectl exec -it <pod-name> --namespace jenkins bash`
 
 ## login to jenkins using the admin password stored in /var/lib/jenkins/secrets/initialAdminPassword
 
 ## create a pipeline for this [python app](https://github.com/AbdelrahmanAdelTaha/pyflask-app-example) using the Jenkinsfile 
