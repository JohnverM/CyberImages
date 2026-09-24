# BA GUIDE

## Writing User Stories

*Desktop Internal Tools • Version 2.0*

---

# 1. Purpose of This Guide

This guide defines the team standard for writing user stories for enterprise internal tools, ensuring clarity, completeness, and consistency from backlog refinement through delivery and testing.

A well-formed user story answers four questions:

-   Who needs this and why? --- Business Value

-   What is in scope? --- Scope (Market, Workflow, GDS)

-   What must exist first? --- Pre-requisites

-   How will it be verified, and what are the precise conditions for done? --- Acceptance Criteria

# 2. Story Structure at a Glance

Each user story is composed of four mandatory components. All four must be completed and reviewed before a story is marked Ready for Development.

  -----------------------------------------------------------------------------------------------------------------
  **\#**   **Component**                          **Key Question**            **Format**
  -------- -------------------------------------- --------------------------- -------------------------------------
  **1**    **Business Value**                     Who needs it and why?       *As a / I want / So that*

  **2**    **Scope**                              What is affected?           *Market + Workflow + GDS Reference*

  **3**    **Pre-requisites**                     What must be true first?    *Dependency list or \'None\'*

  **4**    **Verification/Acceptance Criteria**   How will it be confirmed?   *Plain-language test walkthrough*
  -----------------------------------------------------------------------------------------------------------------

# 3. Component Detail

## 3.1 Business Value

The Business Value statement explains **who** needs something, **what** they need, and **why** it matters. It should be completed before any other part of the story.

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Clause**               **Guidance**
  ------------------------ ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **As a \[role\]**        Name the specific persona or system role --- never a generic \'user\'. Use the exact role name that maps to your system\'s access model (e.g., Finance Admin, Ops Manager, GDS Agent, Procurement Lead).

  **I want to \[goal\]**   Describe the capability or outcome needed. Focus on **what** needs to be achieved, not **how** it is done. Avoid references to screens, buttons, or other UI elements.

  **So that \[reason\]**   Articulate the business outcome or value delivered. If the value cannot be clearly explained, discuss the story further with the Product Owner.
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

+---------------------+------------------------------------------------------------------------+
| **✅ Good Example** | *As a Travel Counselor,*                                               |
|                     |                                                                        |
|                     | *I want all forms of payment added to the PNR to include an asterisk,* |
|                     |                                                                        |
|                     | *So that ticketing can be completed successfully without errors.*      |
+=====================+========================================================================+
+---------------------+------------------------------------------------------------------------+

+--------------+------------------------------------------------------------------------+
| **❌ Avoid** | *As a user,*                                                           |
|              |                                                                        |
|              | *I want all forms of payment added to the PNR to include an asterisk,* |
|              |                                                                        |
|              | *So that ticketing can be completed successfully without errors.*      |
+==============+========================================================================+
+--------------+------------------------------------------------------------------------+

## 3.2 Scope

Scope defines the story\'s boundaries --- markets, workflow, and GDS entities affected --- so developers, QA, and stakeholders share the same understanding before work begins.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Scope Element**        **What to Document**
  ------------------------ -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Market(s) Affected**   List every market, region, or business unit this story applies to. If it applies globally, state \'All Markets\' explicitly. If market-specific business rules apply, describe them here --- not in the AC.

  **Workflow**             Identify the business process this story sits within. Reference the workflow name and ID as documented in your process maps (e.g., New Booking Workflow, Fees Workflow). This ties the story to your process library.

  **GDS Reference**        Specify the Global Data Standard entities, fields, or rules that this story touches. This creates traceability from feature to data model and feeds directly into intent generation.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

+-------------------------------------------------------------------------------------+
| **Scope Example**                                                                   |
+=====================================================================================+
| **Market(s) Affected:** Global, EMEA, APAC, UK, Ireland                             |
|                                                                                     |
| **Workflow:** New Booking, Amend Booking, Send itin, Cancel Booking, Price Tracking |
|                                                                                     |
| **GDS Reference:** 1A (Amadeus), 1S (Sabre)                                         |
+-------------------------------------------------------------------------------------+

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **📌 Note**   *Never leave Scope blank. If the story is unrestricted, explicitly write \'All Markets / Global\'. Unstated scope becomes assumed scope --- a leading cause of scope creep.*
  ------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 3.3 Pre-requisites

Pre-requisites capture every dependency that must be in place before development or testing can begin. They are identified during refinement --- not discovered mid-sprint.

Include a pre-requisite when any of the following apply:

-   Another story or feature must be completed and deployed first

-   Specific data, configuration, or environment setup is required

-   A role, permission, or access level must already exist in the system

-   An upstream API, integration, or service must be available in the target environment

-   A business rule, policy decision, or legal sign-off is pending

  ---------------------------------------------------------------------------------------------------------------------
  **Pre-requisite Type**   **Example**
  ------------------------ --------------------------------------------------------------------------------------------
  **Story dependency**     US-3901 (Vendor Code Setup) must be completed and deployed to UAT.

  **Data / config**        Service Option \"PEX - Use Amadeus Web Service\" is set to YES

  **Role / access**        Finance Admin role must be configured with export permissions in the IAM system.

  **Integration**          DocuSign API v3 endpoint must be active and accessible in the target environment.

  **Decision pending**     Legal approval on data retention policy required before Acceptance Criteria are finalised.
  ---------------------------------------------------------------------------------------------------------------------

  -------------------------------------------------------------------------------------------------------------------------------------------------------
  **📌 Note**   *If there are no pre-requisites, write \'None identified at this time\' --- never leave this field blank or omit the section entirely.*
  ------------- -----------------------------------------------------------------------------------------------------------------------------------------

  -------------------------------------------------------------------------------------------------------------------------------------------------------

## 3.4 Acceptance Criteria

The **Acceptance Criteria** describes how the solution will be validated against the business need, giving BAs and QA a clear, end-to-end view of expected behavior without needing further clarification.

Acceptance Criteria serve as the shared understanding between **Business, Development, and QA** of what must be delivered for the story to be considered complete.

Acceptance Criteria are the only validation section required in the story. Test scenarios, QA test cases, and Given/When/Then scripts should not be included as separate sections unless specifically requested by the team.

**Acceptance Criteria Section Should:**

-   Clearly define the conditions that must be met for the story to be accepted.

-   Focus on observable and measurable outcomes.

-   Describe expected system behavior in business terms.

-   Be specific, unambiguous, and testable.

-   Cover both successful and exception scenarios where applicable.

-   Enable QA to validate the feature without needing additional explanation from the BA.

**Acceptance Criteria Should Not:**

-   Describe technical implementation details.

-   Specify how developers should build the solution.

-   Contain vague statements such as \"works as expected\" or \"system functions correctly.\"

-   Duplicate information already captured in design or technical documentation.

**Writing Guidelines**

When writing Acceptance Criteria:

-   Write from the user\'s perspective.

-   Use clear and concise language.

-   Describe the trigger, action, and expected result.

-   Ensure each criterion can be independently tested.

-   Focus on outcomes rather than system design.

+--------------------------------------------------------------------------------------------------------+
| **User Story with Acceptance Criteria Example**                                                        |
+========================================================================================================+
| **As a** Travel Counselor**,**\                                                                        |
| **I want** all forms of payment added to the PNR to include an asterisk,\                              |
| **So that** ticketing can be completed successfully without errors.                                    |
|                                                                                                        |
| **Verification / Acceptance Criteria**                                                                 |
|                                                                                                        |
| 1.  When a form of payment is added to a PNR, the payment entry includes an asterisk (\*).             |
|                                                                                                        |
| 2.  The asterisk is displayed for all supported forms of payment.                                      |
|                                                                                                        |
| 3.  Users can successfully complete ticketing when payment information includes the required asterisk. |
|                                                                                                        |
| 4.  Existing ticketing functionality continues to work as expected after the change.                   |
|                                                                                                        |
| 5.  If multiple forms of payment are added, each payment entry includes an asterisk.                   |
+--------------------------------------------------------------------------------------------------------+

# 4. Complete Story Template

Use this template for every story. All fields are mandatory. Stories submitted with missing fields will be returned to the BA for completion before refinement.

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Field**                 **Content**
  ------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Title**                 Short imperative title --- e.g., \'Export Approved PO to PDF\'

  **As a**                  \[Specific Role / Persona --- not \'user\'\]

  **I want to**             \[Verb + Object --- capability, not UI action\]

  **So that**               \[Measurable business outcome or value\]

  **Market(s) Affected**    \[Market name(s) or \'All Markets / Global\'\]

  **Workflow**              \[Workflow name\]

  **GDS Reference**         \[GDS entity/field IDs\]

  **Pre-requisites**        \[Dependency list --- or \'None identified at this time\'\]

  **Acceptance Criteria**   \[Plain-language verification statements. Do not create separate Test Scenarios, Test Cases, Test Scripts, or BDD/Gherkin sections unless explicitly requested.\]
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 5. Best Practices

## 5.1 Business Value

-   Always name a specific role --- \'user\' is not a valid persona.

-   Write the goal as a capability (what), not a UI interaction (how).

-   If the \'So that\' clause is hard to complete, escalate to the Product Owner --- the story may lack business justification.

-   One story = one primary goal. If two distinct goals emerge, split into two stories.

-   Avoid technical implementation language in the Business Value --- it belongs in the dev notes or design doc.

## 5.2 Scope

-   Never assume scope --- document it explicitly, even when it seems self-evident.

-   When a story is market-specific, tag it in the backlog tool so QA can configure the correct environment.

-   Always reference the GDS entity --- it supports intent generation and data model traceability.

-   If a workflow ID does not exist, work with the process owner to create one before the story enters refinement.

-   Use \'All Markets / Global\' explicitly rather than leaving Market blank.

## 5.3 Pre-requisites

-   Review pre-requisites at every sprint refinement --- dependencies evolve as the backlog changes.

-   Flag decision-pending pre-requisites to the Product Owner immediately --- they are sprint blockers.

-   Link story IDs for story-level dependencies in your backlog tool (e.g., Jira \'Blocked By\' field).

-   Never assume an environment or integration exists --- verify availability before the story is refined.

## 5.4 Acceptance Criteria

-   Write Verification as if the reader has never seen the story before.

-   Avoid referencing specific UI element names that may change during development.

-   Verification must be executable against a staging or UAT environment with real or representative data.

## 5.5 General Story Quality

-   A story is not ready for development until all components are complete, accurate, and peer-reviewed.

-   Stories must be self-contained --- a developer must understand the full requirement without verbal context.

-   Apply the INVEST test: Independent, Negotiable, Valuable, Estimable, Small, Testable.

-   Use backlog labels or tags to categorize stories by market, workflow, and GDS entity for filtering and reporting.

-   After delivery, update the AC pass/fail status in your backlog tool to support sprint retrospectives and reporting.

-   Review stories with the dev lead during refinement --- not just during planning. Early feedback prevents rework.

# 6. Common Pitfalls & How to Fix Them

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Pitfall**                                **Why It Causes Problems**                                                                           **How to Fix It**
  ------------------------------------------ ---------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------
  **Generic persona (\'As a user\')**        Dev and QA cannot determine who is authorised, what context applies, or which permissions to test.   Use the exact system role: TX Counselor, Client Implementation team, Finance admin, Project team

  **UI-bound goal (\'click the button\')**   Intent becomes obsolete when UI changes; cannot be used for intent generation.                       Describe the capability: \'export the report\' --- not the interaction.

  **Weak \'So that\' clause**                Story lacks clear justification; cannot be prioritised or measured for business value.               If the value isn\'t clear, hold the story and escalate to the Product Owner.

  **Scope left blank**                       Dev assumes all markets and workflows; risk of unintended scope creep in production.                 Always document scope --- even \'All Markets / Global\' must be stated explicitly.

  **GDS not referenced**                     No data traceability; blocks intent generation; causes rework during integration testing.            Identify and link at least one GDS entity or field ID before refinement.

  **Pre-requisites found mid-sprint**        Story is blocked during the sprint; causes team disruption and velocity loss.                        Run a dependency check at refinement. Never assume environment or data availability.

  **Verification skipped**                   QA has no walkthrough; testers must interpret AC without a testing narrative.                        Always write a plain-language test walkthrough covering positive path. Add negative path when applicable or required.

  **AC describes implementation**            Ties QA to a specific technical approach that may change during development.                         The outcome should describe what the user observes --- not how the system builds it.

  **Vague outcome statement**                \'Works correctly\' or \'displays properly\' cannot be tested or failed.                             Be specific: name the field, message, file, status, or system action.

  **Story written after dev starts**         Developer interprets scope without formal guidance; AC becomes a retro exercise.                     All four components must be signed off before sprint planning --- no exceptions.
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# 7. Story Readiness Checklist

Complete this checklist before marking any story as Ready for Development. Stories that fail any item must be updated before entering the sprint.

  -----------------------------------------------------------------------------------------------------------
  **☐**   **Readiness Check**
  ------- ---------------------------------------------------------------------------------------------------
  **□**   Business Value --- Persona is a specific named role (not \'user\' or \'admin\').

  **□**   Business Value --- \'I want to\' describes a capability, not a UI element.

  **□**   Business Value --- \'So that\' articulates a clear and measurable business outcome.

  **□**   Scope --- Market(s) are explicitly named or stated as \'Global\'.

  **□**   Scope --- Workflow is named with a reference ID.

  **□**   Scope --- At least one GDS entity or field is referenced.

  **□**   Pre-requisites --- All dependencies are listed, or field states \'None identified at this time\'.

  **□**   Pre-requisites --- Story-level dependencies are linked in the backlog tool.

  **□**   Acceptance Criteria --- A plain-language test walkthrough is provided.

  **□**   Story is self-contained and requires no verbal context to understand.

  **□**   Story has been reviewed by the Product Owner and development lead.
  -----------------------------------------------------------------------------------------------------------

+-----------------------------------------------------------------------+
| **Version 2.0 • BA Guild • Enterprise Internal Tools**                |
|                                                                       |
| *For questions or updates, contact the BA Practice Lead.*             |
+=======================================================================+
+-----------------------------------------------------------------------+
