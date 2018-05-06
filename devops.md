# DevOps

## Architecture

We are currently running a simple single instance in OpenShift.

We are looking into expanding this to multiple dynamically started and stopped Pods routed through a bungee proxy.

## Deployment

We continously deploy (CI/CD) the master branches of our main repos to our live Minecraft server. 

With great power comes great responsability! ;-)

## Worlds

Worlds are parts of Universes which we store on OpenShift (really Kubernetes) Persistent Volume Claims in this format:

    /universe/world/level.dat
    
For now, we manually upload locally existing worlds like this:

  1. oc new-app openjdk18-web-basic-s2i

  2. [use UI](https://github.com/openshift/origin/issues/10700) at `/browse/storage` to create a new Persistent Volume Claim
  
  3. oc volume dc/openjdk-app --add --mount-path /deployments/PV --claim-name=<the name you gave the new PVC above>

  4. oc get pods

  5. [oc rsync](https://docs.openshift.org/latest/dev_guide/copy_files_to_container.html) /some/local/dir/ openjdk-app-...:/deployments/PV

  6. Check if it worked:

    $ oc rsh dc/openjdk-app
    sh-4.2$ ls /deployments/PV/
    universe

  7. oc delete dc/openjdk-app

The Minecraft Server OpenShift Deployment Configuration then has storage added to mount such a volume at `/deployments/persistent`.

In the future, we may have web services and UI to allow end-users to do this themselves.
