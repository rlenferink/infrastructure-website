Title: Subversion and Git integration with JIRA tickets
slug: reference/committer/svngit2jira

Many projects use JIRA for managing tracking bugs, milestones, feature
requests and so on, and many of these projects keep track of which
commit affects which ticket. In order to make things even easier, we
have a service called svngit2jira, which integrates Subversion and Git
commits with JIRA tickets.


## How it works

The amount of work a committer has to do to achieve this integration is
very light; Simply mention a JIRA ticket in a commit, and the specific
JIRA ticket will receive an update indicating that a certain commit has
been made in reference to the ticket. As an example, you may want to
check out, for instance, [this CloudStack
ticket](https://issues.apache.org/jira/browse/CLOUDSTACK-1638) (just
scroll down a bit and you'll see the commit mentioned).

This service also plugs into the ReviewBoard instance if you use JIRA
ticket names there, as for example the CloudStack project does. General
use of the service

As explained, the most common scenario is simply mentioning a JIRA
ticket in your commit, and the JIRA ticket will be updated to reflect
your new commit. Some projects have this trigger set, so that it only
updates a ticket if the first sentence is the JIRA ticket number, but we
can tailor this to suit your project's needs.


## Getting set up for svngit2jira

Enabling the service for your project is as easy as creating a
[JIRA](https://issues.apache.org/jira/browse/INFRA) ticket with
Infrastructure. We'll need to know the following things in order to
proceed:

- Which project is interested in this service
- Is the project in agreement on using this? (please ensure this before requesting the feature, as it does tend to add quite a lot of new information to JIRA)
- What JIRA name does your project use? (for example, INFRA, GIRAPH etc)
- Do you use git or subversion
- How would you like commits to trigger an update of a JIRA ticket (this can be anything from the standard catch-all FOO-1234 trigger to more specific rules you thought of yourself)
- If you are using Git, are there any specific branches you'd like the service to ignore

## Source code

The source for this feature is freely available at [this location](https://svn.apache.org/repos/infra/infrastructure/trunk/projects/svngit2jira/).