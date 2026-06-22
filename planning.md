# TakeMeter Planning Document

## Community

I selected r/nba because it contains a large volume of public discussions ranging from detailed basketball analysis to emotional reactions and controversial opinions. The variety of discourse makes it a strong candidate for a classification task focused on discourse quality.

## Labels

### Analysis

A post that uses specific facts, evidence, statistics, historical comparisons, or logical reasoning to support, explain, question, or evaluate a basketball-related claim.


Examples:
- "Furthest Draft pick is Jack Sikma..."
- "Definitely not the most a team has gotten from trading Paul George but..."

### Hot Take
A bold opinion, prediction, or claim presented with little supporting evidence or reasoning.

Examples:
- "Man they really got hosed in the Luka trade."
- "Peak offseason content and we're not even two weeks in. Won't be topped."

### Reaction
An emotional, celebratory, sarcastic, angry, or surprised response with little or no reasoning.

Examples:
- "WE'RE SOOO BACKKK"
- "Jesus this is so incredibly pathetic."

## Hard Edge Cases

Example:
LeBron is overrated. His playoff record against top seeds proves it.

Decision Rule:
If evidence is central to the reasoning, label as Analysis.
If evidence is only used to support a bold opinion without explanation, label as Hot Take.


## Data Collection Plan

Data will be collected from public posts and comments on r/nba.

Target distribution:

| Label | Target Count |
|---------|---------|
| Analysis | 70 |
| Hot Take | 65 |
| Reaction | 65 |

Total: 200 examples

Examples will be manually reviewed and labeled according to the taxonomy definitions. If one label becomes underrepresented, additional examples will be collected specifically for that category until the dataset is reasonably balanced.

## Evaluation Metrics

The primary metric will be accuracy because it provides an overall measure of classification performance.

Additional metrics will include:

- Precision
- Recall
- F1 Score

These metrics are important because some labels may be more difficult to classify than others. F1 Score provides a balanced measure of both precision and recall and helps identify weaknesses in specific classes.

A confusion matrix will also be used to identify which labels are most frequently confused.

## Definition of Success

The classifier will be considered successful if:

- Overall accuracy exceeds 75%
- Average per-class F1 score exceeds 0.70
- The fine-tuned model performs noticeably better than the zero-shot baseline

For deployment in a real community moderation or discourse analysis tool, performance above these thresholds would provide useful signal while still acknowledging that discourse quality is inherently subjective.

## AI Tool Plan

### Label Stress Testing

ChatGPT will be used to generate boundary cases between Analysis, Hot Take, and Reaction labels.

If generated examples are difficult to classify consistently, label definitions will be revised before annotation begins.

### Annotation Assistance

ChatGPT may be used to suggest labels for batches of examples.

All labels will be manually reviewed before inclusion in the final dataset.

### Failure Analysis

After evaluation, misclassified examples will be provided to ChatGPT to identify possible patterns in model errors.

Any suggested patterns will be manually verified before being included in the evaluation report.