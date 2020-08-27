<p style="align:center;">
    <img src="https://developers.google.com/open-source/gsoc/resources/downloads/GSoC-logo-horizontal.svg">
</p>

## Abhinav Bajpai | @abhinavbajpai2012 | CHAOSS | GSoC Work Product


#### About the Project & Technologies

Augur is a tool for collecting and measuring structured data about free (https://www.fsf.org/about/) and open source (FOSS) communities.

We gather trace data for a group of repositories, normalize it into our data model, and provide a variety of metrics about said data. The structure of our data model enables us to synthesize data across various platforms to provide meaningful context for meaningful questions about the way these communities evolve.

We are a CHAOSS project, and many of our metrics are implementations of the metrics defined by our awesome community. You can find more information about how to get involved (here)

### Phase-wise Contributions:

#### Phase 1:
Base worker was initally built to handle the Github APIs and workers. Changes were to be made to enable the base worker class to interact with the Gitlab API and Gitlab workers. 
I and Sai, who was a GSoC student along with me started refactoring the base worker to incorporate Gitlab API requests.
These the the following changes made by me:
- Added Gitlab Authorization
- Changed task status registration methods 
- Added Gitlab contributor querying method

[PRs](https://github.com/chaoss/augur/pull/753)

After the base worker refactoring, I moved to the development of Merge Request Worker. MR Worker holds the responsibility of collecting the data related to the Merge Requests of a project.
I the first phase the following collections methods were implemented:
- Query and store merge requests
- Query and store MR labels
- Query contributors (using worker_base)
- Query MR events
- Query MR comments/Notes

Out of 13 collection methods for 3 data models, by now 6 methods for 1 model were competed.

[PRs](https://github.com/chaoss/augur/pull/789)

#### Phase II: 
In the second phase the left out portion of the MR worker was competed. There were 7 more collection methods to be completed for 2 models.
Those were implemented and test were done with a few of the repositories.
Following were the collection methods implemented in this phase:
- MR assignees
- MR message_ref
- MR meta
- MR repo
- MR reviewers
- MR commits
- MR files

[PRs](https://github.com/chaoss/augur/pull/847)

#### Phase III:
There were some logical differences between how Github & Gitlab APIs consider and store the data:
1. Project can be owned by a group of people in Gitlab while in Github, there is always a unique repo owner basically the one who created the repo. Repo could be owned by an organization but the Github API values the repo creator and return the creator as the unique owner. Although Gitlab doesn't differentiate between the group of owners and the project creator, but we explicitly store the Gitlab project creator as the unique owner.
2. Gitlab API returns the email addresses of closed Gitlab accounts but they don't have a unique source id associated with them. But they have a login/username which is enough for our use-case.

These changes had to be taken care of as the collections logics were build considering only the Github API.
Along with that, minor bug fixes were done along with testing and documentation.


 ### Others
- [Blog Posts](https://medium.com/@abhinavbajpai)
