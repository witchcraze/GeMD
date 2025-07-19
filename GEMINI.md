# GEMINI.md: Instruction Manual for AI-Driven Development

This document provides instructions for the AI assistant (Gemini) to perform development tasks in this project. To ensure consistency, quality, and efficiency, please adhere strictly to the following guidelines.

## 1. Guiding Principles for this Document (GEMINI.md)

### 1.1. Purpose
This document is the "starting point for thought and action" for the AI to autonomously advance development. All instructions for the AI are consolidated here, functioning as the project's constitution.

### 1.2. Structure and Writing Rules
To prevent this document from becoming bloated and to maintain readability and maintainability, it is written according to the following rules.

*   **Clear Separation of Strategy and Workflow:**
    *   **Strategy Section (Chapter 3):** Describes only the **policy** of **"What"** the project aims for and **"Why."** This section covers long-term, universal guidelines.
    *   **Workflow Section (Chapter 4):** Describes only the **"How"**—the **concrete, reproducible procedures**—to realize the strategy. This section covers commands and conventions that the AI will directly execute and reference.
*   **Externalization of Details:**
    *   Detailed setup procedures for specific technologies, design philosophies, and lengthy conventions are created as separate Markdown files under the `docs/` directory.
    *   This document only contains references (links) to those external files, keeping this document focused on "instructions" that define the AI's behavior.
*   **Introduction of YAML Configuration Blocks:**
    *   **Purpose:** To describe strict "settings" that directly control the AI's behavior (e.g., label definitions, naming conventions), YAML code blocks are introduced within the Markdown.
    *   **Role Division:** The natural language Markdown is responsible for the "Why" (strategy and philosophy), while YAML is responsible for the "How" (concrete settings), separating their roles.
    *   **Scope of Application:** YAML is actively used for settings that are better for the AI to interpret and execute mechanically (e.g., label definitions, naming conventions).

### 1.3. Update Process
Changes to this document require the following process to maintain quality and prevent unintended modifications.
1.  Propose changes in a GitHub Issue.
2.  After the proposal is approved, the AI creates a Pull Request to update this document.
3.  The change is finalized when the Pull Request is reviewed and merged.

### 1.4. Style Guide
To maintain the readability of this document, the following writing style is followed.

*   **Use of Lists:**
    *   **Purpose:** Used to describe information with order or hierarchy, such as procedures, checklists, and parallel choices.
    *   **Example:** Steps in the development process, perspectives for self-review.

*   **Use of Tables:**
    *   **Purpose:** Used to compare and contrast multiple items with common attributes. Ideal for clearly showing the correspondence of information.
    *   **Example:** A list of labels and their roles, command options and their descriptions.

*   **Writing Style:** To clarify that these are instructions for the AI, use a direct or imperative style rather than a polite (desu/masu) style.

---

## 2. Fundamental Principles for AI Collaboration

*   **Principle of Communication Language:**
    *   **Documentation:** The primary language for all internal documentation (`GEMINI.md`, `docs/`) is English to ensure maximum performance and global collaboration.
    *   **User and GitHub Interactions:** All communication with the user (CLI) and content generated on GitHub (Issue titles and bodies, Pull Request titles and bodies, all comments) **must** be in the language the user is currently using. The AI is responsible for adapting its responses and generated content to the user's language, even if internal templates or guidelines are in English.
*   **Issue-Driven Development:** All development and modification work must originate from a GitHub Issue. If a user's instruction is not based on an Issue, the AI will not start the work and will first request or propose the creation of a corresponding Issue.
*   **Goal-Oriented Action:** Understand not just the superficial instructions in an Issue, but the user's ultimate goal behind them, and act proactively to achieve that goal.
*   **Absolute Adherence to and Self-Verification of Rules:** `GEMINI.md` is the sole constitution governing the AI's thoughts and actions, and its rules are absolute. Before any action—file modification, command execution, Issue/PR operations, etc.—the AI is obligated to self-verify that the action is in complete agreement with the `GEMINI.md` workflow. If there is any contradiction or uncertainty, it must never execute the action and must first seek confirmation from the user.
*   **Ensuring Transparency:** All operations performed by the AI, such as file changes and command executions, must be clearly recorded and reported.
*   **Step-by-Step Execution:** Large changes should be broken down into small steps, and the user's confirmation should be sought at critical decision points.
*   **Principle of Proactive Dialogue:** The AI must not operate on assumptions. It must treat ambiguity—whether in user requests, code, or documentation—as a signal to initiate a dialogue. It will use clear, concise, and, where possible, option-based questions to confirm its understanding and will briefly state its core assumptions when presenting plans or solutions.
*   **Principle of Prior Investigation and Contextual Fitness:** Before proposing any changes, creating new Issues, or starting implementation, the AI has an absolute obligation to conduct a thorough investigation of the existing codebase, documentation (`GEMINI.md`, `docs/`), and active Issues. This is to ensure that any proposal is contextually appropriate, avoids duplication, aligns with existing patterns and architectural decisions, and provides genuine value. The AI must explicitly summarize the results of this investigation in its proposals.

## 3. Project Strategy
*(This section describes only the "policy" that the project aims for)*

*   **Development Strategy:**
    *   **Thorough Issue-Driven Development (IDD):** All development tasks start from a GitHub Issue. By clearly agreeing on the purpose, specifications, and plan in the Issue before starting implementation, we prevent rework and ensure transparency.
    *   **Thorough Test-Driven Development (TDD):** When adding new features or refactoring, it is **mandatory** to start by creating or updating test cases under all circumstances.
        *   **If tests do not exist:** If tests for the feature to be changed do not yet exist, create new tests first.
        *   **If tests already exist:** Review the existing tests and make the necessary modifications (adding test cases, changing assertions, etc.) to cover the current changes.
    *   By thoroughly implementing this "test-first" approach, we prevent unintended side effects (regressions) and treat code quality and maintainability as top priorities.
    *   **Proactive Requirement Definition and Issue Decomposition:** If a user's request is ambiguous, large-scale, or open to multiple interpretations, the AI will clarify the requirements through dialogue before starting implementation. The agreed-upon content will be recorded in documents or Issues, and development will proceed after decomposing it into a group of appropriately sized Issues. This prevents misunderstandings and accurately sets the direction of development.
*   **Documentation Strategy:**
    *   **Purpose:** Documentation is not just a deliverable, but aims to function as a "thinking aid" for all stakeholders, including our future selves, by systematizing project knowledge. It prevents knowledge from being siloed, lowers the learning curve for new participants, and facilitates smooth decision-making.
    *   **Principle: Documentation as Code (DaC):** Like code, documentation should be version-controlled, go through a review process, and be continuously updated. Changes to code and documentation are always treated as a single unit.
*   **GitHub Operational Strategy:**
    *   **Basic Strategy: Adoption of GitHub Flow:** The basic strategy is "GitHub Flow," where the `main` branch is always kept in a deployable state, and all feature additions and fixes are done in feature branches.
    *   **Reason for Adoption:** This strategy has simple operational rules, reduces the context the AI needs to consume to perform tasks, and makes it easy to grasp the state even if a session is interrupted. It avoids the complexity of managing multiple persistent branches (e.g., `develop`) and prioritizes the AI's ability to maintain consistency and operate stably.
    *   **Branching Strategy:**
        * `main` branch: The most stable branch, deployed to the production environment. Direct commits are prohibited; it is updated only by merging Pull Requests.
        * Feature branches: Branches corresponding to each Issue. They are created from the `main` branch, and a Pull Request to the `main` branch is created after the work is completed.
    *   **Branch Lifecycle:**
        * **Creation:** Created from the `main` branch when starting to implement an Issue.
        * **Naming Convention:** Follows the format defined in the YAML block below. The AI must adhere to this format.
          ```yaml
          branching:
            feature_branch_format: "{issue_number}-{kebab-case-issue-title}"
          ```
        * **Deletion:** Deleted promptly after the Pull Request is merged into the `main` branch.
    *   **Version Control Exclusion (.gitignore):**
        *   **Purpose:** To prevent repository bloat and avoid issues caused by environmental differences, it is crucial to exclude unnecessary files from version control. This includes dependencies (e.g., `node_modules/`), build artifacts, log files, and editor-specific settings.
        *   **AI's Responsibility:**
            1.  **Check for `.gitignore`:** At the start of any task, the AI must check for the existence of a `.gitignore` file in the project root.
            2.  **Propose Creation:** If no `.gitignore` file exists, the AI will analyze the project's technology stack (e.g., by checking for `package.json`, `pom.xml`, `requirements.txt`) and propose a standard, technology-specific `.gitignore` template for user approval before creating it.
            3.  **Propose Updates:** If a `.gitignore` file exists, the AI will assess if the current task introduces any new files or patterns that should be excluded from version control (e.g., new build outputs, log files). If so, it will propose the necessary additions to the user for approval.
        *   **Handling Sensitive Information:** It is an absolute rule that files containing sensitive information—such as `.env` files, configuration files with API keys, or credentials—**must never** be committed to the repository. The AI is obligated to ensure these files are listed in the `.gitignore` file.

## 4. Development Workflow
*(This section describes only the "concrete, reproducible procedures" for executing the strategy. The AI will strictly follow this workflow to autonomously carry out development)*

### 4.1. Basic Principle: Single-Tasking
The AI does not handle multiple Issues simultaneously. It must complete (merge) one Issue before starting the next. This prevents branch conflicts and work confusion.

### 4.2. Issue-Driven Development Process
The following is the series of processes from when an Issue is created until it is closed. The AI and the user will collaborate according to this process.

#### **Principle: Use of Temporary Files for GitHub Interactions**
When performing operations that send multi-line text on GitHub, such as creating Issues or comments, or creating Pull Requests or review comments, always write the body text to a temporary file and use the `--body-file` option to avoid unexpected errors in command-line arguments (especially with quotation handling in `gemini cli`).

#### **Principle: Recording Approval**
If user approval is given in the CLI prompt, the AI will post a comment stating "User approval confirmed on the CLI" to the appropriate location to leave a record of the approval. The location is determined by the current phase of the work:
- **Planning Phase (`status: planning`):** The approval record is posted to the **GitHub Issue**.
- **Review Phase (`status: review`):** The approval record is posted to the **Pull Request**.

#### **Issue Granularity**
Issues are created in concrete, clear task units that can be completed in a single Pull Request, based on the following principles.

*   **Single Responsibility Principle:** One Issue focuses on one concern (feature addition, bug fix, refactoring, etc.). Do not mix multiple purposes in one Issue.
*   **Clear Completion Criteria:** The Issue should describe the specific conditions under which the task is considered complete.
*   **Appropriate Scope:**
    *   **Decomposition of Large Issues:** Large-scale feature development that is expected to take more than a day or spans multiple components should be broken down into smaller, multiple Issues. The AI will propose the decomposition of large Issues based on the `Proactive Requirement Definition and Issue Decomposition` strategy.
    *   **Consolidation of Small Issues:** If multiple Issues are closely related and it is more efficient to handle them together, consider consolidating them into a single Issue.

#### **Step 1: Issue Reception and Assignment**
1.  **Trigger:** A user or the AI creates a new Issue.
2.  **AI's Response:**
    *   The AI detects the newly created Issue and sets itself as the assignee for that Issue.
    *   It analyzes the content of the Issue, applies the appropriate **type label**, and sets the initial **status label** by finding the entry with `initial: true` in the state machine defined in `4.4. Label Management`.

#### **Step 2: Implementation Planning and Agreement**
1.  **Trigger:** The `status: planning` label is applied to the Issue.
2.  **AI's Response:**
    *   **1. Conduct Prior Investigation:** Before formulating a plan, the AI must thoroughly investigate the existing codebase, documentation, and issues related to the task.
    *   **Reconfirm Context:** Before starting to create a plan, first reload the latest description of the Issue, related Pull Requests, related comments, and all relevant documents, including `GEMINI.md` and those under `docs/`, to always grasp the latest context.
    *   **Initial Understanding Check:** Thoroughly read the Issue content to understand the underlying **purpose**. Before diving into a detailed plan, the AI should state its high-level understanding of the issue's goal and ask for confirmation (e.g., "My understanding is that the goal is to refactor the authentication module to use JWTs for better security. Is this correct?").
    *   **Clarify Ambiguities:** If the purpose or requirements are unclear or open to multiple interpretations, the AI must ask clarifying questions.
    *   **Propose Options:** If multiple implementation approaches are possible, the AI must concisely present the pros and cons of each as clear options and prompt the user to choose (e.g., "For handling X, we can use Option A or Option B. Option A is more performant, while Option B is simpler. Which do you prefer?").
    *   Based on the confirmed understanding, identify the documents and code that need to be updated.
    *   Break down the necessary tasks and create a concrete implementation plan that lists all files to be changed.
    *   After commenting on the Issue with the implementation plan in the following format, tell the user, "I have posted the implementation plan on the GitHub Issue. Please review it and comment with 'Approve', or convey your approval on this CLI. **After approval, please instruct me to proceed to the next step.**" and wait for a response.
        ```markdown
        ### Implementation Proposal

        To resolve this Issue, I will proceed with the implementation according to the following plan.

        #### 1. **Pre-investigation Summary**
        - (In this section, the AI must summarize the findings of its investigation, referencing relevant files, functions, or existing issues.)

        **Files to be changed:**
        - `path/to/file1.ext`
        - `path/to/file2.ext`

        #### 2. **Contribution to Project Goals**
        - (In this section, briefly explain how the proposed changes contribute to the overall goals of the project)

        #### 3. **Overview of Changes**
        - (In this section, briefly explain the overall picture and purpose of the changes)

        #### 4. **Specific Work Content for Each File**
        - `path/to/file1.ext`: (Describe the specific changes for this file)
        - `path/to/file2.ext`: (Describe the specific changes for this file)

        #### 5. **Definition of Done**
        - [ ] All necessary code changes have been implemented.
        - [ ] New tests have been added to cover the changes.
        - [ ] All existing and new tests pass.
        - [ ] The documentation has been updated to reflect the changes.
        - [ ] The implementation has been manually verified.

        ---
        If you approve, please reply to this comment with "Approve".
        ```
3.  **User's Response:**
    *   Review the plan, and if there are no problems, reply with "Approve" to the relevant comment on the GitHub Issue or convey approval on the CLI, and then instruct the AI to proceed with the work.

#### **4.2.0: AI-Initiated Issue Proposal Workflow**
This workflow governs how the AI proposes and creates new Issues, ensuring they are necessary, well-researched, and approved by the user before creation.

1.  **Trigger:** The AI identifies the need for a new Issue, either based on a direct user instruction that lacks a corresponding Issue or through its own analysis during development (e.g., discovering a necessary refactoring or a new bug).
2.  **Mandatory Investigation:** Before proposing a new Issue, the AI must conduct a thorough investigation to:
    *   Confirm that no existing or closed Issue already addresses the problem.
    *   Analyze the relevant code and documentation to understand the context and potential impact.
3.  **Draft and Propose:** The AI drafts a concise and descriptive Issue title and body. The body must include a "Pre-investigation Summary" section detailing the findings from the investigation. The AI will then present the drafted title and body to the user in the CLI and ask for approval to create the Issue.
4.  **User Approval:** The AI must wait for explicit user approval (e.g., "Yes, create it") before proceeding.
5.  **Issue Creation:** Once approved, the AI will use the `gh issue create` command with the approved title and body to create the Issue on GitHub.

#### **4.2.1. Handling Mid-Implementation Questions**
If a minor, localized ambiguity arises during the implementation phase (`Step 3`), the AI should not halt the entire process. Instead, it should formulate a clear, multiple-choice or yes/no question and present it to the user for a quick decision. This allows for efficient clarification without the overhead of a full plan revision. For example: "I've encountered a situation where the user's session can expire. Should I (A) redirect to the login page, or (B) show an inline 'session expired' message?"

#### **Step 3: Implementation and Pull Request Creation**
1.  **Trigger:** The AI, having received instructions from the user to proceed, confirms the user's approval on the GitHub Issue or in the CLI prompt. If approval cannot be confirmed, it will ask the user for approval again.
2.  **AI's Response:**
    *   Before changing the status, the AI must validate the transition against the state machine in `4.4. Label Management`. It will then remove the `status: planning` label and apply the `status: implementing` label.
    *   Create a new branch from the `main` branch.
        *   Example: `12-update-development-workflow`
    *   Perform code changes, file creation/editing, test additions, etc., according to the implementation plan.
        *   **[IMPORTANT] Principle of Prohibiting Unplanned File Changes & Workflow for Proposing Them:** The AI will, in principle, not change any files other than those agreed upon in the implementation plan. If, in the course of implementation, it determines that an unplanned file change is necessary, it must follow this specific communication workflow:
            1.  **Suspend Work:** Immediately suspend the current implementation task.
            2.  **Report on the Issue:** Post a comment on the active GitHub Issue to report the need for an unplanned change.
            3.  **Provide Detailed Proposal:** The comment must contain a clear and structured proposal, including:
                - **File(s) to be Changed:** The full path of the file(s).
                - **Reason for Change:** A detailed explanation of why the unplanned change is necessary.
                - **Summary of Proposed Changes:** A concise overview of the modifications.
                - **Potential Impact:** An assessment of potential side effects, including impacts on other features or the need for additional tests.
                - **Alternative Solutions:** Any alternative approaches that were considered.
                - **Request for Approval:** A clear request for the user to review and approve the proposal.
            4.  **Await Approval:** Do not proceed with any changes (planned or unplanned) until the user explicitly approves the proposal in a comment on the Issue.
    *   **Final Review:** Before committing, the AI must review the "Definition of Done" checklist from the implementation plan and confirm that all items have been completed. The AI will then post a comment on the GitHub Issue with the completed checklist to report that all planned work is finished.
    *   **Mandatory Quality Gate:** Before committing, the AI **must** execute all test and lint commands. This is a non-negotiable gate.
        *   The AI must first check for the existence of `docs/03_TESTING_GUIDELINES.md`.
        *   If it exists, the AI must consult it to get the exact commands for tests, linting, and formatting.
        *   **If any check fails, the AI is prohibited from proceeding to the commit step.** It must analyze the failure, correct the code, and re-run all checks until they pass successfully. Only after all checks pass may the AI proceed.
    *   Once the work is complete, commit the changes. The commit message will follow the convention defined in `4.5. Commit Message Convention`.
    *   **Push the feature branch and set upstream:** Push the committed changes to the remote repository. This initial push **must** use the `--set-upstream` (or `-u`) flag to establish a tracking relationship between the local and remote branch. This is critical for the stability of subsequent workflow steps.
        *   **Command:** `git push --set-upstream origin {branch_name}`
    *   Create a Pull Request targeting the `main` branch.
    *   The body of the PR must include a link to the relevant Issue (e.g., `Closes #12`).

#### **Step 4: Quality Gate and Self-Review**
1.  **Trigger:** A Pull Request is created.
2.  **AI's Response:**
    *   Before changing the status, the AI must validate the transition against the state machine in `4.4. Label Management`. It will then remove the `status: implementing` label and apply the `status: review` label.
    *   **Check Diffs:** The AI runs the `gh pr diff` command to confirm that its changes are as intended.
    *   **Conduct Self-Review (Quality Gate):** Conduct a self-review from the following perspectives. This process serves as a **Quality Gate** to ensure the quality of the implementation.
        *   **Standard Review Items:**
            1.  **Are the diffs as intended?** Compare the results of `gh pr diff` with the implementation plan.
            2.  **Does the implementation meet the requirements of the Issue?**
            3.  **Has the 'Definition of Done' been verified and reported in the Issue?**
            4.  **Have all CI checks passed?**
            5.  **Does it comply with the `GEMINI.md` conventions (testing, naming rules, etc.)?**
            6.  **Is the code sufficiently readable and maintainable?**
            7.  **Are there any potential side effects from the changes?**
            8.  **Are there any unplanned file changes?**
            9.  **Is the documentation update appropriate?** In light of the **Documentation Strategy** and the definitions in `5.1`, is the documentation update appropriate?
        *   **Quality Gate Items:**
            1.  **Computational Complexity:** Is the computational complexity of the implemented algorithm appropriate? Is there a more efficient method?
            2.  **Security:** Does the code contain basic vulnerabilities such as SQL injection or XSS?
            3.  **Scalability:** Is the implementation scalable enough to accommodate future feature additions and changes?
    *   **Self-Correction:**
        *   If a problem is detected during the self-review (including a CI failure), the AI will first attempt to correct it itself.
        *   **If a CI check has failed,** the AI **must** analyze the failure logs from the CI system. It will then execute the **exact same test/lint commands locally** to replicate the failure. The AI will then correct the code, confirm the fix by re-running the local checks until they pass, and only then force-push the correction to the PR branch.
        *   For other issues, it will modify the code locally, amend the commit with `git commit --amend`, and then update the remote branch with `git push --force`.
        *   After correction, it will restart the process from the beginning of this step (checking diffs).
        *   Only if self-correction is difficult will the AI mention the user and consult on the specific problem and solution in a PR comment.
    *   **Request Review:** If no self-correction is needed, or after it is completed, comment on the PR with the results of the self-review in the following format, then tell the user, "Please review on the GitHub PR and comment with 'Approve for merge', or convey your approval on this CLI. **After approval, please instruct me to execute the merge.**" and wait for a response.
        ```markdown
        ### Self-Review Report

        I have conducted a self-review and confirmed that the implementation aligns with the project's standards and the requirements of the Issue. All standard checks, including diff confirmation, convention adherence, and documentation updates, have been successfully passed.

        ---

        ### Quality Gate Assessment

        - **Computational Complexity:** (Description of the evaluation)
        - **Security:** (Description of the evaluation)
        - **Scalability:** (Description of the evaluation)

        ---

        ### Design Trade-offs

        (Description of the design trade-offs, including why the current implementation was chosen and what other options were considered and discarded.)

        ---
        Please review and approve the merge.
        ```
3.  **User's Response:**
    *   Review the content of the PR and the AI's self-review.
    *   **If Approved:** If there are no problems, reply with "Approve for merge" to the relevant comment on the GitHub PR or convey approval on the CLI, and then instruct the AI to merge. The process then moves to `Step 5`.
    *   **If Modifications are Requested:** If the user requests changes, the process moves to `Step 4.1`.

#### Step 4.1: Handling Review Feedback and Modifications
This step defines the workflow when the user requests modifications during a Pull Request review. The goal is to handle feedback systematically, ensure changes are verified, and clearly communicate the resolution.

1.  **Trigger:** The user provides feedback on the Pull Request (e.g., comments, change requests) that requires code or documentation modifications.

2.  **AI's Response:**
    *   **Acknowledge and Plan:** The AI acknowledges the feedback. It analyzes the requested changes and creates a concise modification plan. This plan is posted as a reply comment on the PR to ensure clarity and alignment.
        *   Example Comment: "Thank you for the feedback. I will address the requested changes. Here is my plan:
1. Refactor the `userService.ts` to handle the null case.
2. Add a new unit test to cover this scenario.
I will proceed with these changes."
    *   **Clarify Ambiguities:** If the user's feedback is unclear, the AI must ask targeted questions to resolve the ambiguity before proceeding with any changes.
    *   **Implement Changes:** The AI modifies the code and/or documentation on the feature branch as per the plan.
    *   **Verify Locally:** The AI **must** re-run all relevant quality checks (tests, linting) as defined in `docs/03_TESTING_GUIDELINES.md` to ensure the modifications are correct and have not introduced any regressions.
    *   **Update Commit:** The AI incorporates the changes into the existing commit using `git commit --amend` to maintain a clean, single-commit history for the feature on the PR.
    *   **Force Push:** The AI updates the Pull Request by force-pushing the amended commit to the remote branch using `git push --force-with-lease`.
    *   **Re-request Review:** After successfully pushing the changes, the AI will post a new comment on the PR, indicating that the feedback has been addressed. The process **must** then return to the beginning of `Step 4` for a new, full self-review and user review cycle. The AI will wait for a new "Approve for merge" from the user before proceeding.
        *   Example Comment: "I have implemented the requested changes and all checks have passed. The PR is ready for another review."

#### **Step 5: Merge and Cleanup**
1.  **Trigger:** The AI, having received instructions from the user to merge, confirms that the user's "Approve for merge" comment exists on the GitHub PR.
2.  **AI's Response (Pre-merge Sync):**
    *   To prevent merge conflicts, the AI first synchronizes the feature branch with the latest `main` branch using a safe and explicit procedure.
    1.  Fetch the latest state from the remote repository to ensure all local references are up-to-date: `git fetch origin`
    2.  Switch to the `main` branch: `git checkout main`
    3.  Safely reset the local `main` branch to exactly match the state of the remote `main` branch. This avoids potential local merge conflicts: `git reset --hard origin/main`
    4.  Switch back to the feature branch: `git checkout {feature_branch_name}`
    5.  Rebase the feature branch onto the now-updated `main` branch: `git rebase main`
    6.  Force-push the rebased branch to the remote. **Crucially, the command must explicitly specify both the remote and the branch name.** This prevents accidental pushes to the wrong destination and works reliably even without a pre-configured upstream branch for push operations.
        *   **Command:** `git push --force-with-lease origin {feature_branch_name}`
3.  **AI's Response (Merge Execution and Verification):**
    *   **Merge Execution:** The AI merges the Pull Request using a squash merge. By default, `gh` creates a commit message using the Pull Request's title as the subject and the body as the detailed description, which helps maintain a clean and informative commit history on the `main` branch. The command used is `gh pr merge --squash --delete-branch`.
    *   **Result Verification:** After executing the merge command, the AI immediately verifies the actual status of the PR by querying the GitHub API. `gh pr view <PR_NUMBER> --json state`
    *   **Post-merge Actions:**
        *   If the state is `MERGED`, the AI confirms that the related Issue was automatically closed. It then performs the final cleanup and status update:
        1.  Switch back to the `main` branch to ensure a clean state for the next task.
            *   **Command:** `git checkout main`
        2.  Delete the now-merged local feature branch to maintain repository hygiene.
            *   **Command:** `git branch -d {feature_branch_name}`
        3.  Validate the transition against the state machine in `4.4. Label Management`, remove the `status: review` label from the closed Issue, and apply the `status: done` label.
        *   If the state is `OPEN` or `CLOSED` (but not merged), the AI reports the failure to the user, provides the error details, and asks for further instructions. It will not attempt to resolve the situation without user guidance.

### 4.3. Quality Assurance (QA) Workflow
*   **Core Principles of Quality:** Quality is not an afterthought; it is a core part of the development process. The AI is expected to build quality into the code from the start, not just check for it at the end.
*   **Testing Principles:**
    *   **Unit Tests:** All new functions and modules must be accompanied by unit tests that verify their correctness in isolation.
    *   **Integration Tests:** When changes span multiple modules, integration tests must be added to ensure the modules interact as expected.
    *   **End-to-End (E2E) Tests:** For features that impact user-facing workflows, E2E tests should be considered to validate the system from the user's perspective.
*   **Code Quality Principles:**
    *   **Static Analysis (Linting):** Code must be free of linting errors. This enforces a consistent code style and helps catch potential bugs early.
    *   **Code Formatting:** Code must be formatted according to the project's standards.
*   **Automated Quality Gates:**
    *   **Local Execution:** Before creating a commit, the AI **must** run all defined quality checks (tests, linting, formatting) locally. The successful execution of these checks, guided by `docs/03_TESTING_GUIDELINES.md` (if it exists), is a mandatory prerequisite for creating a Pull Request.
*   **Project-Specific Guidelines:**
    *   The specific commands, tools, and configurations for testing and linting for this project should be defined in `docs/03_TESTING_GUIDELINES.md`. The AI must always consult this document if it exists to execute the correct quality checks.

### 4.4. Label Management
The AI uses the labels defined in the following YAML to clarify the status and type of Issues and Pull Requests. This YAML block is the **single source of truth** for the issue workflow. The AI must strictly adhere to the transition rules defined by `initial` and `valid_next_statuses`. If a label does not exist when the AI tries to apply it, it will automatically create the label according to this definition before applying it.

```yaml
labels:
  status:
    - name: "status: planning"
      color: "FBCA04"
      description: "State where the AI is formulating an implementation plan"
      initial: true
      valid_next_statuses: ["status: implementing"]
    - name: "status: implementing"
      color: "1D76DB"
      description: "State where the AI is in the process of implementation"
      valid_next_statuses: ["status: review"]
    - name: "status: review"
      color: "8E44AD"
      description: "State where the Pull Request is awaiting review"
      valid_next_statuses: ["status: done"]
    - name: "status: done"
      color: "0E8A16"
      description: "State where the Issue has been addressed and merged"
  type:
    - name: "type: bug"
      color: "D73A4A"
      description: "A bug in existing functionality"
    - name: "type: feature"
      color: "0E8A16"
      description: "Addition of a new feature"
    - name: "type: documentation"
      color: "0075CA"
      description: "Creation or update of documentation"
    - name: "type: refactor"
      color: "A2EEEF"
      description: "Code improvement that does not change external behavior"
    - name: "type: chore"
      color: "FFFFFF"
      description: "Tasks other than the above, such as changes to the build process or auxiliary tools"
```

### 4.5. Commit Message Convention
The AI will create commit messages based on the Conventional Commits specification. The types of commits allowed are defined in the YAML block below.

```yaml
commits:
  conventional:
    types:
      - "feat"
      - "fix"
      - "docs"
      - "style"
      - "refactor"
      - "test"
      - "chore"
```

#### 4.5.1. Commit Timing and Granularity
To maintain a clean and understandable commit history, the AI will adhere to the following principles for commit timing and granularity.

*   **Commit Timing:**
    *   Commits should be made at logical points in the development process. This typically means committing a complete, self-contained change that fulfills a specific purpose.
    *   A good time to commit is when a logical unit of work is complete, such as a single feature implementation, a bug fix, or a refactoring task.
    *   It is encouraged to commit even if the work is not fully complete, as long as it represents a stable checkpoint (e.g., a part of a feature is implemented and passes tests).

*   **Commit Granularity:**
    *   **Single Responsibility Principle:** Each commit should focus on a single concern. Do not mix unrelated changes in one commit (e.g., a feature addition and a refactoring of unrelated code).
    *   **Atomic Changes:** A commit should represent an atomic change. This means that the change should be a single, indivisible unit of work.
    *   **Well-Scoped Changes:** The scope of a commit should be small enough to be easily described in the commit message. If a change is too large or complex to be summarized clearly, it should be broken down into smaller commits.

## 5. Documentation Strategy and Workflow
This defines the workflow for the AI to accurately understand the project's specifications and design philosophy and to maintain consistency between development and documentation.

### 5.1. Document Structure and Content
Information about the project is managed in the files defined in the YAML block below. Before starting development, the AI must read and understand these documents. The AI will use the `update_trigger` in this definition as the sole basis for determining whether a document needs to be updated.

```yaml
documentation:
  - file: "[README.md](README.md)"
    purpose: "Provides the information that new participants and external viewers will see first, as the face of the project. It includes the project overview, main features, technologies used, setup, basic usage, license, and contribution guidelines."
    update_trigger: "When there are major changes to the project's basic information, technology stack, or setup method."
  - file: "[CONTRIBUTING.md](CONTRIBUTING.md)"
    purpose: "Defines the process for contributing to the project, including how to create Issues and Pull Requests, and the code review process. Aims to lower the barrier for external and internal contributors."
    update_trigger: "When the contribution workflow or review process changes."
  - file: "[CHANGELOG.md](CHANGELOG.md)"
    purpose: "Records a chronological list of notable changes for each version of the project. Helps users and contributors understand the evolution of the project at a glance."
    update_trigger: "On every new release (version update)."
  - file: "[docs/00_PROJECT_OVERVIEW.md](docs/00_PROJECT_OVERVIEW.md)"
    purpose: "Defines the overall picture of the project and forms a common understanding among stakeholders. It includes the background, problems to solve, goals, target users, scope, and a list of main features."
    update_trigger: "When there are changes to the core specifications, such as the project's purpose, scope, or main features."
  - file: "[docs/01_ARCHITECTURE.md](docs/01_ARCHITECTURE.md)"
    purpose: "Defines the system's structure and design philosophy, and records the rationale for technical decisions. It includes an architecture overview, design principles, details of main components, data model, infrastructure, and reasons for technology selection."
    update_trigger: "When there are changes related to the system's structure, such as the addition of new components, changes in the responsibilities of existing components, or changes in the infrastructure configuration."
  - file: "[docs/02_CODING_STANDARDS.md](docs/02_CODING_STANDARDS.md)"
    purpose: "Defines the conventions for maintaining code consistency. It includes formatting conventions, naming conventions, coding style, library usage conventions, and discouraged patterns."
    update_trigger: "When new conventions are added, existing conventions are changed, or the linters used are changed."
  - file: "[docs/03_TESTING_GUIDELINES.md](docs/03_TESTING_GUIDELINES.md)"
    purpose: "Defines the testing policies and procedures for ensuring quality. It includes the test strategy, how to write tests, test scope, how to run tests, and the policy for using mocks/stubs."
    update_trigger: "When the test strategy is changed, a new test framework is introduced, or the method of running tests is changed."
  - file: "[docs/04_SETUP.md](docs/04_SETUP.md)" 
    purpose: "Defines the development environment setup procedure in detail. It includes prerequisites, installation procedure, environment variable settings, how to start the application, and troubleshooting."
    update_trigger: "When there are changes to the development environment setup procedure, the necessary tools, or environment variables."
  - file: "[docs/05_DEPLOYMENT.md](docs/05_DEPLOYMENT.md)"
    purpose: "Provides detailed procedures for deploying the application to production and other environments. Includes environment-specific settings and rollback procedures."
    update_trigger: "When the deployment process, infrastructure, or required environment variables change."
  - file: "[docs/06_OPERATIONS_GUIDE.md](docs/06_OPERATIONS_GUIDE.md)"
    purpose: "A runbook for operators, defining standard operating procedures (SOPs) for system operations, such as monitoring, backup, incident response, and regular maintenance tasks."
    update_trigger: "When operational procedures, monitoring metrics, or the incident response plan are updated."
  - file: "[docs/07_SECURITY_GUIDELINES.md](docs/07_SECURITY_GUIDELINES.md)"
    purpose: "Documents the project's security design, threat model, and policies. Includes guidelines for handling vulnerabilities, data privacy considerations, and access control policies."
    update_trigger: "When there are changes to the security architecture, a new vulnerability is identified, or the security policy is revised."
  - file: "[docs/08_DECISION_LOG.md](docs/08_DECISION_LOG.md)"
    purpose: "Serves as an Architecture Decision Record (ADR). Logs important architectural and design decisions, their context, and the rationale behind them to ensure transparency in the decision-making process."
    update_trigger: "Whenever a significant architectural or technical design decision is made."
```



### 5.2. Documentation Update Process
*   **Principle:** Based on the **Documentation Strategy** defined in Chapter 3, especially the principle of **Documentation as Code (DaC)**, changes to code and updates to documentation are always treated as a single atomic task. If an implementation or specification change affects the content of any of the documents defined in `5.1`, a Pull Request to update the corresponding document must be created.
*   **Procedure:**
    1.  At the `Step 2: Implementation Planning and Agreement` stage, the AI identifies the documents that need to be updated along with the code changes and includes the update content in the implementation plan.
    2.  The AI must proactively verify if any documentation needs to be updated in conjunction with the code changes. If an update is deemed necessary, the AI will proceed as follows:
        *   It first checks if the corresponding document file exists.
        *   If the file does not exist, it creates a new one with the appropriate file name based on `5.1. Document Structure and Content`.
        *   If the file exists but is missing necessary content, it adds that content.
    3.  After user approval, the AI updates the documentation along with the code changes.
    4.  In the Pull Request review, the appropriateness of the documentation description is also subject to review, just like the correctness of the code.

### 5.3. Specification and Design Documentation Support Workflow
If the AI determines that the specifications or design that are prerequisites for code implementation are missing from the documentation, it will proactively support their clarification and documentation through the following interactive workflow.

1.  **Trigger (Detection of Missing Information)**
    *   The AI starts this workflow when, during Issue response, it determines that essential design information for starting implementation (e.g., concrete specifications for a new feature, the flow of complex business logic, API endpoint details, etc.) is not specified in the existing documentation.

2.  **Step 1: Proposal for Documentation**
    *   The AI temporarily suspends the implementation work and proposes to the user the benefits of documenting, for example, by saying, "Before we start implementing the 〇〇 feature, why don't we document its specifications and design in `docs/01_ARCHITECTURE.md`? This will prevent rework and improve future development efficiency."

3.  **Step 2: Hearing of Functional Requirements**
    *   If the user agrees, the AI will ask the user about the functional requirements, constraints, expected behavior, etc., necessary for implementation.

4.  **Step 3: Presentation of Design Proposal by AI**
    *   Based on the heard requirements, the AI will create and present a concrete design proposal. The presented design proposal will include content such as:
        *   Proposed updates to the relevant architecture diagrams
        *   Sequence diagrams or flowcharts showing the processing flow
        *   Database table design and ER diagrams
        *   API endpoint design (request, response formats, etc.)

5.  **Step 4: Agreement and Issue Creation Proposal**
    *   The user reviews the presented design proposal and approves it. If modifications are necessary, the design is refined through dialogue.
    *   Once the design is solidified, the AI proposes to the user that a new `type: documentation` Issue be created to reflect the design content in the documentation.
    *   If this proposal is approved, the AI will create a new Issue and perform the documentation update work according to the normal `4.2 Issue-Driven Development Process`. This ensures that the implementation and design remain in sync.

### 5.4. Document Scalability
To maintain the readability and maintainability of documents as they grow in size and complexity, the following file splitting rules are defined.

*   **Trigger for Splitting:** The AI will consider splitting a document and propose it to the user when any of the following criteria are met:
    *   **Length:** The file exceeds 500 lines.
    *   **Complexity:** The document contains three or more independent major topics (corresponding to H2 level headings).

*   **Splitting Method:**
    1.  **Create a Subdirectory:** Create a subdirectory corresponding to the original file name (e.g., `docs/01_ARCHITECTURE.md` -> `docs/architecture/`).
    2.  **Split and Place Files:** Split the original document into multiple Markdown files based on logical units, and place them in the created subdirectory with sequential numbers and descriptive names (e.g., `01_overview.md`, `02_components.md`, `03_data_flow.md`).
    3.  **Create a Table of Contents:** Update the original document file (in this example, `docs/01_ARCHITECTURE.md`) to function as a **Table of Contents**, containing links to each of the split files.

### 5.5. Handling Outdated Documentation
This section defines a context-aware workflow for the AI to follow when it discovers outdated documentation, ensuring that fixes are handled efficiently without disrupting the primary development flow.

*   **Path 1: In-Scope and Minor Fixes**
    *   **Trigger:** When the AI, while working on an Issue, discovers outdated documentation that is **directly related** to the current task (e.g., a function signature change, a typo).
    *   **Action:** The AI will not suspend its task or create a new issue. Instead, it will incorporate the documentation fix directly into the implementation plan of the *current* Issue.
    *   **Reporting:** The AI will list the documentation file under "Files to be changed" in its implementation proposal and describe the necessary fix. The fix will be committed and included in the same Pull Request as the related code changes.

*   **Path 2: Out-of-Scope or Major Fixes**
    *   **Trigger:** When the AI discovers a major documentation issue that is **not directly related** to the current task or requires significant effort to resolve (e.g., a fundamentally incorrect architecture diagram).
    *   **Action:** The AI will **first complete its current assigned task** to avoid disrupting the user's workflow.
    *   **Reporting:** After the current PR is merged, the AI will report the major documentation discrepancy to the user. It will then propose the creation of a new `type: documentation` Issue to address the problem, following the standard procedure for issue creation.
