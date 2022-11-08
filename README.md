====For Organization Runners===

---
apiVersion: actions.summerwind.dev/v1alpha1
kind: RunnerDeployment
metadata:
  name: lbg-platform-runner
  namespace: actions-runner-system
spec:
  template:
    spec:
      image: summerwind/actions-runner-dind
      dockerdWithinRunnerContainer: true
      organization: gh-action-runners
      labels:
      - lbg-platform-linux
      - lbg-platform-runner
      env: []
---
apiVersion: actions.summerwind.dev/v1alpha1
kind: HorizontalRunnerAutoscaler
metadata:
  name: lbg-platform-runner-autoscaler
  namespace: actions-runner-system
spec:
  scaleTargetRef:
    kind: RunnerDeployment
    name: lbg-platform-runner
  scaleDownDelaySecondsAfterScaleOut: 300
  minReplicas: 50
  maxReplicas: 100
  metrics:
  - scaleDownFactor: "0.5"
    scaleDownThreshold: "0.2"
    scaleUpFactor: "2"
    scaleUpThreshold: "0.5"
    type: TotalNumberOfQueuedAndInProgressWorkflowRuns
    repositoryNames:
    - test-runners-1
