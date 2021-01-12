---
title: "Excluding Specific Logs From a Particular Pod in Fluentd"
date: 2021-01-12T18:09:24+05:30
tags: [
    "kubernetes",
    "fluentd",
    "logging",
]
categories: [
    "kubernetes",
    "logging"
]
draft: false
---

#### Problem:
I want to exclude these noisy logs coming from activemq pod.
```
kubernetes-cluster-logging $ kubectl logs activemq-79bd55f9c-jdtqf --tail 10 -f
 WARN | Transport Connection to: tcp://172.29.108.66:37302 failed: java.io.EOFException
 WARN | Transport Connection to: tcp://172.29.108.66:37366 failed: java.io.EOFException
 WARN | Transport Connection to: tcp://172.29.108.66:37518 failed: java.io.EOFException
 WARN | Transport Connection to: tcp://172.29.108.66:37582 failed: java.io.EOFException
```

#### Solution:
- Create regex pattern for your log line that need to be excluded.
- Use [kubernetes_metadata filter](https://github.com/fabric8io/fluent-plugin-kubernetes_metadata_filter) to enrich logs with kubernetes metadata.
- Use `kubernetes.container_name` tag to select a specific container. Also there are other tags to select specific pod, namespace and so on.
- Use `log` tag to capture a specific log line with the help of regex pattern.
- Use fluentd `exclude` filter with `and` operator to exclude particular log line from specific container.
```
# Enrich logs with kubernetes metadata
<filter  cluster.**>
  @type  kubernetes_metadata
</filter>

# Exclude noisy logs of activemq container
<filter kubernetes.**>
  @type grep
  <and>
    <exclude>
      key $.kubernetes.container_name
      pattern ^activemq$
    </exclude>
    <exclude>
      key $.log
      pattern ^WARN | Transport Connection to: tcp:\/\/\b(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?):\d{1,5}\b failed: java.io.EOFException$
    </exclude>
  </and>
</filter>
```

#### References:
https://github.com/fluent/fluentd/issues/1858 (`regex` or `exclude` filter need additional `and` filter to assert multiple conditions of a specific log line in a specific container)

