# PSRule for GitHub

A suite of rules to validate GitHub repositories using PSRule.

![ci-badge]

Features of PSRule for GitHub include:

- [Ready to go](docs/features.md#ready-to-go) - Leverage pre-built rules.
- [DevOps](docs/features.md#devops) - Validate repositories throughout their lifecycle.
- [Cross-platform](docs/features.md#cross-platform) - Run with GitHub Actions or other CI integrations.

## Disclaimer

This project is open source and **not a supported product**.

If you are experiencing problems, have a feature request, or a question, please check for an [issue] on GitHub.
If you do not see your problem captured, please file a new issue, and follow the provided template.

If you have any problems with the [PSRule][engine] engine, please check the project GitHub [issues](https://github.com/Microsoft/PSRule/issues) page instead.

## Getting the modules

This project requires the `PSRule` PowerShell module. For details on each see [install].

You can download and install these modules from the PowerShell Gallery.

Module              | Description | Downloads / instructions
------              | ----------- | ------------------------
PSRule.Rules.GitHub | Validate GitHub repositories using PSRule. | [latest][module] / [instructions][install]

## Getting started

### Export repository

To validate a GitHub repository, first export configuration data with the `Export-GitHubRuleData` cmdlet.

For example:

```powershell
# Export repository configuration data for Microsoft/PSRule
Export-GitHubRuleData -Repository 'Microsoft/PSRule';
```

To export multiple repositories:

- Comma separate each repository.
- Use `<organization>/` to include all repositories in the organization.

Authenticate to export private repositories by:

- Using `-Credential` to specify a `PSCredential` object with a personal access token (PAT).
The username of `PSCredential` is ignored.
- Using `-UseGitHubToken` to read a PAT token from the `GITHUB_TOKEN` environment variable.

### Validate repositories

To validate a GitHub repository using the extracted data use the `Assert-PSRule` cmdlet.

For example:

```powershell
Assert-PSRule -InputPath .\*.json -Module 'PSRule.Rules.GitHub';
```

For advanced usage, see [Assert-PSRule](https://microsoft.github.io/PSRule/commands/PSRule/en-US/Assert-PSRule.html) help.

## Rule reference

For a list of rules included in the `PSRule.Rules.GitHub` module see:

- [Rules by category](docs/rules/en/module.md)

## Language reference

PSRule for GitHub extends PowerShell with the following features.

### Commands

The following commands exist in the `PSRule.Rules.GitHub` module:

- [Export-GitHubRuleData](docs/commands/PSRule.Rules.GitHub/en-US/Export-GitHubRuleData.md) - Export GitHub repository configuration.

## Changes and versioning

Modules in this repository will use the [semantic versioning](http://semver.org/) model to declare breaking changes from v1.0.0.
Prior to v1.0.0, breaking changes may be introduced in minor (0.x.0) version increments.
For a list of module changes please see the [change log](CHANGELOG.md).

> Pre-release module versions are created on major commits and can be installed from the PowerShell Gallery.
> Pre-release versions should be considered experimental.
> Modules and change log details for pre-releases will be removed as standard releases are made available.

## Contributing

This project welcomes contributions and suggestions.
If you are ready to contribute, please visit the [contribution guide](CONTRIBUTING.md).

## Code of Conduct

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)
or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Maintainers

- [Bernie White](https://github.com/BernieWhite)

## License

This project is [licensed under the MIT License](LICENSE).

[issue]: https://github.com/Microsoft/PSRule.Rules.GitHub/issues
[install]: docs/install-instructions.md
[ci-badge]: https://dev.azure.com/bewhite/PSRule.Rules.GitHub/_apis/build/status/PSRule.Rules.GitHub-CI?branchName=main
[module]: https://www.powershellgallery.com/packages/PSRule.Rules.GitHub
[engine]: https://github.com/Microsoft/PSRule
