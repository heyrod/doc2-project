## About the OI Self-Service repository
This repository contains JSON files that describe monitoring configuration of hosts. Here you can add and delete different types of hosts and update their monitoring configuration through OI Self-Service. For general information and help, refer to [Self-Service 2.0 User Guide](https://confluence.wolterskluwer.io/display/GPTH/Self-Service+2.0+User+Guide) in Confluence.

## How to use the repository
You cannot commit your code directly to the repository. Create your own fork of the repository and deliver your code through a pull request. Each pull request is validated by a Jenkins-based validator, and only then it is merged into the master branch. If there are errors in your code, the validator marks the pull request as failed and adds a comment explaining the reason of the failure. Refer to [Validation rules](https://confluence.wolterskluwer.io/display/GPTH/Validation+rules) to find out the meaning of error messages and learn the rules of [Working with the repository](https://confluence.wolterskluwer.io/display/GPTH/Working+with+the+repository).

If you need to configure automatic turnover of instances within the monitoring system, use the instructions described for [Automated workflow](https://confluence.wolterskluwer.io/display/GPTH/Automated+workflow).

## Helpful Links

* [Self-Service 2.0 User Guide](https://confluence.wolterskluwer.io/display/GPTH/Self-Service+2.0+User+Guide)
* [Notify User Guide](https://confluence.wolterskluwer.io/display/GPTH/Notify+User+Guide)
* [Grafana User Guide](https://confluence.wolterskluwer.io/display/GPTH/Grafana+User+Guide)
* [Monitoring Types Library](https://confluence.wolterskluwer.io/display/GOMT/Monitoring+types+library)
* [Alerts KB](https://confluence.wolterskluwer.io/display/GOMT/Alerts+KB)
* [JSON samples](https://confluence.wolterskluwer.io/display/GPTH/JSON+samples) 
* [How to use monitoring types?](https://confluence.wolterskluwer.io/display/GPTH/How+to+use+monitoring+types)
* [How to enable threshold overrides?](https://confluence.wolterskluwer.io/display/GPTH/How+to+enable+threshold+overrides)
* [How to configure CloudWatch alarms?](https://confluence.wolterskluwer.io/display/GPTH/How+to+configure+CloudWatch+alarms)
* [How to set different thresholds for logical drives?](https://confluence.wolterskluwer.io/display/GPTH/How+to+set+different+thresholds+for+logical+drives)
* [How to enable MySQL monitoring?](https://confluence.wolterskluwer.io/display/GPTH/How+to+enable+MySQL+monitoring)
* [How to run item commands?](https://confluence.wolterskluwer.io/display/GPTH/How+to+run+item+commands)
* [How to rename a Zabbix proxy server?](https://confluence.wolterskluwer.io/display/GPTH/How+to+rename+a+Zabbix+proxy+server)

## Frequently asked questions

#### 1. __How can I enable monitoring of a new server?__
First, you need to complete the prerequisites that are specific for each type of servers. They typically cover firewall or security group configuration, installation of a monitoring agent, and some other steps described in our guides. Then you create a JSON file with monitoring configuration of your server and commit it to this repository from your fork through a pull request. For a more detailed workflow, refer to the instructions for [Adding a new host](https://confluence.wolterskluwer.io/display/GPTH/Adding+new+hosts) in Confluence.

#### 2. __Why can't I see metrics from the host that I have recently added through OI Self-Service?__

If you cannot see data from your host in Grafana, it may be caused by misconfiguration of the Zabbix agent or JMX interface on the host. For troubleshooting, go to the [Hosts by proxy dashboard in Grafana](https://grafana.wkgpooi.net/d/000000084/zabbix-hosts-by-proxy?orgId=1), select your Zabbix proxy server in the drop-down list, and search for the host name. Check out any interface connection errors reported for the host. To find out the reason of errors, see the description of [Connection errors](https://confluence.wolterskluwer.io/display/GPTH/Connection+errors).

#### 3. __Why do I not receive alerts for the host that I have recently added through OI Self-Service?__
If you do not receive alert notifications from the host that you have recently added through OI Self-Service but you can see alerts from the host in Grafana, the reason is that you are not subscribed to notifications.
This may happen if:
(a) You have added the host to the group, for which you have no active subscription, or
(b) You have created a new group under the parent group, for which you have no active subscription, or
(c) You have created a new root group, under which all other groups and hosts have no subscriptions yet.

Go to [Notify](https://notify.wkgpooi.net), check out your active subscriptions, and subscribe to alert notifications if required (see how you can do it in [Subscription Manager](https://confluence.wolterskluwer.io/display/GPTH/Managing+your+subscription).


#### 4. __Why can't I find in Notify the host that I have recently added through OI Self-Service?__
If you have added a new host to monitoring through OI Self-Service but cannot find it in Notify, you just need to wait more. Notify syncs with Zabbix every 30 minutes and then updates its database. Once the sync is done, you will see the host in Notify and be able to apply silent mode or change the alert subscription details.

#### 5. __What are pseudo-hosts?__
To put it simple, [pseudo-hosts](https://confluence.wolterskluwer.io/display/GPTH/Pseudo-hosts) are required to enable monitoring or handling of some specific things with Zabbix. We call them pseudo-hosts because they are neither servers nor applications. But they also have their monitoring configuration files in this repository and can be added and removed through OI Self-Service. For example, we already use pseudo-hosts for handling SMART tests, Mail Trackers, Elasticsearch queries, CloudWatch alarms, and  many other things, the number of which is growing.

#### 6. __My pull request was not merged because of a conflict. How can I fix it?__
This often happens if your fork has diverged from the upstream repository, and your pull request cannot be merged because, for example, the target file does not exist any more in the upstream repository. A merge conflict may also happen if some file has been changed both in the source branch and the destination branch. In this situation, git does not know what change to accept.
To resolve the conflict, sync your fork with the upstream repository manually. Depending on the synchronization strategy chosen by you (merge, discard, or rebase), your pull request then will be either merged automatically or pushed with a new commit. For more information, see [Resolving merge conflicts](https://confluence.wolterskluwer.io/display/GPTH/Resolving+merge+conflicts).

#### 7. __Where can I ask for help with OI Self-Service?__
Please send your requests to __gpo-ops-platform@wolterskluwer.com__ or post your question at the [General Feedback](https://confluence.wolterskluwer.io/display/GPTH/General+Feedback) page in Confluence. For more information about the request workflow, see [OI Work Procedures](https://confluence.wolterskluwer.io/display/GPTH/OI+Work+Procedures).
