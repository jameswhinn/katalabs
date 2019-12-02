Out of the box, Helm has a fixed list of known repositories that host the most common charts you may add to Kubernetes. See the current list of public repos.

``helm repo list``{{execute}}

Within these repos are stable and incubating charts. 

The stable chart count is consistently increasing with the maturing Kubernetes ecosystem. There are a bunch of common charts that, as a Kubernetes developer, you may want to leverage.

``helm search postgres``{{execute}}

``helm search sonarqube``{{execute}}

``helm search rabbitmq``{{execute}}

``helm search kafka``{{execute}}

The list is long.

``helm search stable | sed -E "s/(.{27}).*$/\1/"``{{execute}}

Each chart is backed with a GitHub repo, a readme and a team of people that are subject matter experts in forming these opinionated charts. As an example, take a look as the Minio chart source and scan the README to learn how this chart can be installed and configured.

There is also the public [Helm Hub](https://hub.helm.sh/)