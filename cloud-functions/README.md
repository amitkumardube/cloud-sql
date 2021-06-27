# Cloud Functions

## how to use this code?
* The code needs to be supplied as source.
* The calling function is CloudFunctions.
* This is HTTP type function without any authentication required. Check this [page](https://cloud.google.com/functions/docs/securing/managing-access-iam#allowing_unauthenticated_http_function_invocation) to read about the configuration needed for unauthenticated functions.
* At this stage, the access to function will be available through test function feature in cloud console. If you need to access function from browser, please read the next point.
* After configuration is done, the unauthenticated access should be allowed for everyone to access the function from browser. Reference [here](https://cloud.google.com/functions/docs/securing/managing-access-iam#after_deployment).
* Please note that unauthenticated access to function can be restricted using organization policy as described [here](https://cloud.google.com/functions/docs/securing/managing-access-iam#domain_restricted_sharing).

## How to do authenticated HTTP call?
* The HTTP authentication are bit tricky as the request can come from any source ie: developer , any tool , service , tester etc.
* In order access the function the invoker must have a role called `Cloud Functions Invoker` to call the function. Ref [here] (https://cloud.google.com/functions/docs/securing/authenticating#authenticating_developer_testing).
