# Clerk-API-Wrapper Helm Chart: Deployment Guide

<img src=cover.png>

## Overview

The **Clerk-API-Wrapper Helm Chart** simplifies the deployment of the Clerk-API-Wrapper application using Helm. This guide outlines the steps to package, index, and deploy the application efficiently.

### Prerequisites

Before proceeding, ensure the following tools are installed:

- **Helm**: For managing Kubernetes packages.
- **Git**: For version control.
- **Kubernetes CLI (kubectl)**: For interacting with the Kubernetes cluster.

---

## Steps for Deployment

### 1. Create Helm Package

1. Navigate to the `mychart` directory.
2. Run the following command to package the chart:

   ```sh
   helm package . --destination ../ --version 1.0.0
   ```

   > This creates the `clerk-app-1.0.0.tgz` file in the parent directory.

---

### 2. Generate Helm Repository Index

1. Navigate to the root directory of the repository.
2. Generate the `index.yaml` file by running:

   ```sh
   helm repo index . --url https://johnbedeir.github.io/clerk-app-chart
   ```

3. Commit the changes to your GitHub repository to update the hosted Helm repository.

---

### 3. Deploy Application via Helm Chart

1. Add the Helm repository:

   ```sh
   helm repo add clerk-app https://johnbedeir.github.io/clerk-app-chart
   ```

2. Update the repository to fetch the latest charts:

   ```sh
   helm repo update
   ```

3. Install the Clerk-API-Wrapper application:

   ```sh
   helm install clerk-app clerk-app/clerk-app --namespace dev-clerk-app
   ```

   > Ensure the `dev-clerk-app` namespace exists before running the command.
