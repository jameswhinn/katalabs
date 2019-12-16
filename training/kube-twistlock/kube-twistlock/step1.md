Before deploying Prisma Cloud to our K8s cluster, we must first prepare our enviornment. In this step, we will configure the project and pull required docker images to our image cache ready for installation in step 2. 



## Download Artifacts

Now that our project is created, let's import the neccessary artifacts we need to proceed with our Prisma deployment. Go to the [releases page](https://docs.twistlock.com/docs/19.11/download/releases.html) and login with your subscriptions token. Copy the download link for the latest release to your clipboard

![alt text](https://raw.githubusercontent.com/jameswhinn/katalabs/master/twistlock-openshift/assets/tlrel.png "Releases")

Download the release tarball to your cluster controller:

`wget <LINK_TO_CURRENT_RECOMMENDED_RELEASE_LINK>`

Unpack the release tarball:

`mkdir twistlock`{{execute}}

`tar xvzf prisma_cloud_compute_edition_<VERSION>.tar.gz -C twistlock/`{{execute}}


`./linux/twistcli console export kubernetes --registry-token <REGISTRY_TOKEN> --persistent-volume-storage 10Gi --persistent-volume-labels "app-volume=twistlock-console" --service-type LoadBalancer`{{execute}} 

