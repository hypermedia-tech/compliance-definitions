# Security Standards & Attestations

This repository contains machine-readable security standards and attestation schemas for our build and deployment pipelines. These standards enable automated compliance verification and supply chain security through CycloneDX attestations.

If you need help implementing these standards or building secure CI/CD pipelines [please contact us](https://www.hypermedia.tech/company/contact).

## Quick Navigation

### Standards (Requirements)

Security requirements that define what must be achieved:

- **[Build Provenance v1](./standards/build-provenance/v1.json)**  
  Requirements for establishing verifiable provenance of container image builds.  
  Individual requirements are addressable via fragment identifiers (e.g., `v1.json#github-actions-build`)

- **[Static Analysis v1](./standards/static-analysis/v1.json)**  
  Requirements for static application security testing (SAST) of containerized applications.

- **[Catalog Approval v1](./standards/catalog-approval/v1.json)**  
  Requirements for human approval for advancing protected environments of containerized applications.

- **[Container Vulnerability Scan v1](./standards/container-vulnerability-scan/v1.json)**  
  Requirements for vulnerability scans of containerized applications.


### Attestation Schemas

JSON schemas that validate attestations generated in CI/CD pipelines:

- **[Build Provenance Attestation v1](./attestations/build-provenance/v1.json)**  
  Schema for build provenance attestations in CycloneDX format.

- **[Static Analysis Attestation v1](./attestations/static-analysis/v1.json)**  
  Schema for static application security testing attestations in CycloneDX format.

- **[Catalog Approval Attestation v1](./attestations/catalog-approval/v1.json)**  
  Schema for human catalog approval attestations in CycloneDX format.

- **[Container Vulnerability Scan v1](./attestations/container-vulnerability-scan/v1.json)**  
  Schema for vulnerability scan attestations in CycloneDX format.


## How It Works

1. **Standards** define security requirements with unique identifiers
2. **CI/CD pipelines** generate attestations that reference these standards via URLs
3. **Attestation schemas** validate the structure and content of generated attestations
4. **Cosign** cryptographically signs and attaches attestations to container images
5. **Deployment policies** verify attestations before allowing deployment

## Architecture

Standards and attestations follow REST principles:
- Each requirement is addressable via URI (e.g., `https://sec.hypermedia.au/standards/build-provenance/v1#github-actions-build`)
- Attestations link to requirements using these URIs
- Conformance scores (0.0 to 1.0) indicate how well requirements are met

![hypermedia tech logo](assets/images/hypermediatech-default.webp)