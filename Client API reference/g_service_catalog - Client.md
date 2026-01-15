g_service_catalog - Client
Release version: 
Zurich
UpdatedJul 30, 20251 minute read
The g_service_catalog API provides methods to access data in a multi-row variable set (MRVS) when a model is open.

This API is available in all environments, such as, Service Portal, ServiceNow AI Platform, Workspace, and Now® Mobile.

g_service_catalog - getValue(String variableName)
Returns the value of the specified field on the catalog item form when used in a client script on multi-row variable sets (MRVS).

Use this method when an MRVS modal is open for editing or creating and you want to modify data within the MRVS based on the value of a field on the parent catalog item form. For example, when you need to modify the contents of the cells within an MRVS based on a check box on the parent form. You can also use this method to access the data of other MRVS elements within the same parent form.

Note: This method can only be called from the parent object, such as g_service_catalog.parent.getValue().
Parameters
Name	Type	Description
variableName	String	Name of the variable in the catalog item form to return.
Returns
Type	Description
String	Value contained in the specified variable of the catalog item form.
Example
In this example, a catalog item for blocking multiple IP addresses on a firewall has a variable address_type with two choices - IPV4 and IPV6. The MRVS has two variables (ipv4_address and ipv6_address) for the respective address types. If the Address type field on the parent form is set to IPV4, the field IPV6 address is hidden on the MRVS.

Explain this code
function onLoad() {
  if (g_service_catalog.parent.getValue("address_type") == "ipv4") {
    g_form.setValue("ipv4_address", "XX.XX.XX.XX");
    g_form.setVisible("ipv6_address", "false");
  }
}
