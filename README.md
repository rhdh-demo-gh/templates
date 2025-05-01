# Software Templates

A set of sample software templates.

# 🚀 Setting Up Your Fork of the Red Hat Developer Hub (RHDH) Software Template

This guide walks you through the process of forking and customizing the software template to align with your organization's setup, with a focus on **Red Hat Developer Hub (RHDH)** integration, Backstage metadata, and deployment configurations.

---

## 1️⃣ **Fork the Template Repository**

1. Navigate to the **GitHub repository**:  
   👉 [https://github.com/rhdh-demo-gh/templates.git](https://github.com/rhdh-demo-gh/templates.git)
2. Click the **Fork** button (top-right corner).
3. Choose your **GitHub organization** or personal account as the fork destination.
4. Clone your forked repository:
   ```bash
   git clone https://github.com/<your-org-id>/templates.git
   cd templates
   ```

---

## 2️⃣ **Update Backstage Metadata for RHDH**

Red Hat Developer Hub (RHDH) uses **Backstage** for software cataloging and discovery. Ensure the `catalog-info.yaml` file under your application directory is correctly configured for RHDH.

- Locate `catalog-info.yaml` under the relevant application directory (e.g., `your-app/skeleton/`).
- Update the **source location** to point to your forked repository:
  ```yaml
  backstage.io/source-location: url:https://github.com/<your-org-id>/${{ values.name }}
  ```
  Replace `<your-org-id>` with your **GitHub organization ID**.

This step ensures that your service is correctly registered within **Red Hat Developer Hub**.

---

## 3️⃣ **Update Repository URLs**

Modify `template.yaml` under the `deploy-component/` directory to reference your forked repository:
```yaml
repoUrl: github.com?repo=<your-repo-name>&owner=<your-org-id>
```
Replace:
- `<your-org-id>` with your **GitHub organization ID**.
- `<your-repo-name>` with the **name of your repository**.

Also, update `template.yaml` under your **application folder** to ensure it uses your organization's repository URL.

---

## 4️⃣ **Ensure Correct Namespace for OpenShift GitOps**

Since **RHDH is designed to work seamlessly with OpenShift**, ensure that your deployment configuration is correct.

In `template.yaml` under `deployment-yaml/`, update the namespace:
```yaml
namespace: openshift-gitops
```
This ensures that deployments align with **OpenShift GitOps**, the recommended deployment method for **RHDH software templates**.

---

## 5️⃣ **Customize Helm Chart Metadata**

Modify `chart.yaml` in both `production/` and `deployment/` directories:
- **Application Name** → Update it to match your actual service name.
- **Description** → Provide a relevant description.

Additionally, ensure `values.yaml` is updated with your template name:
- Locate `values.yaml` in the relevant folder.
- Replace the default **base template name** with your **custom software template name**.

---

## 6️⃣ **Check CI/CD Pipeline Configuration**

Verify that the GitHub Actions workflow in `.github/workflows/` is correctly configured:
- If your template contains `build.yaml` or `build-and-push.yaml`, ensure it references your forked repository.
- Update any image repository paths if required.

Since RHDH integrates well with CI/CD, ensure that pipelines are configured to automatically trigger deployments to OpenShift.

---

## ✅ Final Checklist

✔ **Fork the repository** and clone your version  
✔ **Update `catalog-info.yaml`** with the correct Backstage source location for RHDH  
✔ **Modify `repoUrl`** in `deploy-component/template.yaml`  
✔ **Update `repoURL`** in your application’s `template.yaml`  
✔ **Set `namespace: openshift-gitops`** in deployment configurations  
✔ **Update `chart.yaml` and `values.yaml`** with application details  
✔ **Verify `.github/workflows/` pipeline setup for CI/CD integration**  

🔹 **Once these steps are complete, your software template will be ready for use in Red Hat Developer Hub!** 🚀



