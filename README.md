# Continous Deploy The Static Site on AWS S3 with Circle CI


### Tutorial link
link: https://eftakhairul.com/automate-static-website-deployment-on-aws-s3-using-circleci/


### Circle CI config file: circle.yml

```sh
version: 2
jobs:
  build:
    docker:
      - image: circleci/python:3.6.3

    working_directory: ~/circle-ci-aws-s3-deploy

    steps:
      - checkout

      - run:
          name: Install AWS CLI
          command: pip install awscli --upgrade --user

      - run:
          name: s3 deploy
          command: ~/.local/bin/aws s3 sync --delete --acl public-read ~/circle-ci-aws-s3-deploy s3://circlecis3deploy --exclude ".git/*" --region us-east-1

```