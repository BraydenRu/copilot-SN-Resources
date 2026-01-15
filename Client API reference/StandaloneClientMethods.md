StandaloneClientMethods
Release version: 
Zurich
UpdatedJul 30, 20253 minutes to readSummarize
Standalone client methods are methods that you can use within your client JavaScripts, such as reflistOpen, but aren't a part of any class or API.

You can directly access these methods within a client script without any constructor or other type of instantiation before use.

Standalone - reflistOpen (String target, String elementName, String refTableName, String dependent, String useQBE, String refQualElements, String additionalQual, String parentID, String forceReference, String ignoreTargetValue)
Shows the reference field data in a standard pop-up window. This method is commonly used when selecting a magnifying glass icon, beside any reference field, in UI 16 forms.

For example, using this method you can display reference field data for a specific set of query criteria:

Ref data in pop-up window

Similarly, you can use this method to display a search form that enables the user to enter their own set of query criteria for selecting the reference field data to display.

Search in pop-up window

When opening the URL in the standard pop-up, if the URL length is greater than TinyURL length, 1024 by default, the URL is converted to TinyURL, such as:

"sys_user_list.do?sysparm_tiny=7ea02c4ff8a8b510f877c74d78b60460".

Note:
reflistOpen() isn’t supported in Workspace Client Script. Use the g_modal.showFrame() method instead.


Parameters
Name	Type	Description
target	String	Form target reference field ID.
For example, the caller_id parameter's target reference field ID is incident.caller_id.

elementName	String	Form reference field element name.
For example: caller_id

refTableName	String	Reference table to map to the form reference field.
For example, for the reference field caller_id, sys_user is the reference table. In this case, you would pass the value sys_user.

dependent	String	Configured dependent field for the specified target element.
For additional information, see Make a field dependent.

useQBE	String	Flag that indicates the type of information to return in the pop-up window.
Valid values:
true: Display a query form with a search button.
false: Display the query results.
Default: false

refQualElements	String	Configured reference qualifier for the specified target element. The function appends the specified reference qualifiers to the URL and only displays the filtered results in the pop-up window. If you don't want to include a reference qualifier, pass an empty string.
For additional information on reference qualifiers, see Reference qualifiers.

additionalQual	String	Optional. Additional qualifier query to use to filter the results that display in the pop-up window.
For example, for a caller_id reference field in an incident, you could pass the user's sys_id sys_id=62826bf03710200044e0bfc8bcbe5df1.

The function filters the User [sys_user] table and shows the filtered results in the pop-up window.
parentID	String	Optional. Currently only an internal parameter, no need to pass a value.
forceReference	String	Optional. Currently only an internal parameter, no need to pass a value.
ignoreTargetValue	String	Optional. Currently only an internal parameter, no need to pass a value.
Returns
Type	Description
Pop-up window	Displays the returned reference field data in a standard pop-up window.
Example
The following example shows how to invoke this method to show the caller field data in the pop-up window for the incident table (first image above).

Explain this code
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {
      return;
   }

   reflistOpen('incident.caller_id', 'caller_id', 'sys_user','company', 'false', '');
}
Example
The following example shows how to invoke this same client script, but with useQBE = true, which displays a search button and associated search criteria within the pop-up window (second image above).

Explain this code
function onChange(control, oldValue, newValue, isLoading, isTemplate) {
   if (isLoading || newValue === '') {
      return;
   }

   //  Type appropriate comment here, and begin script below
   reflistOpen('incident.caller_id', 'caller_id', 'sys_user','company', 'true', '');
}
