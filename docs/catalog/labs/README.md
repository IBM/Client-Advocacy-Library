# Catalog Automation

## Directory Structure

```text
+ catalog/
|- README.md
|- catalog.json
|---+ labs/
    |- <lab-name>.json
    |- <lab-name>.json
    |- etc
```

Contains the following:

* catalog.json file, main configuration file for catalog with `Content Groups` or `Squads` matching Github labels starting with `Squad : ` and `Learning Paths` matching Github labels starting with `Learning Path : `.
* labs directory, containing configuration files for individual labs, referencing details in the README.md of the respective Github repository or repository subdirectory. Branches, versions are maintained following Github standards.

### catalog.json

The catalog file below had two learning paths: `Application Modernization 1` and `Application Modernization 2`, with in order the labs it contains, referencing lab details in the relative file paths.

```json
{
    "ContentGroups" : [
        {
            "Cloud Native" : [
                {
                    "Application Modernization 1" : [
                        "labs/containers101.json", "labs/kube101.json", "labs/helm101.json", "labs/istio101.json", "labs/storage-lab1.json", "labs/kube-networking101.json", "labs/logging-monitoring101.json", "labs/jenkins101.json"
                    ],
                    "version": "0.1.0",
                    "last_updated": "2021-03-01"
                },
                {
                    "Application Modernization 2" : [
                        "labs/crw-odo.json", "labs/kube-config-management.json", "labs/scc-rbac-sa-openshift.json", "labs/vpcgen2.json", "labs/apic101.json", "labs/apache-kafka.json", "labs/operators-helm.json", "labs/cos-s3fs-fuse.json"
                    ]
                },
                {
                    "Unassigned" : [
                        "labs/new-lab.json"
                    ]
                }
            ],
            "Unassigned" : []
        }
    ]
}
```

### lab101.json

```json
{
    "title": "Container Storage",
    "duration": "60 minutes",
    "repo" : "https://github.com/IBM/docker101",
    "subdir": "docs/lab3"
}
```

## Templates

* content-new-lab-template.md
