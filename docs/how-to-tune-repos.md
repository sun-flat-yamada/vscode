# How to tune repository - リポジトリの整備方法

## Directory Structure

Best Practice : Directory Structure
https://softwareengineering.stackexchange.com/a/392461


## Pull Request Template の作成方法

### Sample

https://github.com/stevemao/github-issue-templates
https://embeddedartistry.com/blog/2017/08/04/a-github-pull-request-template-for-your-projects/


### Azure DevOps の場合

ref.
https://docs.microsoft.com/en-us/azure/devops/repos/git/pull-request-templates?view=azure-devops

Azure DevOps の場合は、リポジトリRootにある以下ディレクトリに、`pull_request_template.md` か `pull_request_template.txt` として置けば自動的に引用される。

- .azuredevops
- .vsts
- docs
- (root directory of repos)

`dev`や`feature`といった特定branchで場合分けしたい場合や、Pull Request作成ページで追加のTemplateを挿入したい場合は、上記同様のディレクトリ階層に以下の様な配置をすれば良い。

- docs/pull-request-template/branches/dev.md
- docs/pull-request-template/branches/feature.md
- docs/pull-request-template/check-list.md


### GitHubの場合

仕組みはほぼ同じ。

- .github
- docs
- (root directory of repos)
