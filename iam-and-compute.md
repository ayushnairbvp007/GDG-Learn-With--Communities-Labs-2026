# Configure Service Accounts and IAM Roles for Google Cloud: Challenge Lab

## ID: ARC134

## 1. Global Setup (Run in Cloud Shell)

```bash
export PROJECT_ID=\$(gcloud config get-value project)
echo "Project ID: \$PROJECT_ID"
```

## 2. Task 2: Create a Service Account

```bash
gcloud iam service-accounts create devops \
--description="Devops service account" \
```
--display-name="devops"

## 3. Task 3: Grant IAM Permissions to Service Account

```bash
export PROJECT_ID=$(gcloud config get-value project)
```
SA="devops@${PROJECT_ID}.iam.gserviceaccount.com"

```bash
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member="serviceAccount:$SA" \
```
--role="roles/iam.serviceAccountUser"

```bash
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member="serviceAccount:$SA" \
```
--role="roles/compute.instanceAdmin"

## 4. Task 4: Create a Compute Instance with Service Account

```bash
gcloud compute instances create vm-2 \
--zone=us-east1-c \
--machine-type=e2-medium \
--service-account="devops@$(gcloud config get-value project).iam.gserviceaccount.com" \
```
--scopes=cloud-platform

# Grant instance admin role at the project level (or appropriate compute permissions as required)

```bash
gcloud projects add-iam-policy-binding $DEVSHELL_PROJECT_ID \
--member="serviceAccount:$SA" \
```
--role="roles/compute.instanceAdmin"

## 5. Task 5: Create a Custom Role Using a YAML File

```bash
cat << 'EOF' > role-definition.yaml
title: "Custom CloudSQL Role"
description: "Custom role with cloudsql instances connect and get permissions"
stage: "ALPHA"
includedPermissions:
- cloudsql.instances.connect
- cloudsql.instances.get
EOF
gcloud iam roles create customCloudSqlRole \
--project=$(gcloud config get-value project) \
```
--file=role-definition.yaml

## 6. Task 6 Step A: Create Service Account, Roles & VM (Cloud Shell)

## Task 6: Use the client libraries to access BigQuery from a service account

Create the second service account named bigquery-qwiklab:

```bash
gcloud iam service-accounts create bigquery-qwiklab \
--description="BigQuery Qwiklab service account" \
```
--display-name="bigquery-qwiklab"

Assign the BigQuery Data Viewer and BigQuery User roles to bigquery-qwiklab:

```bash
export BQ_SA="bigquery-qwiklab@${PROJECT_ID}.iam.gserviceaccount.com"
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member="serviceAccount:$BQ_SA" \
```
--role="roles/bigquery.dataViewer"

```bash
gcloud projects add-iam-policy-binding $PROJECT_ID \
--member="serviceAccount:$BQ_SA" \
```
--role="roles/bigquery.user"

Create the bigquery-instance VM attached to this new service account:

```bash
gcloud compute instances create bigquery-instance \
--zone=europe-west1-b \
--machine-type=e2-medium \
--service-account=$BQ_SA \
```
--scopes=https://www.googleapis.com/auth/cloud-platform

SSH into bigquery-instance to set up and run the Python script:

```bash
gcloud compute ssh bigquery-instance --zone=europe-west1-b
```
Once inside the VM terminal, install the necessary dependencies:

sudo apt-get update && sudo apt-get install -y python3-pip python3-pandas

```bash
pip3 install google-cloud-bigquery db-dtypes
```
Create and run the Python query script (make sure to replace YOUR_PROJECT_ID and YOUR_SERVICE_ACCOUNT with your actual values):

```bash
cat << 'EOF' > query.py
from google.auth import compute_engine
from google.cloud import bigquery
credentials = compute_engine.Credentials(
```
service_account_email='bigquery-qwiklab@' + 'qwiklabs-gcp-01-78c649fa98b7' + '.iam.gserviceaccount.com')

```bash
query = '''
SELECT name, SUM(number) as total_people
FROM `bigquery-public-data.usa_names.usa_1910_2013`
WHERE state = 'TX'
GROUP BY name, state
ORDER BY total_people DESC
LIMIT 20
'''
client = bigquery.Client(
```
project='qwiklabs-gcp-01-78c649fa98b7',

credentials=credentials)

```bash
print(client.query(query).to_dataframe())
EOF
```

## 7. Task 6 Step B: SSH into VM & Run Script (inside VM)

# 1. SSH into the VM

```bash
gcloud compute ssh bigquery-instance --zone=us-east1-c
```
# 2. Install python3-full and pip inside the VM

sudo apt-get update && sudo apt-get install -y python3-full python3-pip

# 3. Create and activate a Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```
# 4. Install BigQuery and Pandas libraries

```bash
pip install google-cloud-bigquery pandas google-auth
```
# 5. Create query.py

```bash
cat << 'EOF' > query.py
from google.auth import compute_engine
from google.cloud import bigquery
credentials = compute_engine.Credentials()
query = '''
SELECT name, SUM(number) as total_people
FROM `bigquery-public-data.usa_names.usa_1910_2013`
WHERE state = 'TX'
GROUP BY name, state
ORDER BY total_people DESC
LIMIT 20
'''
client = bigquery.Client(credentials=credentials)
print(client.query(query).to_dataframe())
EOF
```
# 6. Run the script!

```bash
python3 query.py
```

# The Basics of Google Cloud Compute: Challenge Lab

## ID: ARC120

## COMMAND 1:

```bash
export ZONE=
```

## COMMAND 2:

```bash
curl -LO raw.githubusercontent.com/prateekrajput08/Arcade-Google-Cloud-Labs/refs/heads/main/The%20Basics%20of%20Google%20Cloud%20Compute%3A%20Challenge%20Lab/TechCode.sh
sudo chmod +x TechCode.sh
./TechCode.sh
```
