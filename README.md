# Pull Request FAQs

A GitHub Workflow that automatically answers the following questions on closed/merged Pull Requests.

1. How long was PR open?

2. Who contributed to the PR?

3. What files changed in the PR?

4. How many lines of code changed in the PR?

# Workflow

The following highlights how this workflow works.

1. When a pull request is closed, the workflow is started.
2. The workflow downloads the repo using the GitHub Action [actions/checkout@v2](https://github.com/actions/checkout)
3. The workflow uses the GitHub GraphQL API using the template query to get data on the pull request using the GitHub Action [helaili/github-graphql-action@2.0.1](https://github.com/helaili/github-graphql-action)
4. The workflow saves the output as a JSON file
5. The workflow uses the [jannekem/run-python-script-action@v1](https://github.com/jannekem/run-python-script-action) to parse the JSON file to set answers to the questions as environment variables
6. The workflow uses the [chuhlomin/render-template@v1.2](https://github.com/chuhlomin/render-template) to set the answers into the PRFAQs template 
7. The workflow uses the [peter-evans/create-or-update-comment@v1](https://github.com/peter-evans/create-or-update-comment) to post the answers as a comment on the Pull Request 

## Example

The following image is an example from [here](https://github.com/banjtheman/prfaq_action/pull/34#issuecomment-964757256)  

![image](https://user-images.githubusercontent.com/696254/141141700-db820032-b977-4306-b811-c1dc6135dd7d.png)
