---
page_title: "anomalo_table Resource - terraform-provider-anomalo"
subcategory: ""
description: |-
An Anomalo table's configuration. Maps closely to the Anomalo API for tables. See your API documentation for more information on attributes.

---

# anomalo_table (Resource)

An Anomalo table's configuration. Maps closely to the Anomalo API for tables. See your API documentation for more information on attributes.


## Example Usage

```terraform
resource "anomalo_table" "VariationsTable" {
    table_name                    = "square.items.variations"
    definition                    = "All variations (deleted or active) in all merchant catalogs."
    notification_channel_id       = anomalo_notification_channel.alert_channel.id
    check_cadence_type            = "daily"
    check_cadence_run_at_duration = "PT6H"
    always_alert_on_errors        = true
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `notification_channel_id` (Number) Notification channel that you would like to send notifications from this table to. Can be used with the NotificationChannel Datasource, ex anomalo_notification_channel.team_slack_channel.id
- `table_name` (String) The fully qualified name of the table, including the warehouse. Ex warehouse_name.schema_name.table_name

### Optional

- `always_alert_on_errors` (Boolean)
- `check_cadence_run_at_duration` (String)
- `check_cadence_type` (String) How often checks should execute on this table. Exclude this attribute (or equivalently, set to null) to de-configure and turn off checks for the table. Acceptable values include null, "daily", and "daily_freshness_gated"
- `definition` (String)
- `fresh_after` (String)
- `interval_skip_expr` (String)
- `notify_after` (String)
- `table_id` (Number) The ID of the table. Should not be set manually. Is Optional strictly to support more forgiving imports.
- `time_column_type` (String)
- `time_columns` (List of String)



## Import

### Importing

Import is supported using the following syntax:

```shell
terraform import anomalo_table.table_name table_id
```
