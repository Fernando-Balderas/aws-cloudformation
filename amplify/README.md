# Amplify

```bash
# load env variables
set -o allexport; source .env; set +o allexport
```

```bash
# list stacks
aws cloudformation describe-stacks

# create stack from file
aws cloudformation create-stack \
    --stack-name myamplifystack \
    --template-body file:////home/fbalderas/Projects/aws-cloudformation/amplify/amplify-app.yaml \
    --parameters ParameterKey=GitAccessToken,ParameterValue=$GIT_ACCESS_TOKEN ParameterKey=ApiUrl,ParameterValue=$API_URL ParameterKey=UserPoolClientId,ParameterValue=$USER_POOL_CLIENT_ID ParameterKey=UserPoolId,ParameterValue=$USER_POOL_ID

# trigger a build of a branch
aws amplify start-job --app-id d2vrj4nlh23jp7 --branch-name main --job-type RELEASE

# delete stack and remove resources
aws cloudformation delete-stack \
    --stack-name myamplifystack
```
