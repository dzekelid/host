---
swagger: "2.0"
x-collection-name: Bitbucket
x-complete: 1
info:
  title: Bitbucket
  description: code-against-the-bitbucket-api-to-automate-simple-tasks-embed-bitbucket-data-into-your-own-site-build-mobile-or-desktop-apps-or-even-add-custom-ui-addons-into-bitbucket-itself-using-the-connect-framework-
  termsOfService: https://www.atlassian.com/legal/customer-agreement
  contact:
    name: Bitbucket Support
    url: https://support.atlassian.com/bitbucket
    email: support@bitbucket.org
  version: 1.0.0
host: api.bitbucket.org
basePath: /2.0
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /repositories/{username}/{repo_slug}/pipelines_config/ssh/known_hosts/{known_host_uuid}:
    delete:
      summary: Delete Repositories Username Repo Slug Pipelines Config Ssh Known Hosts
        Known Host Uu
      description: Delete repositories username repo slug pipelines config ssh known
        hosts known host uu
      operationId: deleteRepositoriesUsernameRepoSlugPipelinesConfigSshKnownHostsKnownHostUu
      x-api-path-slug: repositoriesusernamerepo-slugpipelines-configsshknown-hostsknown-host-uuid-delete
      parameters:
      - in: path
        name: known_host_uuid
        description: The UUID of the known host to delete
      - in: path
        name: repo_slug
        description: The repository
      - in: path
        name: username
        description: The account
      responses:
        200:
          description: OK
      tags:
      - Repositories
      - Username
      - Repo
      - Slug
      - Pipelines
      - Config
      - Ssh
      - Known
      - Hosts
      - Known
      - Host
      - Uu
    get:
      summary: Get Repositories Username Repo Slug Pipelines Config Ssh Known Hosts
        Known Host Uu
      description: Get repositories username repo slug pipelines config ssh known
        hosts known host uu
      operationId: getRepositoriesUsernameRepoSlugPipelinesConfigSshKnownHostsKnownHostUu
      x-api-path-slug: repositoriesusernamerepo-slugpipelines-configsshknown-hostsknown-host-uuid-get
      parameters:
      - in: path
        name: known_host_uuid
        description: The UUID of the known host to retrieve
      - in: path
        name: repo_slug
        description: The repository
      - in: path
        name: username
        description: The account
      responses:
        200:
          description: OK
      tags:
      - Repositories
      - Username
      - Repo
      - Slug
      - Pipelines
      - Config
      - Ssh
      - Known
      - Hosts
      - Known
      - Host
      - Uu
    put:
      summary: Update Repositories Username Repo Slug Pipelines Config Ssh Known Hosts
        Known Host Uu
      description: Put repositories username repo slug pipelines config ssh known
        hosts known host uu
      operationId: putRepositoriesUsernameRepoSlugPipelinesConfigSshKnownHostsKnownHostUu
      x-api-path-slug: repositoriesusernamerepo-slugpipelines-configsshknown-hostsknown-host-uuid-put
      parameters:
      - in: path
        name: known_host_uuid
        description: The UUID of the known host to update
      - in: path
        name: repo_slug
        description: The repository
      - in: path
        name: username
        description: The account
      - in: body
        name: _body
        description: The updated known host
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Repositories
      - Username
      - Repo
      - Slug
      - Pipelines
      - Config
      - Ssh
      - Known
      - Hosts
      - Known
      - Host
      - Uu
---