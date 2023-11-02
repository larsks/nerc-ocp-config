To update this repository with schemas from your currently cluster:

```
./schemautil
```

This will:

1. Fetch OpenAPI schemas from the remote cluster
2. Split the schema definitions into individual files under the `schemas` directory (wrapped with a bogus metadata header to make kustomize happy)
3. Re-generate `schemas/kustomization.yaml`

The `kustomization.yaml` in this directory includes the resources from the `schemas` directory and applies our patches (which primarily add merge keys to CRDs).

The `Makefile` in the parent directory then processes the result with yq ([this one], not [that one]) to create a merged OpenAPI schema.

[this one]: https://kislyuk.github.io/yq/
[that one]: https://github.com/mikefarah/yq
