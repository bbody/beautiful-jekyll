---
layout: post
title: My experiences with CI/CD
subtitle: The team members who enjoys doing boring testing and deployments
tags: devops ci/cd productivity projects productivity
categories: devops
---

Often in my work, the CI/CD process has been handled by someone else and I've very rarely needed to peek behind the curtain. I think names like Jenkins and Travis are great for CI/CD tools, I tend to anthropomorphize them, thinking of them as team members. When explaining CI/CD to non-technical people I usually tell them to think of the CI/CD as another team member who is great at following orders and is happy to do it over and over again.

In much of my work I don't need to touch devops and I am content with this. I would not consider myself devops nor an expert on CI/CD but I have dabbled. In my personal projects, it can often be months between coding sessions and I found myself often trying to figure out my build process again and again...

After some contemplation, I realised that one of the biggest factors hindering my ability to work on projects outside of work is the need to get my head back into my previous context. So I spent time on my projects ensuring it had decent build tools to keep me moving fast then adding in automated testing to ensure I don't break code. This led me to being able to write a lot of code quickly without worrying about breaking or how to build/run/test/release code. Despite the initial time investment, I found these build tools have helped me a lot. The natural next step was to have it not run on my computer, it should be run on a CI/CD system.

As I have tried different technologies over different projects, I have tried to experiment with CI/CD as well. I would say I leveraged a lot of each CI for my various projects, but my experience is by no means in depth. Below are summaries of my experiences with different CI/CD tools.

## Jenkins

[Jenkins](https://jenkins.io/) was the first experience I had with CI/CD systems, everytime I had to change something I was intimidated.

- **Pros**
    - Mature tool and community
    - Someone has probably done what you are trying to do before
    - Open Source
    - A lot of plugins
    - Great for older languages
- **Cons**
    - Config's can be a little hard to read
    - Setup can be overwhelming

## Travis CI

[Travis CI](https://travis-ci.com) is the CI/CD where I really dipped my toes into the water. I really like it and would consider it the one I am most familiar with.
- **Pros**
    - Very easy to learn
    - Open Source
    - Can be self-hosted or use cloud instances
    - Databases are simple to use
    - Free plan decent
- **Cons**
    - Setup could be simplified with containerization paradigm
    - Have experienced some stability issues with cloud hosted instance

## Circle CI

[Circle CI](https://circleci.com/) definitely has great marketing but it is also a pretty good product. In a commercial setting, this is the tool I would probably use if repository is not hosted on GitLab. Understanding how to speed up build and time resources is very easy to handle.

- **Pros**
    - Great visualizations of different tasks
    - Uses containerization
    - I like how jobs and workflow are separated

- **Cons**
    - Free tier can be a little limiting
    - I get too many YouTube ads for it which rubs me the wrong way

## GitLab CI/CD

[GitLab CI/CD](https://docs.gitlab.com/ee/ci/) unlike the other tools listed here is actually something I have used commercially. I find it to be very similar to Circle CI in terms of config, not a bad thing. I do however feel their UI isn't as great. If the repository is hosted on GitLab, I would not hesitate to use GitLab CI/CD.

- **Pros**
    - Easily integrated with your Gitlab repository
    - Decent free plan
    - Can host own instances for the CI runner to use
    - Can easily run builds locally (Great for debugging)
- **Cons**
    - Need to use GitLab
    - UI can be sluggish
    - UI not as good as Circle CI

## AWS CodePipeline

I haven't actually heard much about [AWS CodePipeline](https://aws.amazon.com/codepipeline/) but recently I wrote a website which required Lambda and S3 hosting, so i figured there was an AWS CI/CD offering.

- **Pros**
    - Great if infrastructure hosted on AWS
    - Amazing for handling security all within AWS
    - Can use UI to design PipeLine for common features
    - Deployment to S3 was very straight forward
- **Cons**
    - I quickly ran through the free allowance on a simple project
    - Deploying assets to Lambda required scripting
    - It is AWS

## GitHub Actions

With GitLab having GitLab CI/CD and Bitbucket having Bamboo, it was no surprise that GitHub would eventually introduce its own CI/CD. [GitHub Actions](https://github.com/features/actions) also subscribes to the containerization paradigm.

- **Pros**
    - Easily integrated with your GitHub repository
    - Free tier is very generous
    - Great for basic stuff
    - Actions tab is right in with your repository
    - Can use GitHub's, your own or other's "Actions" to handle tasks e.g. checkout, setup Node version, etc.
- **Cons**
    - Very new product (still in beta as of writing)
    - Documentation outside of 1st party is still lacking
    - Jobs and workflow are integrated, can make configs a little difficult to understand if you need a high level summary
    - Need to use GitHub
    - [Easy to expose your private tokens](https://julienrenaux.fr/2019/12/20/github-actions-security-risk/)

## What do I use?

Despite trying out different tools, at the moment I would say I am quite happy with Travis and GitHub Actions. I like that Travis is very flexible and I always feel in control of my builds but it is also one of its downsides. Sometimes a containization approach does a lot of the boring stuff for you. Yes, I know Travis can user containers too but it isn't designed with that paradigm in mind. For much of my latest projects, I try to use GitHub Actions, it does basic stuff easily and with custom actions you could abstract a lot from your config file. If I am working with a repository on GitLab, I would probably use GitLab CI/CD. That being said I have no intention of changing my other project's CI/CD, it runs and as long as it keeps working they are fine. One of the beautiful things about CI/CD systems, set it and forget it.

## Next

Although I am happy with the CI/CD tools I currently use, if opportunity strikes I would like to try other tools. Some that have caught my eye have been:
- [CodeShip](https://codeship.com/)
- [Buildbot](https://buildbot.net/)
- [Buildkite](https://buildkite.com/)
- [Semaphore](https://semaphoreci.com/)