

# EXP 5: COMPARATIVE ANALYSIS OF DIFFERENT TYPES OF PROMPTING PATTERNS AND EXPLAIN WITH VARIOUS TEST SCENARIOS

# Aim: 
To test and compare how different pattern models respond to various prompts (broad or unstructured) versus basic prompts (clearer and more refined) across multiple scenarios.  Analyze the quality, accuracy, and depth of the generated responses 

## AI Tools Required: ChatGPT

# Explanation: 

## 1. Introduction

Automated maintenance report generation is a growing application of AI, where systems summarize machine conditions, errors, and required actions into clear, structured reports. A challenge in such systems is the variation in quality of AI-generated outputs, which depends heavily on how prompts are designed. Poorly structured prompts may produce vague or incomplete responses, while refined prompts can yield highly accurate and useful reports. This study focuses on prompt templating, a technique where prompts are pre-designed in structured formats, and on the command pattern technique, which allows consistent and repeatable task execution. By combining these two approaches, the study aims to test whether report generation can become more accurate, consistent, and scalable.

## 2. Prompt Templating Techniques

Prompt templating refers to the systematic structuring of prompts that guide AI models in producing responses. Instead of giving random or natural queries, users rely on predefined formats to achieve higher-quality outputs.

Broad or unstructured prompts:
* Example: “Generate a maintenance report for a machine breakdown.”
* Issues: AI may produce responses that are too general, inconsistent in format, or lacking in depth.

Basic or refined prompts:
* Example: “Generate a maintenance report including: (1) Machine Name, (2) Fault Description, (3) Root Cause, (4) Corrective Action, (5) Preventive Measures.”
* Benefits: Ensures a clear structure, predictable output, and improved relevance.

Impact on outputs:
* Refined templates reduce ambiguity, increase reliability, and make AI responses easier to integrate into industrial workflows.

Examples of templating styles:
* Question-based template: “What is the issue? What caused it? What is the solution?”
* Checklist-style template: “Machine Name → Issue → Action Taken → Next Steps”
* Tabular template: Used when reports need structured fields for database entry.

<img width="1100" height="618" alt="image" src="https://github.com/user-attachments/assets/5112955c-122a-4c7a-b797-4cdfef4cc1c4" />


## 3. Command Pattern Technique

The command pattern is a design pattern in software engineering that encapsulates a request as an object. This allows systems to parameterize tasks, queue them, and execute them consistently.

Key elements:
* Command – the request (e.g., “Generate maintenance report”).
* Invoker – the trigger that executes the command.
* Receiver – the AI system or engine performing the task.

Relevance to prompt design:
* In AI-based reporting, each type of prompt can be treated as a “command object.”
* This makes it easy to reuse prompts, maintain consistency, and execute them systematically.

Example:
* Command: Generate report for turbine vibration issue.
* Template ensures fields like Cause, Impact, Action.
* Invoker: software system calling the AI.
* Receiver: AI generates structured output.

Benefits:
* Reduces manual variation in how prompts are asked.
* Standardizes outputs across multiple scenarios.
* Makes scaling automated reporting across large systems possible.

<img width="560" height="420" alt="image" src="https://github.com/user-attachments/assets/33226016-6b89-4e8c-a89e-c0b5f5a07203" />


## 4. Integration of Prompt Templating with Command Pattern

Concept: 
* By combining templating with the command pattern, AI-generated maintenance reports can follow strictly defined structures while remaining adaptable to different contexts.

Workflow:
* User/system identifies the type of report needed.
* Corresponding command object is created (linked to a specific template).
* Command is executed by the invoker.
* AI (receiver) fills the template with detailed, context-specific information.
* Final structured report is generated.

Illustration (example):
* Command: “Generate preventive maintenance report.”

Template:
* Machine: [Name]
* Current Status: [Condition]
* Faults Observed: [List]
* Actions Taken: [Steps]
* Preventive Recommendations: [Suggestions]
* Output: AI fills the placeholders with contextual information.

Advantages of integration:
* Consistency – reports always follow a fixed structure.
* Accuracy – templates reduce ambiguity in AI interpretation.
* Scalability – can handle thousands of maintenance logs with little manual intervention.
* Flexibility – templates can be domain-specific (e.g., electrical faults, mechanical wear).

Example Implementation:
```
# Command Pattern with Prompt Templating for Maintenance Report Generation

from abc import ABC, abstractmethod

# --- Command Interface ---
class Command(ABC):
    @abstractmethod
    def execute(self):
        pass

# --- Receiver (AI/Report Generator) ---
class ReportGenerator:
    def fill_template(self, machine, issue, cause, action, recommendation):
        template = f"""
        Maintenance Report
        ------------------
        * Machine Name: {machine}
        * Issue Reported: {issue}
        * Root Cause: {cause}
        * Corrective Action Taken: {action}
        * Preventive Recommendation: {recommendation}
        """
        return template.strip()

# --- Concrete Command ---
class GenerateMaintenanceReport(Command):
    def __init__(self, receiver, machine, issue, cause, action, recommendation):
        self.receiver = receiver
        self.machine = machine
        self.issue = issue
        self.cause = cause
        self.action = action
        self.recommendation = recommendation

    def execute(self):
        return self.receiver.fill_template(
            self.machine, self.issue, self.cause, self.action, self.recommendation
        )

# --- Invoker ---
class MaintenanceSystem:
    def __init__(self):
        self.commands = []

    def add_command(self, command):
        self.commands.append(command)

    def run(self):
        for command in self.commands:
            print(command.execute())
            print("\n" + "="*50 + "\n")

# --- Client Code ---
if __name__ == "__main__":
    # Receiver
    generator = ReportGenerator()

    # Command (with templated fields)
    report_cmd = GenerateMaintenanceReport(
        generator,
        machine="CNC Milling Machine",
        issue="Unusual vibration detected",
        cause="Loose coupling between motor shaft and spindle",
        action="Coupling re-tightened and alignment verified",
        recommendation="Implement routine torque checks every 200 operating hours"
    )

    # Invoker
    system = MaintenanceSystem()
    system.add_command(report_cmd)
    system.run()
```

## 5. Advantages of this Approach (Tabulation)

| Feature           | Prompt Templating | Command Pattern | Combined Approach |
|-------------------|------------------|-----------------|------------------|
| Consistency       | Moderate          | High            | Very High        |
| Accuracy          | Moderate          | High            | Very High        |
| Flexibility       | High              | Moderate        | High             |
| Scalability       | Low               | High            | High             |
| Depth of Response | Moderate          | High            | Very High        |

## 6. Applications
* Automated maintenance report generation.
* Predictive maintenance in industries.
* Fault diagnosis and troubleshooting.
* Training and knowledge management.

## 7. Future Enhancements
* Adaptive templates using reinforcement learning.
* Real-time feedback integration.
* Multi-lingual prompt optimization.
* Domain-specific fine-tuned AI models.

## 8. Conclusion
* Combining prompt templating with the command pattern offers a scalable and reliable framework for maintenance reporting.
* It addresses issues of inconsistency, shallow responses, and lack of structure in AI outputs.
* This approach has potential to be deployed widely in industrial automation.

# RESULT:
The prompt for the above said problem executed successfully
