# case-178312259400188-verification

Verification: CodeBuild self-hosted runner (CI) + CodePipeline approval flow (CD)

## Architecture

```
push → webhook → CodeBuild Runner (GitHub Actions self-hosted)
  → CI job executes
  → if main branch push: aws codepipeline start-pipeline-execution
    → Pipeline: Source → Manual Approval → Deploy (echo)
```

## Deploy

```bash
aws cloudformation deploy \
  --template-file template.yml \
  --stack-name case-178312259400188 \
  --capabilities CAPABILITY_NAMED_IAM \
  --region ap-northeast-1
```

## Cleanup

```bash
aws cloudformation delete-stack --stack-name case-178312259400188 --region ap-northeast-1
```
# test
# feature branch test
