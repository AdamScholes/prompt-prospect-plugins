---
name: check-fit
description: Judge everyone at a researched conference against the workspace's target customer so the matches sort to the top. Use when the user asks who is worth meeting, who matches their ideal customer, or asks to run or rerun Check fit. Spends the workspace's credits, so it always confirms first.
---

Check fit is the one paid step. Follow this exactly.

1. **Make sure there is a target customer.** Call `get_target_customer`. If the description and qualifying criteria are empty, stop and use the `target-customer` skill first; judging against nothing returns only "Unknown".
2. **Estimate before spending.** Call `check_fit` with the `event_id` and `confirm: false` (the default). It answers with how many people and companies would be assessed, how many results are reused free, the credits it would spend and the credits available. Repeat those numbers to the user and ask whether to go ahead.
3. **Run only on a clear yes.** Call `check_fit` again with `confirm: true`. It queues the work; it does not block. Tell the user it takes a few minutes for a small event and up to an hour for a very large one, and that they will be told when it finishes.
4. **Show the result.** When they ask, call `list_event_people` with `fit: ["STRONG", "PLAUSIBLE"]` and present the matches with the reason each one fits. Offer `set_people_status` with `pursue` for the ones they want to meet.
5. **Out of credits.** If the estimate shows fewer credits than needed, say how many are missing and that more credits are added at Settings → Billing in Prompt Prospect. Do not try to work around the limit.

Boundaries: never call `check_fit` with `confirm: true` without the user's explicit agreement in this conversation; never re-run it "just to refresh", since saved results are reused free and a rerun only assesses new people. A verdict is Prompt Prospect's judgment against the saved criteria, so present it as "judged a strong fit", not as fact about the person.
