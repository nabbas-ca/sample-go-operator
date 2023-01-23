# sample-go-operator
Sample go operator to install a product. Used to demonstrate best practices for unit testing

# Respository Initilization commands

```
operator-sdk init --domain sample.com --repo github.com/nabbas-ca/sample-go-operator --project-version=3
operator-sdk create api --group kafka-wrapper --version v1alpha1 --kind KafkaWrapper --resource --controller
operator-sdk create webhook  --group kafka-wrapper  --kind KafkaWrapper --version v1alpha1 --defaulting --programmatic-validation
```

# Unit testing Philosophy 

1. All methods should be tested in a test file in the same folder, with _test addition. So as to keep unit test code as close to the method/package we are unit testing

1. Methods that don't need k8s client, should be tested in a native golang way, preferred using table testing

1. Methods that need k8s client, should be tested in Ginkgo way, so that envtest is initialized. 