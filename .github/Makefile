org_name=poc
test_level=RunLocalTests

validate:
	@sf project deploy validate     \
		-w 120                      \
		-l "$(test_level)"          \
		-x package/package.xml      \
		-o "$(org_name)"            \
		--coverage-formatters clover

validate_v2:
	@sf project deploy validate     \
		-w 120                      \
		-l "$(test_level)"          \
		-x package/package.xml      \
		-o "$(org_name)"            \
		--coverage-formatters clover

validate_without_tests:
	@sf deploy metadata             \
		-w 120                      \
		-x package/package.xml      \
		-o "$(org_name)"            \
		-l NoTestRun                \
		--dry-run

deploy:
	@sf project deploy start        \
		-w 120                      \
		-l "$(test_level)"          \
		-x package/package.xml      \
		-o "$(org_name)"            \
		--coverage-formatters clover

deploy_v2:
	@sf project deploy start        \
		-w 120                      \
		-l "$(test_level)"          \
		-x package/package.xml      \
		-o "$(org_name)"            \
		--coverage-formatters clover

vlocity_validate:
	@echo "Generating Vlocity delta with packExport" && \
	vlocity -sfdx.username "$(org_name)" -job vlocity/manifest.yaml packExport || (echo "packExport failed" && exit 1)

vlocity_deploy:
	@echo "Starting real Vlocity deploy with packDeploy" && \
	vlocity -sfdx.username "$(org_name)" -job vlocity/manifest.yaml packDeploy || (echo "packDeploy failed" && exit 1)
