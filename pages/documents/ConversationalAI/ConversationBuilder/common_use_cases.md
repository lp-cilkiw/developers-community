---
pagename: Common Use Cases
redirect_from:
Keywords:
sitesection: Documents
categoryname: "Conversational AI"
documentname: Conversation Builder
permalink: conversation-builder-common-use-cases.html
indicator: both
---

Trying to accomplish a specific goal? Check this list of common use cases.

### Use and capture the consumer's last response

To include the consumer's last response in a message, use the following syntax:

`{$query}`

For example, in a [Fallback dialog](conversation-builder-dialogs-fallback-dialogs.html), you might send the fallback response, "I'm not sure what '{$query}' means."

It's common to use this special syntax in the response conditions of questions because often you want to store the consumer's response to a question in a variable. For more on this, see [here](conversation-builder-variables-slots.html).

### Access authenticated customer information
Use the [Get Authenticated Customer Info](conversation-builder-scripting-functions-get-and-set-user-data-and-variables.html#get-authenticated-customer-info) scripting functions.

### Get the bot to close the dialog
Use the [LP_CLOSEDIALOG](conversation-builder-keywords.html#lp_closedialog) keyword in a Text statement.


### Get the bot to close the conversation
Use the [LP_CLOSECONVERSATION](conversation-builder-keywords.html#lp_closeconversation) keyword in a Text statement.
