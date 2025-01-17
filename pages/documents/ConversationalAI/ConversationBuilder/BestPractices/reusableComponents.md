---
pagename: Reusable Components
redirect_from:
Keywords:
sitesection: Documents
categoryname: "Conversational AI"
documentname: Conversation Builder
subfoldername: Best Practices
permalink: conversation-builder-best-practices-reusable-components.html
indicator: both
---

Consider adopting the reuse techniques below to avoid building the same components over and over again.

### Create reusable “yes” and “no” intents

One way to handle the responses to yes/no questions is to use pattern matching in the response conditions:

<img style="width:350px" src="img/ConvoBuilder/reusableYesNo1.png">

While that approach does work, it's error prone and not the most efficient, as it means you’ll need to enter the same patterns over and over again in the response conditions for all yes/no questions.

A better approach is to create two intents in the relevant domain--one intent for “yes” and the other for “no”--and to reuse the intents across the bot’s dialogs. You might name these as follows:

* **Affirmation**: The training phrases for this intent would include “yes”, “yeah”, “yup”, “ok” and so on.
* **Negative Affirmation**: The training phrases for this intent would include “no”, “nah”, “nope”, “no thanks” and so on.

For example:

<img style="width:350px" src="img/ConvoBuilder/reusableYesNo2.png">

Once you create the "yes" and "no" intents, you can create response conditions that evaluate the consumer’s response against them. In a condition, simply select “Response Intent,” and then select the appropriate intent.

<img style="width:800px" src="img/ConvoBuilder/reusableYesNo3.png">

### Create a reusable "resolve and close" dialog

Many dialogs require the following sequence of interactions within their flow:

*Did that resolve your question? Yes or No*

*Where:*
* *"Yes" sends a good-bye message and closes the conversation.*
* *"No" asks the user for input and matches the user's intent.*

To avoid repeatedly having to build this set of interactions within every dialog, you can create a reusable "resolve and close" dialog.

**To create the "resolve and close" dialog**

1. Create a new dialog named something like, "Confirm Resolution and Close".
2. Add the series of interactions shown in the following image (one Multiple Choice question, followed by three Text statements). Name the interactions with easily identifiable names. And configure the question's response conditions to direct the flow as indicated.
    
    <img style="width:600px" src="img/ConvoBuilder/reusableResolveAndCloseDialog1.png">
    
    
    To configure the response conditions, consider using reusable "yes" and "no" intents, as described in the [first section](conversation-builder-best-practices-reusable-components.html#create-reusable-yes-and-no-intents) on this page.

3. In the LP_CLOSECONVERSATION statement's interaction details, set the **Next Step** to "End Interaction."

    <img style="width:800px" src="img/ConvoBuilder/reusableResolveAndCloseDialog5.png">

    In the case of a "no" answer, the [LP_CLOSECONVERSATION](conversation-builder-keywords.html#lp_closeconversation) statement will cause the bot to end the conversation.

4. Go to another dialog in your bot, and, where it reaches its logical end and you want to confirm resolution with the consumer, explicitly set the **next step** to be this Confirm Resolution and Close dialog's "Is there anything else I can help you with?" question. 

    The following serves as an example:
    <img style="width:800px" src="img/ConvoBuilder/reusableResolveAndCloseDialog2.png">

5. Repeat the preceding step for all other applicable dialogs.
6. Test the dialog affirmatively and negatively.

    Below is an example flow for an affirmative (yes) answer.
    <img style="width:500px" src="img/ConvoBuilder/reusableResolveAndCloseDialog3.png">

    Below is an example flow for a negative (no) answer.
    <img style="width:500px" src="img/ConvoBuilder/reusableResolveAndCloseDialog4.png">