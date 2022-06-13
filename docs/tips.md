# Tekton Tips

## Prune failed PipelineRuns

```bash
# Switch to your Project
oc project your-project

PIPELINE_PROJECTS=($(oc get pipelineruns -o=jsonpath='{.items[?(@.status.conditions[?(@.type=="Succeeded")].status=="failed")].metadata.name}'))

## Loop through PipelineRuns
for i in "${PIPELINE_PROJECTS[@]}"
do
  oc delete pipelinerun $i --dry-run=client
done

for i in "${PIPELINE_PROJECTS[@]}"
do
  oc delete pipelinerun $i
done
```