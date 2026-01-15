GlideDocument - Client
Release version: 
Zurich
UpdatedJul 30, 20251 minute read
The GlideDocument API provides methods to search a Document Object Model (DOM) element, a document, or a JQuery element.

You can use this API in client-side scripts using ListV2 and ListV3 APIs. The GlideDocument APIs are accessed using the g_document global object.

GlideDocument - getElement(String selector, Element context)
Returns a node found in the specified DOM based context or created from the HTML context.

Parameters
Name	Type	Description
selector	String or Object	Selector expression
context	String or Object	Optional. DOM Element, document, or JQuery object to search.
Returns
Type	Description
node	Node that matches the selector.
Example
This example shows how to get the list view name value from a UI page.

Explain this code
//HTML entry
<input type="hidden" id="list_view" name="list_view" value="${sysparm_list_view}" />

// Client script
var listView = g_document.getElement('#list_view').value;
GlideDocument - getElements(String selector, Element context)
Returns a node list found in the specified DOM based context or created if an HTML context is specified.

Parameters
Name	Type	Description
selector	String or Object	The selector expression
context	String or Object	(Optional) A DOM Element, document, or JQuery object to be searched.
Returns
Type	Description
node list	A list of nodes that matches the selector.
