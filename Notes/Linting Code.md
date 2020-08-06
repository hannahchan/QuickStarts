# Linting Code

_Linting_ in software development is the process of using a tool to analyze source code for programmatic or stylistic errors in order to help you improve the overall quality of your code. The term _linting_ originally comes from a Unix utility for C. There are many code linters available today for various programming languages.

## CloudFormation Linter - <https://github.com/aws-cloudformation/cfn-python-lint>

`cfn-lint` validates CloudFormation YAML or JSON templates against [CloudFormation Resource Specifications](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-resource-specification.html) and performs additional checks. Includes checking valid values for resource properties and best practices. Python is required to use `cfn-lint` as it is a Python package.

Once installed, lint your CloudFormation templates by running;

    cfn-lint <File>

Glob patterns supported.

## ESLint - <https://eslint.org/>

ESLint is an open source JavaScript linting utility used to find problematic patterns or code that doesn't adhere to certain style guidelines in Node.js projects.

To add ESLint to your project;

    npm install eslint --save-dev

To create an initial ESLint configuration file;

    npx eslint --init

To run ESLint;

    npx eslint <File/Directory>

## Prettier - <https://prettier.io/>

Prettier is an opinionated code formatter that works with many file types including JavaScript, JSX, Typescript, JSON, CSS, HTML, YAML and Markdown. It's written in JavaScript and requires Node.js to run.

Checks to see if the given file or directory is formatted according to Prettier;

    npx prettier --check <File/Directory>

Attempts to fix formatting issues for the given file or directory;

    npx prettier --write <File/Directory>

## StyleCop.Analyzers - <https://github.com/DotNetAnalyzers/StyleCopAnalyzers>

StyleCop.Analyzers is one of many ways in which you can lint C# code. All you have to do is add the nuget package `StyleCop.Analyzers` to your C# project. If you have multiple C# projects and don't want to added this package to every project manually, create a `Directory.Build.props` next to your solution file and add it there. Below is an example `Directory.Build.props` file.

```xml
<Project>

  <PropertyGroup>
    <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)/CodeAnalysis.ruleset</CodeAnalysisRuleSet>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="StyleCop.Analyzers" Version="1.1.118">
      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
  </ItemGroup>

</Project>
```

To configure individual rules for StyleCop.Analyzers, you'll need to reference a ruleset file. The following is an example ruleset file.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Code Analysis Rule Set" Description="Code Analysis Rules" ToolsVersion="15.0">

  <!-- https://github.com/DotNetAnalyzers/StyleCopAnalyzers/blob/master/DOCUMENTATION.md -->
  <Rules AnalyzerId="StyleCop.Analyzers" RuleNamespace="StyleCop.Analyzers">
    <Rule Id="SA0001" Action="None" />
    <Rule Id="SA1600" Action="None" />
    <Rule Id="SA1601" Action="None" />
    <Rule Id="SA1633" Action="None" />
    <Rule Id="SA1652" Action="None" />
  </Rules>

</RuleSet>
```

## SonarAnalyzer.CSharp - <https://github.com/SonarSource/sonar-dotnet>

SonarAnalyzer.CSharp is a static analyzer which you can use to help you spot code smells in C# code. All you have to do is add the nuget package `SonarAnalyzer.CSharp` to your C# project. If you have multiple C# projects and don't want to added this package to every project manually, create a `Directory.Build.props` next to your solution file and add it there. Below is an example `Directory.Build.props` file.

```xml
<Project>

  <PropertyGroup>
    <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)/CodeAnalysis.ruleset</CodeAnalysisRuleSet>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="SonarAnalyzer.CSharp" Version="8.10.0.19839">
      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
  </ItemGroup>

</Project>
```

To configure individual rules for StyleCop.Analyzers, you'll need to reference a ruleset file. The following is an example ruleset file.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Code Analysis Rule Set" Description="Code Analysis Rules" ToolsVersion="15.0">

  <!-- https://rules.sonarsource.com/csharp -->
  <Rules AnalyzerId="SonarAnalyzer.CSharp" RuleNamespace="SonarAnalyzer.CSharp">
    <Rule Id="S1172" Action="None" />
    <Rule Id="S3626" Action="None" />
  </Rules>

</RuleSet>
```
