# 📝 Useful SharePoint App Registration & Permission Links

## Register a New App (AppRegNew.aspx)

[Register New App](https://example.sharepoint.com/sites/sam/_layouts/15/appregnew.aspx)

## Grant App Permissions (AppInv.aspx)

[Grant App Permissions](https://example.sharepoint.com/sites/sam/_layouts/15/appinv.aspx)

## Example Permission XML

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
  <AppPermissionRequest Scope="http://sharepoint/content/tenant"
  Right="FullControl" />
</AppPermissionRequests>

<AppPermissionRequests AllowAppOnlyPolicy="true">
    <AppPermissionRequest Scope="http://sharepoint/content/sitecollection"
    Right="FullControl" />
</AppPermissionRequests>
```

## More Useful SharePoint URLs

- [Grant App Permissions (Admin)](https://example-admin.sharepoint.com/_layouts/15/appinv.aspx)
- [App Principals - GlobalHub](https://example.sharepoint.com/sites/ExampleHub/_layouts/15/AppPrincipals.aspx)
- [App Principals - MyLibrary](https://example.sharepoint.com/sites/MyLibrary/_layouts/15/AppPrincipals.aspx)
- [SharePoint REST API](https://example.sharepoint.com/sites/MyLibrary/_api/)

## 🔗 References

- [Connect-PnPOnline with AppId and AppSecret](https://www.sharepointdiary.com/2019/03/connect-pnponline-with-appid-and-appsecret.html)
- [SharePoint Add-in Permission XML Cheat Sheet](https://medium.com/ng-sp/sharepoint-add-in-permission-xml-cheat-sheet-64b87d8d7600)

## Example PowerShell: Connect-PnPOnline

```powershell
Connect-PnPOnline -Url https://contoso.sharepoint.com/sites/demo `
 -ClientId [Your Client ID] `
 -ClientSecret "[Your Client Secret]"


Connect-PnPOnline -ClientId <application-client-id> `
  -CertificatePath '<path-to-pfx-file>' `
  -CertificatePassword (ConvertTo-SecureString -AsPlainText "<certificate-password>" -Force) `
  -Url https://<yourtenant>.sharepoint.com -Tenant "<tenantname>.onmicrosoft.com"
```

---

# SPO Reset APIs Permissions

**SharePoint App-Only Permission XML Examples**

This repository provides ready-to-use XML snippets for configuring SharePoint app permissions at various scopes, including tenant, site collection, web, list/library, and special services like Search, Taxonomy, and Business Connectivity Services.

---

## 🚀 How to Use

1. Copy the relevant `<AppPermissionRequests>` XML snippet below.
2. Paste it into your SharePoint app manifest or permission request file as needed.
3. Adjust the `Scope` and `Right` attributes to fit your scenario.

---

## 🔑 Permission XML Examples

### Full Control at Tenant Level

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
    <AppPermissionRequest Scope="http://sharepoint/content/tenant"
     Right="FullControl" />
</AppPermissionRequests>
```

### Manage Control at Tenant Level

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
    <AppPermissionRequest Scope="http://sharepoint/content/tenant"
     Right="Manage" />
</AppPermissionRequests>
```

### Full Control at Site Collection Level

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
   <AppPermissionRequest Scope="http://sharepoint/content/sitecollection"
    Right="FullControl" />
</AppPermissionRequests>
```

### Manage Control at Site Collection Level

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
   <AppPermissionRequest Scope="http://sharepoint/content/sitecollection"
    Right="Manage" />
</AppPermissionRequests>
```

### Full Control at Web Level

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
  <AppPermissionRequest Scope="http://sharepoint/content/sitecollection/web"
   Right="FullControl" />
</AppPermissionRequests>
```

### Full Control to a List/Library

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
   <AppPermissionRequest Scope="http://sharepoint/content/sitecollection/web/list"
    Right="FullControl" />
</AppPermissionRequests>
```

---

## ⚡ Special Scenarios

### 1. Provide Access to Search Service

> **Note:** Search service permission is a special case.

```xml
<AppPermissionRequests AllowAppOnlyPolicy="false">
   <AppPermissionRequest Scope="http://sharepoint/search"
    Right="QueryAsUserIgnoreAppPrincipal" />
</AppPermissionRequests>
```

### 2. Provide Access to Taxonomy

> **Note:** Only `Read` and `Write` permissions can be granted. Taxonomy supports app-only permissions.

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
   <AppPermissionRequest Scope="http://sharepoint/taxonomy"
    Right="Read" />
</AppPermissionRequests>
```

### 3. Provide Access to Business Connectivity Service

> **Note:** Business Connectivity only supports `Read` access.

```xml
<AppPermissionRequests AllowAppOnlyPolicy="true">
   <AppPermissionRequest Scope="http://sharepoint/bcs/connection"
    Right="Read" />
</AppPermissionRequests>
```

---

## 📚 License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
