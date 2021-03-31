# Catalog Automation

create-catalog.go --includeCG "Data and AI","Cloud Native" --name catalog-rbs 

catalog-rbs.md


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

## Notes

Considerations:

* Require a repo to be refactored and comply to directory structure, e.g. https://github.com/IBM/kubernetes-networking/tree/master/docs is too granular with a root level files per segment, https://github.ibm.com/IBM-DEG/ClientAdvocacy/issues/1303
* Other directories like this https://github.com/IBM/kube101/tree/master/docs do not easily let themselver be refactored, cause they're so self-contained at repo level.
* Looking at https://github.com/IBM/jenkins101 with lab-01 and lab-02, require a short description. Where should a summary/description of the lab be pulled from? Require a file in the repo? 
* Require a lab config file in repo instead of in this `catalog/labs` directory?
* What to do with unlinked workshops that are added to a Learning Path but which are TBD or unknown what URL they are located at? E.g. AppMod2 "API Management, Documentation and Security with APIC", "Message Streams with Apache Kafka"
* The operators labs dont have a subdir but have a single MD file
* This repo has a Istio101 which consists of a sub-selection of the root level markdown files: https://github.com/IBM/istio101/tree/master/docs

    ```yaml
    {
        "title": "Istio 101",
        "duration": "60 minutes",
        "repo" : "https://github.com/IBM/istio101",
        "subdir": "docs/mtls",
        "sections": [
            { "mTLS": "docs/mtls" },
            { "Observe service telemetry: metrics and tracing": "docs/exercise-4"},
            { "Expose the service mesh with the Istio Ingress Gateway": "docs/exercise-5"},
            {"Perform traffic management": "docs/exercise-6"},
            {"Secure your service mesh": "docs/exercise-7"}
        ]
    }
    ```
