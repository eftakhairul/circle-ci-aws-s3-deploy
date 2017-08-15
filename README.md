# Continous Deploy The Static Site on AWS S3 with Circle CI


### Tutorial link
link: https://eftakhairul.com/automate-static-website-deployment-on-aws-s3-using-circleci/


### Circle CI config file: circle.yml

```sh
dependencies:
    override:
        - sudo pip install awscli
test:
  override:
    - echo "test"
    
deployment:
  prod:
    branch: master
    commands:
      - aws s3 sync /home/ubuntu/circle-ci-aws-s3-deploy s3://circlecis3deploy --region us-east-1

```