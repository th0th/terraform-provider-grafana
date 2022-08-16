---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "grafana_annotation Resource - terraform-provider-grafana"
subcategory: ""
description: |-
  Official documentation https://grafana.com/docs/grafana/latest/dashboards/annotations/HTTP API https://grafana.com/docs/grafana/latest/http_api/annotations/
---

# grafana_annotation (Resource)

* [Official documentation](https://grafana.com/docs/grafana/latest/dashboards/annotations/)
* [HTTP API](https://grafana.com/docs/grafana/latest/http_api/annotations/)

## Example Usage

```terraform
resource "grafana_annotation" "test" {
  text = "basic text"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `text` (String) The text to associate with the annotation.

### Optional

- `dashboard_id` (Number) The ID of the dashboard on which to create the annotation.
- `panel_id` (Number) The ID of the dashboard panel on which to create the annotation.
- `tags` (Set of String) The tags to associate with the annotation.
- `time` (String) The RFC 3339-formatted time string indicating the annotation's time.
- `time_end` (String) The RFC 3339-formatted time string indicating the annotation's end time.

### Read-Only

- `id` (String) The ID of this resource.

