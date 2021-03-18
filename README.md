# MVC Dashboard - How to load different data based on the current user

This example shows how to configure the Dashboard control so that it loads data in the multi-user environment. 

You can identify a user in the current session and handle the following events to select the underlying datasource:

* [DashboardConfigurator.ConfigureDataConnection](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWeb.DashboardConfigurator.ConfigureDataConnection)
* [DashboardConfigurator.DataLoading](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWeb.DashboardConfigurator.DataLoading)
* [DashboardConfigurator.CustomFilterExpression](https://docs.devexpress.com/Dashboard/DevExpress.DashboardWeb.DashboardConfigurator.CustomFilterExpression)

**Files to look at**: [DashboardConfig.cs](./CS/MVCDashboard/App_Start/DashboardConfig.cs)

## Example Structure

You can limit access to data depending on the current user's ID. This ID is stored in the `HttpContext.Current.Session["CurrentUser"]` value from session state.

When the application starts, you see the [Index](./CS/MVCDashboard/Views/Home/Index.cshtml) view with a ComboBox in which you can select a user. When you click the **Sign in** button, the ID of the selected user is passed to the `HttpContext.Current.Session["CurrentUser"]` variable and you are redirected to the [Dashboard](./CS/MVCDashboard/Views/Home/Dashboard.cshtml) view. In this view, the Web Dashboard control displays the lists of dashboards and every dashboard loads data available to the selected user. Below is a table that illustrates the user IDs and their associated datasources in this example:

| Role  | Sql | Json | Excel | Object | OLAP | Extract | Entity Framework |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Admin | Categories | Customers | Bikes | Sales | Customers | Sales | Categories |
| User | Categories from different source with optional filter | Customers from different source with optional filter | Bikes from different source | Sales from different source | - | - | Categories from different source |



## See Also

- [T954359 - MVC Dashboard - How to implement multi-tenant Dashboard architecture](https://supportcenter.devexpress.com/ticket/details/t954359/mvc-dashboard-how-to-implement-multi-tenant-dashboard-architecture)
- [T590909 - Web Dashboard - How to load dashboards based on user roles](https://supportcenter.devexpress.com/ticket/details/t590909/web-dashboard-how-to-load-dashboards-based-on-user-roles)
- [T896804 - ASP.NET Core Dashboard - How to implement authentication](https://supportcenter.devexpress.com/ticket/details/t896804/asp-net-core-dashboard-how-to-implement-authentication)
- [T400693 - MVC Dashboard - How to load and save dashboards from/to a database](https://supportcenter.devexpress.com/ticket/details/t400693/mvc-dashboard-how-to-load-and-save-dashboards-from-to-a-database)
