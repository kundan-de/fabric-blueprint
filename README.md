# Fabric-Blueprint

The **Fabric-Blueprint** repository serves as the single source of truth for your Microsoft Fabric ecosystem. It manages the "Control Plane" of your data platform, ensuring that workspaces, lakehouses, and security configurations are deployed consistently across environments.

## Overview
This project uses a declarative YAML approach to define your Fabric environment. It bridges the gap between your desired state and the Microsoft Fabric API.

*   **Config-Driven:** All resources are defined in `config.yaml`.
*   **Idempotent:** Deployment scripts ensure resources exist without creating duplicates.
*   **GitOps Ready:** Designed to be triggered via CI/CD pipelines (GitHub Actions/Azure DevOps).

## Quick Start

1.  **Configure:** Define your environment in `config.yaml`:
```yaml
    workspaces:
      - name: "Marketing_Analytics"
        lakehouses: ["Raw_LH", "Gold_LH"]
    ```
2.  **Authenticate:** Set your Service Principal credentials as environment variables:
    * `TENANT_ID`
    * `CLIENT_ID`
    * `CLIENT_SECRET`
3.  **Deploy:** Run the provisioning script:
```bash
    python src/provisioner.py --env prod
    ```

## Project Structure
```text
.
├── config/              # Environment-specific YAML manifests
├── src/
│   ├── provisioner.py   # Main orchestration engine
│   └── auth.py          # Authentication handler
├── pyproject.toml     # Python dependencies
└── README.md
