# Risk/Assumption/Dependency Register

## Overview
The RAD Register is a tool for tracking risks, assumptions, and dependencies in the ConnText project.

## Structure
The RAD Register will be structured as a table with the following columns:
- **Feature/Requirement**: The feature or requirement associated with the risk, assumption, or dependency.
- **Assumption**: An assumption made about the feature or requirement that may affect its implementation.
- **Dependency**: A condition or event that must occur before a task can be completed.
- **Risk**: A potential event or condition based on the assumption or dependency that could negatively impact the project.
- **Mitigation**: The strategy employed to reduce the likelihood or impact of the risk.
- **Impact**: The potential impact of the risk on the project if there is no mitigation.
- **Likelihood**: The likelihood of the risk occurring or being exploited.

## RAD Metrics
Only the impact and likelihood columns have metrics associated with them. The impact and likelihood are both measured using the following scale:

- **Impact Scale (low-high)**:
    - Low: Minimal impact on the project/software.
    - Medium: Moderate impact on the project/software.
    - High: Significant impact on the project/software.

- **Likelihood Scale (low-high)**:
    - Low: Unlikely to occur.
    - Medium: Possible but not expected to occur.
    - High: Very likely to occur.

## Hybrid RAD Register
The RAD Register will be a hybrid of the traditional concepts such as; RAID Register; Risk Register; Assumptions Logs; and Dependency Logs. It will be used to track risks, assumptions, and dependencies in the ConnText project. After these have been identified, we will identify what the mitigation strategies are for each risk, the impact of each risk, and the likelihood of each risk occurring. The RAD Register should be updated regularly as new risks, assumptions, and dependencies are identified, and as existing ones are resolved or mitigated.
