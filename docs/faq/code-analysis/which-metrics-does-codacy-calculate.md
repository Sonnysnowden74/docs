---
description: Codacy scans your code for issues and calculates code complexity, duplication, and coverage metrics. Besides this, Codacy also calculates a grade for your repository and files based on all calculated code quality metrics.
---

# Which metrics does Codacy calculate?

Codacy performs static code analysis and calculates code duplication, code complexity, and code coverage metrics for [most supported programming languages](../../getting-started/supported-languages-and-tools.md).

The following sections describe how Codacy calculates each supported metric and where you can see each metric on the Codacy UI:

-   [Grade](#grade)
-   [Issues](#issues)
-   [Complexity](#complexity)
-   [Duplication](#duplication)
-   [Code coverage](#code-coverage)

!!! note
    Depending on certain characteristics of your repository, such as the number of source code files and their size, Codacy may [apply limits to the code analysis](does-codacy-place-limits-on-the-code-analysis.md) that impact the calculation of the supported metrics.

## Grade

Codacy assigns an overall grade to your repository branches and to individual files to help you assess the code quality of your repository. Grades represent a weighted average of the available code quality metrics (issues, complexity, duplication, and coverage), and range from **A** to **F**:

<table>
  <tr>
    <td>Highest grade</td>
    <td><img src="../images/grade_a.png" alt="Grade A"></td>
    <td><img src="../images/grade_b.png" alt="Grade B"></td>
    <td><img src="../images/grade_c.png" alt="Grade C"></td>
    <td><img src="../images/grade_d.png" alt="Grade D"></td>
    <td><img src="../images/grade_e.png" alt="Grade E"></td>
    <td><img src="../images/grade_f.png" alt="Grade F"></td>
    <td>Lowest grade</td>
  </tr>
</table>

Codacy displays grades on the following places:

|Place|Metric|
|-----|------|
|[Files page](../../repositories/files.md)|Grade for each file in your repository|
|[Repository Dashboard](../../repositories/repository-dashboard.md)<br/>[Codacy badge](../../getting-started/adding-a-codacy-badge.md)|Grade of each analyzed branch in your repository|
|[Email notifications](../../account/emails.md#managing-your-email-notifications)|Grade of your repository|
|[Organization overview](../../organizations/organization-overview.md)|Average grade of the repositories in your organization and grade of each repository|
|[Repositories list](../../organizations/managing-repositories.md)|Grade of each repository in your organization|

## Issues

Codacy calculates the number of issues in the following static code analysis categories:

<!--issue-categories-start-->
-   **Code style:** Code formatting and syntax problems, such as variable names style and enforcing the use of brackets and quotation marks
-   **Error prone:** Code that may hide bugs and language keywords that should be used with caution, such as the operator `==` in JavaScript or `Option.get` in Scala
-   **Code complexity:** High complexity files that should be refactored
-   **Performance:** Code that can have performance problems
-   **Compatibility:** Mainly for frontend code, compatibility problems across different browser versions
-   **Unused code:** Unused variables and methods, code that can't be reached
-   **Security:** Potential security vulnerabilities, including hard-coded passwords and keys (secret scanning), vulnerable dependencies (software composition analysis or SCA), and insecure code patterns (static application security testing or SAST). For more information, see the complete [list of security issue categories](../../organizations/managing-security-and-risk.md#supported-security-categories)
-   **Documentation:** Methods and classes that don't have the correct comment annotations
-   **Best practice:** Code that doesn't follow the recommended coding standards and best practices
-   **Comprehensibility:** Code that can be difficult to understand and modify
<!--issue-categories-end-->

Besides this, Codacy also allows you to compare issues across repositories with different sizes by showing **issues per thousand lines of code (kLoC)**.

Codacy displays issues on the following places:

|Place|Metric|
|-----|------|
|[Commit detail page](../../repositories/commits.md)<br/>[Pull request detail page](../../repositories/pull-requests.md)<br/>[Email notifications](../../account/emails.md#managing-your-email-notifications)|Number of new and fixed issues introduced by the commit or pull request|
|[Files page](../../repositories/files.md)|Number of issues in each file|
|[Issues page](../../repositories/issues.md)|List of all issues detected in each branch|
|[Repository Dashboard](../../repositories/repository-dashboard.md)|Issues per 1000 lines of code|
|[Organization overview](../../organizations/organization-overview.md)|Average issues / kLoC of the repositories in your organization and issue / kLoC of each repository|
|[Repositories list page](../../organizations/managing-repositories.md)|Issues / kLoC in each repository in your organization|

## Complexity

Codacy uses [cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity) to identify files with complex methods in your repository. Cyclomatic complexity is the number of linearly independent paths through the source code of a method: the more control flow statements used in a method, the higher the value. Methods with a high cyclomatic complexity are more difficult to test and more likely to have defects. [Learn more about code complexity](https://blog.codacy.com/code-complexity/) on Codacy's blog.

Codacy calculates complexity as follows:

-   The complexity value of a file is the total sum of the cyclomatic complexities of all methods within it.
-   A file is considered complex if its cyclomatic complexity value is higher than the threshold [**File is complex when over**](../../repositories-configure/adjusting-quality-goals.md).
-   The complexity value of a commit or pull request is determined by the cyclomatic complexity of its changes.

Codacy displays complexity on the following places:

|Place|Metric|
|-----|------|
|[Commit detail page](../../repositories/commits.md)<br/>[Pull request detail page](../../repositories/pull-requests.md)<br/>[Email notifications](../../account/emails.md#managing-your-email-notifications)|The complexity variation introduced by a commit or pull request is defined as the sum of the changes in code complexity for each file modified in the commit or pull request|
|[Files page](../../repositories/files.md)|The file complexity value is the sum of the complexity values of all methods defined within the file|
|[Repository Dashboard](../../repositories/repository-dashboard.md)|Percentage of complex files in your repository and how the metric is evolving over time|
|[Organization overview](../../organizations/organization-overview.md)|Average percentage of complex files in the repositories in your organization and percentage of complex files in each repository|
|[Repositories list page](../../organizations/managing-repositories.md)|Percentage of complex files in each repository in your organization|

## Duplication

Codacy identifies clones or [sequences of duplicate code](https://en.wikipedia.org/wiki/Duplicate_code) that exist in at least two different places of the source code of your repository. Clones typically indicate deeper code quality issues and should be eliminated through abstraction when possible.

Codacy calculates duplication as follows:

-   The duplication value for each file is the number of clones in the file.
-   A file is considered duplicated if the number of clones in the file is higher than the threshold [**File is duplicated when over**](../../repositories-configure/adjusting-quality-goals.md).
-   The duplication value of a commit or pull request is the number of clones introduced by the commit or pull request.

!!! note
    You can [customize the rules for identifying duplicated blocks of code](../../repositories-configure/codacy-configuration-file.md#pmd-cpd-duplication) when using PMD CPD to analyze the source code of your repository.

Codacy displays duplication on the following places:

|Place|Metric|
|-----|------|
|[Commit detail page](../../repositories/commits.md)<br/>[Pull request detail page](../../repositories/pull-requests.md)<br/>[Email notifications](../../account/emails.md#managing-your-email-notifications)|Number of clones added or fixed by a commit or pull request|
|[Files page](../../repositories/files.md)|Duplication value of each file|
|[Repository Dashboard](../../repositories/repository-dashboard.md)|Percentage of duplicated files in your repository and how the metric is evolving over time|
|[Organization overview](../../organizations/organization-overview.md)|Average percentage of duplicated files in the repositories in your organization and percentage of complex files in each repository|
|[Repositories list page](../../organizations/managing-repositories.md)|Percentage of duplicated files in each repository in your organization|

## Code coverage

Code coverage describes the degree to which the source code of a program is tested. There are several types of coverage, but Codacy uses line coverage, which measures the percentage of coverable lines of code that are covered by automated tests. [Learn more about code coverage](https://blog.codacy.com/a-guide-to-code-coverage-part-1-code-coverage-explained/) on Codacy's blog.

You must set up your CI/CD pipeline to [upload code coverage data to Codacy](../../coverage-reporter/index.md). Because of this, the tool that you use to generate the coverage reports is responsible for creating the data that Codacy then uses to calculate code coverage.

Codacy calculates code coverage as follows:

-   The coverage value for each file is the percentage of coverable lines that are covered by tests in the file. If a line is covered multiple times, Codacy counts it as a single covered line when calculating coverage.
-   A repository is considered to have acceptable coverage if the percentage of coverable lines that are covered by tests in the repository is higher than the threshold [**Coverage is under**](../../repositories-configure/adjusting-quality-goals.md).
<!--code-coverage-metrics-start-->
-   The **coverage variation** of a commit or pull request is the increase or drop in the percentage of coverable lines that are covered by tests in the repository because of the changes of the commit or pull request.
-   The **diff coverage** of a pull request is the percentage of **coverable lines** that the pull request **added or modified** that are covered by tests.

    If a pull request doesn't add or modify any coverable lines, the diff coverage is `∅` (not applicable). This scenario happens when the only changes in a pull request are:

    -   Deleted lines
    -   Added or modified lines that aren't coverable
<!--code-coverage-metrics-end-->

!!! note
    If you encounter a situation where Codacy shows an unexpected drop in coverage, learn about [the most common reasons causing those scenarios](why-does-codacy-show-unexpected-coverage-changes.md).

Once the coverage setup is complete, Codacy displays coverage data on the following places:

|Place|Metric|
|-----|------|
|[Commit detail page](../../repositories/commits.md)<br/>[Pull request detail page](../../repositories/pull-requests.md)<br/>[Email notifications](../../account/emails.md#managing-your-email-notifications)|Variation in percentage points of the coverage value for all files in the commit or pull request|
|[Pull request detail page](../../repositories/pull-requests.md)|Diff coverage for the changes included in the pull request|
|[Files page](../../repositories/files.md)|Coverage percentage of each file|
|[Repository Dashboard](../../repositories/repository-dashboard.md)|Coverage of the most recent commit of the selected branch and its evolution over time|
|[Codacy badge](../../getting-started/adding-a-codacy-badge.md)|Coverage of the most recent commit of the configured branch|
|[Organization overview](../../organizations/organization-overview.md)|Average coverage of the repositories in your organization and coverage of each repository|
|[Repositories list page](../../organizations/managing-repositories.md)|Coverage of each repository in your organization|

## See also

-   [Diff coverage: <span class="skip-vale">we have</span> a new metric and quality gate rule for PRs](https://blog.codacy.com/diff-coverage/)
-   [Why does Codacy show unexpected coverage changes?](why-does-codacy-show-unexpected-coverage-changes.md)
-   [Does Codacy place limits on the code analysis?](does-codacy-place-limits-on-the-code-analysis.md)
