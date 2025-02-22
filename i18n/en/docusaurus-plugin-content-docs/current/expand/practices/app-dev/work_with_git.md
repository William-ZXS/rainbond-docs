---
title: Integrate Git repositories with rapid deployment components
description: This best practice explains Rainbond's integration of Git warehouse rapid deployment components, which is suitable for developers and application operators.
---

This document is suitable for application operation and maintenance personnel1 who use and GitLab systems **the same time.

This document is suitable for the scenario：Through the demonstration use case, understand how rainbond connects with GitLab for OAuth, and realize the rapid deployment of projects in GitLab and the use of Webhook to achieve automatic construction

### Preconditions

- If the existing GitLab private repository has not been deployed, you can refer to the following section **GitLab Quick Deployment**to deploy it

### Steps

GitLab can be deployed directly into your Rainbond environment through one-click installation from the App Market.

#### GitLab Rapid Deployment

- Install the GitLab app

  ![image-20200515143803028](https://tva1.sinaimg.cn/large/007S8ZIlly1get4lviy8jj30zl0hg78d.jpg)

- running result

  ![image-20200515164633334](https://tva1.sinaimg.cn/large/007S8ZIlly1get8bkft3jj31ml0u0q5u.jpg)

#### Connect to GitLab-type OAuth

This section will configure Rainbond to connect to GitLab type OAuth

- **Configure Applications**

  Go to User Settings → Applications

| option name  | Fill in the content                                  | illustrate                                                                                                                                                                                                                                     |
| ------------ | ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name         | Rainbond                                             | Fill in the custom Application name                                                                                                                                                                                                            |
| Redirect URI | https://goodrain.goodrain.com/console/oauth/redirect | The fallback path is used to receive the credentials returned by the third-party platform. The public cloud format is https://xxx.goodrain.com/console/oauth/redirect The private deployment format is https://IP:7070/console/oauth /redirect |
| Scopes       | api, read_user, read_repository                    | GitLab permission settings, you need to open api, read_user, read_repository                                                                                                                                                                 |

- Rainbond Platform Certification

  Enter Rainbond Homepage Enterprise View→ Settings→ OAuth Interconnection Service→ View Settings→ Add

| option name                 | Fill in the content               | illustrate                                                             |
| --------------------------- | --------------------------------- | ---------------------------------------------------------------------- |
| OAuth type                  | gitlab                            | Oauth type for authentication                                          |
| OAuth type                  | Custom (GitLab-Demo)              | Fill in the custom Oauth service name                                  |
| service address             | https://rainbond.gitlab/          | GitLab service access address                                          |
| Client ID                   | Fill in with specific information | Application ID generated by GitLab                                     |
| client secret               | Fill in with specific information | Application Secret generated by GitLab                                 |
| Platform access domain name | Use default fill                  | The access address used for the bounce back after OAuth authentication |

- OAuth authentication

  Enter Rainbond Homepage Enterprise View → Personal Center → OAuth Account Binding → Corresponding Account → Go to Authentication

#### Dock GitLab repository and complete automatic build

- Create a GitLab project with the following content

  ![image-20200518113119649](https://tva1.sinaimg.cn/large/007S8ZIlly1gewg2hhicxj31le080dgp.jpg)

- When deploying Rainbond using privatization, you need to configure GItLab to allow sending webhook requests to the local network

  Go to Admin area → settings → NetWork → Outbound requests

  Check the Allow requests to the local network from hooks and services option

- Build from source with Rainbond

  Enter the Rainbond team view → Add → Create components based on source code → Corresponding Gitlab project → Corresponding source code project → Create component

  ![image-20200518112657470](https://tva1.sinaimg.cn/large/007S8ZIlly1gewfxy3sbrj30xn08ujta.jpg)

  Go to the build page and select configure

  ![image-20200519142235426](https://tva1.sinaimg.cn/large/007S8ZIlly1gexqn1b7laj30wc09wdi4.jpg)

  Visit the performance display

  ![image-20200518114603719](https://tva1.sinaimg.cn/large/007S8ZIlly1gewghtmy3uj30xc044dge.jpg)

- Webhook automatically builds presentations

  Modify the index.html file of the GitLab rainbond-test project, and add the keyword @deploy to the Commit information when submitting

  ![image-20200518132824057](https://tva1.sinaimg.cn/large/007S8ZIlly1gewjgawobgj31l208oaaz.jpg)

  Automatic update effect display

  ![image-20200518133118625](https://tva1.sinaimg.cn/large/007S8ZIlly1gewjjc0vngj30zh0giwgt.jpg)

  Visit the performance display

  ![image-20200518132745969](https://tva1.sinaimg.cn/large/007S8ZIlly1gewjfn43hwj30v804adgx.jpg)
