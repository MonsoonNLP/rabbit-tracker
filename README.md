# Rabbit-Tracker

Benchmark server for Rabbit

## Goals

- Serves random sample of secret evaluation dataset to submitted models
- Compares submitted model predictions to secret evaluation labels (can't test accuracy on user-scripted machine)
- Stores scores of candidate models

## Possible ideas

Trigger GitHub Actions rerun when the pull request is updated

Identify each proposal by Pull Request number

Models can be stored in their own directory, either from initial merge in
(similar to AdapterHub), or after being de-throned from top spot

Use a hidden environment variable, crypto key, or IP address to
prevent users from repeatedly querying and downloading the secret evaluation set.

Evaluation set should be from a different day of Reddit (or selected from a
random day on Reddit).

A: Automatically merge pull requests if the test set score is better, and the
secret evaluation set shows that the model is not simply overfit to the test
set.

B: Automatically merge pull requests if the secret eval set score is better

Train/test/eval set will be updated over time, as new vocabulary and uses
become popular. Old models should be re-run on the new train/test/eval, because
ideally someone has created a model with long-term adaptability

Are these patches actually better than using new vocab + finetuning with masked
words? Is CPU/GPU difference helpful?

Would it make more sense to use AdapterHub / use with AdapterHub to apply patches?
