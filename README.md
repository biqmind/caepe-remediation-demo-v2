# caepe-remediation-demo-v2

A manifests application for demonstrating CAEPE workload remediation on a Pod.

`manifests/pod-image-typo.yaml` deploys a bare Pod whose image is misspelled
(`ngnix:1.27-alpine` instead of `nginx:1.27-alpine`), so it stays in
`ImagePullBackOff`.

## Using it

1. Register this repository in CAEPE.
2. Create a **Manifest** application from it with folder `manifests`, any
   namespace.
3. Deploy the application to a cluster.
4. Run a workload scan on that cluster. The pod is reported as unable to pull
   its image, with steps that name `nginx:1.27-alpine`.
5. Trigger the workload remediation. The image is changed in place, the pod
   starts, and the run is recorded in the audit log.

To run the demo again, delete the deployment and redeploy the application.
