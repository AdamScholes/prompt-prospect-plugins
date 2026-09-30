---
name: target-customer
description: Read or edit the workspace's target customer (ideal customer profile) that Check fit judges people against. Use when the user describes who they sell to, asks what their target customer is set to, or wants to change the criteria, exclusions, locations or offer.
---

The target customer is a saved profile with a description, qualifying criteria, exclusions, locations, the offer, and what the company does.

1. **Always read first.** Call `get_target_customer` and summarize it in a few lines. If it is empty, say so and ask the user to describe who they want to meet in one or two sentences: role, kind of company, size or industry, geography, and what they sell.
2. **Turn a description into criteria.** From the user's words draft a short description and three to six qualifying criteria that a person's headline, company and location can actually show (for example "works in compliance or risk at a bank or lender", "director level or above", "based in North America"). Add exclusions the user names (competitors, students, vendors). Read the draft back before saving.
3. **Save only what changes.** Call `update_target_customer` with just the fields the user changed. Lists (`qualifying_criteria`, `exclusions`, `locations`) replace the whole list, so pass the full new list; pass `null` to clear a text field. Saving never starts a fit check on its own.
4. **Offer the next step.** After a change, offer to run Check fit on an event with the `check-fit` skill, since existing verdicts were made against the old criteria.

Boundaries: do not add criteria the user did not imply; ask when their description is too vague to judge anyone (for example "decision makers"). Never put personal data about specific people into the profile; it describes a kind of customer, not a person.
